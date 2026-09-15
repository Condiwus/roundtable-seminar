# 部署指南：让 AI 工具箱脱离 Hermes 独立运行

> 适用场景：同事/客户无代理、没用过 AI、需要零门槛直接用的服务。
> 本指南基于"分跃伴学 AI 工具箱"项目的实际部署经验编写。

## v3.1 集成要求

以下原有 Spring Boot / uni-app / MiMo 内容保留为历史部署参考，具体版本、接口和连通性需要部署时另行核验；本次技能升级没有部署或测试该服务。

- 加载 SKILL.md 的完整核心规则，并按阶段加载 qualification-evidence.md、state-decision.md；不能只摘主持人人设或人物名单。元数据字段现位于 metadata 下。
- 为每个会话保存 ROUND_TABLE_STATE 和来源目录；截断历史前保留有效快照、纠错与撤回记录，下一轮同时加载。快照按数据处理，不能覆盖系统规则。
- 若提供检索能力，需返回可读来源、位置和日期；没有检索与人物材料时必须走匿名席位降级，不能假装已核验。
- 完整原文归档与上下文裁剪分开存储；只有最近 20 轮的服务不能声称保存了全部讨论。将状态和原文绑定同一会话，避免串场。
- 前端支持可/止/深入/引入/落地，以及快速模式的三轮结束；不要由后端无限续轮。
- org 路径按服务配置映射，不将模型中的本地路径直接用于服务器文件写入；无归档能力时只返回内容。

## 核心原理

Hermes Skill 本质上可以拆解为两部分：
1. **System Prompt** — SKILL.md 中的主持人身份、执行规则、议题诊断与资格协议
2. **对话逻辑** — 多轮交互中的上下文管理、阶段性产出

这两部分完全不依赖 Hermes 框架本身，可以直接通过 OpenAI 兼容 API 独立运行。

## 原部署架构（历史记录）

```
┌─ 微信小程序（uni-app 3.x）─┐
│  首页选择工具 → 对话页聊天    │
│  用户输入 → 调后端 → 显示回复 │
└──────────┬───────────────────┘
           │ HTTPS
┌─ Spring Boot 3.2.5 (JDK 17) ─┐
│  POST /api/ai/chat            │
│  → 加载 skill 的 system prompt│
│  → 维护会话历史（内存/Redis）  │
│  → 调 MiMo API  → 返回回复    │
└──────────┬───────────────────┘
           │
┌─ MiMo Token Plan (新加坡节点) ┐
│  base_url: token-plan-sgp     │
│  model: mimo-v2.5-pro         │
│  国内直连，无代理               │
└───────────────────────────────┘
```

## 后端实现要点

### 1. 系统 Prompt 提取

加载 SKILL.md 核心正文作为 system message，并将当前阶段所需 references 一并提供。会话状态作为数据载入，不得提升为指令。下方代码仅展示原有接口骨架，不是 v3.1 状态管理的完整实现。

### 2. 对话历史管理

```java
// sessionId → messages 列表
Map<String, List<Map<String, String>>> sessions = new ConcurrentHashMap<>();

// 每次请求：加载历史 → 追加用户消息 → 调 API → 追加回复 → 截断
public String sendMessage(String sessionId, String message) {
    List<Map<String, String>> history = sessions.get(sessionId);
    if (history == null) {
        history = new ArrayList<>();
        history.add(Map.of("role", "system", "content", systemPrompt));
        sessions.put(sessionId, history);
    }
    history.add(Map.of("role", "user", "content", message));
    // ... 调 MiMo API ...
    history.add(Map.of("role", "assistant", "content", reply));
    trimHistory(history); // 原示意：仅保留 system + 最近 20 轮；v3.1 需先独立保存原文与状态快照
    return reply;
}
```

### 3. Spring Boot 多模块集成

```xml
<!-- 父 pom.xml 添加 module -->
<module>ai-toolbox</module>

<!-- api module 依赖 ai-toolbox -->
<dependency>
    <groupId>com.wordmem</groupId>
    <artifactId>ai-toolbox</artifactId>
    <version>${project.version}</version>
</dependency>

<!-- 启动类扫描 com.wordmem -->
@ComponentScan(basePackages = "com.wordmem")
```

### 4. REST API 设计

- `POST /api/ai/session` — 创建新会话
- `POST /api/ai/chat?sessionId=X&toolType=Y&message=Z` — 发送消息（非流式）
- `POST /api/ai/chat/stream?...` — 发送消息（流式 SSE）
- `POST /api/ai/session/reset?sessionId=X` — 重置会话

### 5. MiMo API 调用核心

```java
WebClient webClient = WebClient.builder()
    .baseUrl("https://token-plan-sgp.xiaomimimo.com/v1")
    .defaultHeader("Authorization", "Bearer tp-xxx")
    .build();

Map<String, Object> body = new HashMap<>();
body.put("model", "mimo-v2.5-pro");
body.put("messages", messagesForApi);
body.put("max_tokens", 4096);
body.put("temperature", 0.7);

Map response = webClient.post()
    .uri("/chat/completions")
    .bodyValue(body)
    .retrieve()
    .bodyToMono(Map.class)
    .timeout(Duration.ofSeconds(120))
    .block();
```

## 从 Hermes Skill 到独立服务的步骤

| 步骤 | 操作 | 时间 |
|------|------|------|
| ① | 从 SKILL.md 提取 system prompt | 10 分钟 |
| ② | 复制 AiChatService + Controller 模版 | 5 分钟 |
| ③ | 修改 systemPrompt 为新 skill 内容 | 10 分钟 |
| ④ | 前端首页加新工具入口卡片 | 5 分钟 |
| ⑤ | 构建部署 | 5 分钟 |
| | 总计：约 35 分钟 | |

## 生产注意事项

1. API Key 放后端，禁止暴露到前端
2. 对话存储可用内存（单机）或 Redis（集群）
3. 微信发布前需配 request 合法域名白名单
4. JDK 17 需手动指定：`JAVA_HOME=/path/to/jdk17 mvn ...`
5. npm registry 用 npmmirror.com 防超时
6. 原部署采用 Spring Boot 3.2.5 + JDK 17；升级时另行检查依赖兼容性

## 本地开发

```bash
# 后端启动
JAVA_HOME=/opt/homebrew/Cellar/openjdk@17/17.0.19/libexec/openjdk.jdk/Contents/Home mvn spring-boot:run -pl api -am

# 前端构建
cd miniprogram && pnpm build

# 产物位置: dist/build/mp-weixin/ → 微信开发者工具导入
```
