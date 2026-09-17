# Roundtable Seminar v3.2.1 Release Candidate

以最小必要认知复杂度，找到当前最值得相信、最值得行动的答案。

本项目承接「优化圆桌提示词」对话中已接受的 RC 架构与 Red Team 修改。保留已修订 Kernel、Brainstorm 的方案，完成 Deliberation、Protocols、Examples 的对齐，并归档 v3.0 / v3.1 / v3.2 原始附件。

## 项目结构

```text
roundtable-seminar/
├── SKILL.md                         运行入口与唯一全局 Router
├── references/
│   ├── brainstorm-engine.md         扩展候选空间
│   ├── deliberation-engine.md       Dialectic ↔ Reasoning
│   ├── protocols.md                 按触发条件读取的工具箱
│   └── examples.md                  行为回归案例
├── legacy/
│   ├── v3.0/Roundtable-Seminar-v3.0.md
│   ├── v3.1/Roundtable-Seminar-v3.1.md
│   └── v3.2/Roundtable-Seminar-v3.2.md
├── review/
│   ├── baseline/                    对话中 Kernel / Brainstorm RC 原文
│   ├── red-team-baseline.md          已接受的原架构审查记录
│   ├── consistency-check.md          本次检查及修订说明
│   ├── forward-check.md              独立前向检查记录
│   └── checks.json                   文件完整性与来源校验结果
└── README.md
```

## 使用

将 `SKILL.md` 与整个 `references/` 目录作为一个技能包提供给支持技能的宿主，从 `SKILL.md` 进入。只按当前需要加载对应参考文件。项目已整理为可交付文件，本次没有自动安装或修改全局技能配置。

`legacy/`、`review/` 和本 README 属于项目资料，不是运行指令；部署运行包时只包含根 `SKILL.md` 与 `references/`，不要把历史版本与当前版本同时加载。

可以用“圆桌：……”开始；“可 / 继续”“深挖”“查证”“落地”“止”等控制语义由 Kernel 定义。不要求每个问题都出现多人讨论或完整报告。

如果旧版 v3.1 仍放在宿主的项目指令中，仅加载新技能并不能保证旧规则失效。迁移时应明确替换旧版运行指令，保留其归档即可。本次未改动现有项目 `AGENTS.md` 或任何同步参考材料。

## 文件职责

| 唯一规则归属 | 内容 |
|---|---|
| [SKILL.md](SKILL.md) | 模式、用户命令、Need Router、State、可逆行动偏置、停止、自适应输出 |
| [Brainstorm](references/brainstorm-engine.md) | 独立生成、机制聚类、按缺口升级、饱和退出 |
| [Deliberation](references/deliberation-engine.md) | Dialectic / Reasoning 的内部处理、动态交锋、真人真实性 |
| [Protocols](references/protocols.md) | Evidence、Ledger、Red Team 等协议的触发、细则、返回和停止 |
| [Examples](references/examples.md) | 条件变化下应观察到的行为；不另建 Router |

核心原则仍是 Direct Path First、Light by Default、Minimum Necessary Cognitive Complexity，以及 ACT / EXPERIMENT under reversibility。它们在 Kernel 定义，其他文件遵循该定义。

## RC 合并范围

- 删除独立 Hybrid Mode，混合问题通过 Kernel 在 Dialectic、Reasoning 与直接操作之间切换。
- Claim Ledger 移至 Protocols，只有实际追踪负担加高阈值信号才考虑；普通 State 足够时不建表。
- Red Team 按共识加风险因子触发；显式审查请求按范围执行。
- Evidence 的 [C] 统一为合理推演；来源类型不被当作自动可信度排名。
- 移除全局阶梯和固定深度全流程，使 Search / Calculate / Experiment / Act 可以直接成为第一步。
- Kernel、Brainstorm 原文另有快照；运行稿仅作格式兼容、重复规则归位、路由边界与退出条件修补，未增加认知机制。

详细差异与验证范围见 [一致性检查](review/consistency-check.md)。

## 验证与限制

本 RC 包含静态格式/链接/归档完整性检查、案例走查，以及一次独立前向检查。案例集并不表示已用真实用户、真实平台或重复模型运行验证效果。它仍是 Release Candidate，后续应依据实际使用中出现的误路由做窄修订。

来源对话：[优化圆桌提示词](chatgpt-conversation://6aab7232-64fc-83ea-9d5a-50ddece4de2b)。历史附件按原始字节保存，完整性结果见 [checks.json](review/checks.json)。
