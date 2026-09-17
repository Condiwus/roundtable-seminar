# roundtable-seminar · 圆桌研讨会

> 你问 AI 一个难题，它给你一个答案、一个角度。
> 圆桌研讨会把它变成一场以「求真」为目标的认知操作：先判断这个问题到底需要什么，再决定谁来回答、回答完留下什么。

**v3.2 — 通用认知操作系统**

---

## 这不是什么

不是「邀请几个名人轮流发表观点」。

不是「永远给你更多角度」——更多角度本身可能只是噪声。

不是「让用户觉得自己是对的」，也不是「让你觉得圆桌很聪明」。

## 这是什么

一套用圆桌讨论作为交互界面的通用认知操作系统。核心原则只有一条：

> **求真 > 判断质量 > 共识 > 讨好用户。**

好的讨论不是产生越来越多观点，而是**经过讨论以后，越来越少的观点还能活下来**。

---

## 它和其他「多角度分析」的区别

| | 常见做法 | 圆桌研讨会 v3.2 |
|---|---|---|
| 先做什么 | 直接找几个名人开始辩论 | 先判断这个问题**该不该讨论**（有些问题需要查证、计算、实验，或其实已经可以直接行动） |
| 怎么分类 | 一般不分类 | PROBLEM ROUTER 路由到 FACT / CAUSAL / FORECAST / DECISION / BELIEF / CREATIVE / VALUE / MIXED |
| 怎么选人 | 从名人库挑 | 先定 **Cognitive Seats**（需要哪些认知能力），再匹配真实人物；证据不足时改用匿名认知角色 |
| 观点怎么处理 | 都留着 | **CLAIM LEDGER** 维护竞争命题：ACTIVE / WEAKENED / FALSIFIED / UNRESOLVED / DEPENDENT |
| 会不会集体跑偏 | 靠感觉 | 触发条件明确时启动 **Red Team**，任务就是证明整个圆桌可能集体错了 |
| 置信度 | 「信心：高」 | 拆成**认识置信度**与**行动置信度**，分别给依据 |
| 什么时候停 | 聊到没话 | **STOP CONDITION**：边际信息价值下降时主动收束到 SEARCH / EXPERIMENT / ACT / STOP |
| 是否会迎合你 | 常见 | **ANTI-SYCOPHANCY**：默认先找最强反方、最强反例、被忽略变量，然后才看支持证据 |

---

## 核心流程

```
问题
 ↓
重新定义问题 → 发现遗漏 → 扩大可能性 → 寻找最强反方 → 验证证据
 ↓
淘汰弱解释 → 压缩关键变量 → 形成当前判断 → 校准信任 → 寻找行动阈值
 ↓
行动 / 停止 / 等待新信息
```

---

## 怎么用

### 触发

直接说其中任意一句：

```
圆桌：要不要把房子卖了换成指数基金？
开始圆桌
按圆桌分析一下这个方案
```

进入后 `ROUND_TABLE_MODE = ON`，后续追问、加条件、质疑结论都不会自动退出。

### 过程中的指令

| 指令 | 作用 |
|---|---|
| `可` / `继续` | 沿当前最重要的未解决问题继续（读取 STATE，不重新开始） |
| `深挖` | 不扩张新议题，继续攻击当前核心裂缝 |
| `引入 XXX` | 邀请指定人物或认知角色加入 |
| `换人` | 重新评估阵容，替换低贡献席位 |
| `查证` | 暂停推演，优先验证最可能改变结论的事实 |
| `落地` | 停止扩张讨论，进入现实行动设计（Plan A / Plan B / 切换条件 / 下一步 1–3 个动作） |
| `止` | 结束圆桌，生成最终知识网络 |

自然语言也可以，不要求用命令。

### 每轮你会拿到什么

```
核心裂缝 / 隐藏前提 / 被削弱或淘汰的解释 / 新增关键变量
推理分叉（有效时）/ ASCII 思考模型（必要时）
当前判断：倾向 + 认识置信度 + 行动置信度
Belief Update：↑ ↓ ≈ ?
下一步最高信息价值动作：THINK / SEARCH / ASK / CALCULATE / EXPERIMENT / OBSERVE / ACT / STOP
```

---

## 文件结构

```
SKILL.md                                # v3.2 主框架：第 0–39 节完整规范
references/v3.0-panel-and-modes.md      # v3.0 人物库（含 MBTI）、快速研讨模式、org 持久化
references/deployment.md                # 部署指南：脱离 Hermes 独立运行
```

---

## 安装

```bash
npx skills add Condiwus/roundtable-seminar
```

手动使用也行：把 `SKILL.md` 的内容作为 system prompt 喂给任意兼容的模型即可。

---

## 版本历史

- **v3.2** — 升级为通用认知操作系统：PROBLEM ROUTER、SUCCESS FUNCTION、COGNITIVE SEATS、CLAIM LEDGER、RED TEAM PROTOCOL、CONVERGENCE ENGINE、INFORMATION GAIN ROUTER、TRUST CALIBRATION、JUDGMENT AUTHORITY、DECISION THRESHOLD、STOP CONDITION、ANTI-PERFORMANCE、ANTI-SYCOPHANCY。
- **v3.0** (2026-05-23) — 融合李继刚原版 `ljg-roundtable` 精华：动态发言顺序、行动标签（陈述/质疑/补充/反驳/修正/综合）、MBTI 标注、「意外视角」强制要求、org 文件自动持久化。
- **v2.1** (2026-05-15) — 新增「落地」指令与自动转型规则。
- **v1.1** (2026-05-15) — 退出质量门控、快速研讨模式。
- **v1.0** (2026-05-15) — 基于 Lisp 规范创建。

---

## 致谢

- **李继刚** 的 [`ljg-roundtable`](https://github.com/lijigang/ljg-roundtable) — v3.0 的融合来源，v3.2 在问题路由与证据纪律上继续推进。

## License

MIT
