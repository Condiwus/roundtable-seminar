# v3.2.1 RC 一致性检查

日期：2026-09-17。范围：根 SKILL.md 与 references 四文件；legacy / review 为非运行资料。

## 修订结论

本轮未发现仍需修复的跨文件 Router 冲突、重复维护的协议细则或强制全局流程。这里的“无重复规则”指同一规则有唯一维护位置；摘要、交叉引用和案例可以复述其用途，不另设不同的触发或执行要求。

## 核查结果

| 项目 | 结论与处理 |
|---|---|
| Router 归属 | Kernel 第 9–10 节唯一全局调度；Engine / Protocol 返回结果与 need |
| Hybrid | 执行模式已移除；只在删除说明、反例或归档中提及 |
| 直接路径 | Search、Ask、Calculate、Experiment、Act 可作为第一操作 |
| Light 默认 | Brainstorm 保留三个独立方向；Deliberation 从一条分歧开始，不强制人数 |
| 候选配额 | 3–5 为参考；两个候选足以测试可立即退出 |
| 升级与降级 | 移除 Kernel / Protocol 的全局阶梯；局部升级允许按缺口选择、随时返回 |
| Claim Ledger | Protocol 唯一维护触发、字段、状态；实际追踪负担是必要条件 |
| Red Team | Protocol 唯一维护默认共识加风险触发；共识人数不足以触发 |
| Evidence | [A]/[B]/[C]/[D] 仅在 Protocol 定义，[C] 为合理推演 |
| 真人真实性 | Deliberation 唯一维护详细规则；Brainstorm 引用而不复制 |
| Round Summary | Kernel 唯一维护自适应输出，Engine 不另强制完整摘要 |
| State / Ledger | 普通主张只进 State；已证伪与证据不足不混淆 |
| 循环与退出 | 无变化可立即退出；两次无变化往返时明确暂停 |
| 可逆行动 | 区分 ACT 与 EXPERIMENT；便宜不等于有区分力，可逆不等于已有外部授权 |
| 事实与价值 | 混合问题按实际瓶颈切换，事实不能自动推出用户应如何选择 |
| 安装边界 | 没有改动现有 AGENTS.md、同步材料或全局安装目录 |

## 保留稿的一致性修补

原始 Kernel 与 Brainstorm RC 完整保存在 baseline/，便于对照；不是以重写稿冒充原文。

Kernel：将版本与标签放入兼容的 metadata；修复标题层级与文件链接；协议细则归位并改为引用；删除与直接实验冲突的全局升级链；澄清 CLARIFY、EVIDENCE、OBSERVE 不是新增路由；补齐单命题检验与执行偏好的边界；区分议题停止和模式退出。

Brainstorm：保留 Light 搜索、独立生成、机制聚类及按需升级机制；把候选数由硬配额改为参考；合并重复的独立生成、去重与预算说明；全局路由建议统一交回 Kernel；饱和、现实测试与退出规则对齐，不要求逐级跑满。

Deliberation、Protocols、Examples 在原草案及已接受 Red Team 基线上修订；删除旧的强制步骤并集中规则所有权。README 最后编写，用于交付和迁移，不充当运行 Router。

## 验证记录与限度

- 官方 skill-creator `quick_validate.py`：对运行技能校验 frontmatter、命名及未完成占位符。
- 文件检查：Markdown 本地链接及锚点、围栏配对、必需文件、历史原件字节哈希、RC 快照完整性；结果见 [checks.json](checks.json)。
- 案例走查：examples.md 的 19 组场景及边界变体，人工对照触发/禁止行为；包括直接回答、计算、概念争议、轻量发散、混合问题、权限、Ledger、共识、停止及真实性。
- 独立前向检查：五个实际回答样本及修补见 [forward-check.md](forward-check.md)。这是一次模型文本演练，不是重复实验或真实产品运行。

格式校验不会证明语义正确；人工审查也不能保证所有未来输入都无误路由。当前交付保持 RC 状态，不把有限检查描述为正式发布认证。
