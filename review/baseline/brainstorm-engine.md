# Brainstorm Engine

> **Mission**
>
> 当正确答案可能尚未进入候选空间时，以最小必要成本扩大搜索空间。

Brainstorm 不负责：

> 哪个答案最正确？

它负责：

> **还有什么重要可能被我们漏掉了？**

核心原则：

> **先提高 Recall，再提高 Precision。**

但同时：

> **不要为了发散而发散。**

---

# 1. DEFAULT PHILOSOPHY

Brainstorm 默认使用：

`LIGHT MODE`

而不是完整 Brainstorm。

默认流程：

```text
Search Target
↓
3 Independent Search Directions
↓
Generate
↓
Cluster
↓
Candidate Map
↓
Return to Kernel
```

只有当这套轻量搜索仍无法形成足够多样的 Candidate Space 时，

才升级。

原则：

> **Earn Complexity.**

---

# 2. WHEN TO CALL

Kernel 判断：

`CURRENT NEED = POSSIBILITY`

时调用。

典型信号：

- 用户只有一个方案
- 用户陷入 A / B False Binary
- 当前候选高度相似
- 第一个答案形成明显锚定
- 所有方案来自同一种行业逻辑
- 现有解释都无法很好覆盖问题
- 用户明确问“还有没有别的可能？”
- 当前最值得做的是扩大候选空间

---

# 3. WHEN NOT TO CALL

## Fact Missing

关键事实未知：

→ `SEARCH`

## User Constraint Missing

缺目标、预算、偏好、数据：

→ `ASK`

## Candidates Already Rich

已经存在多个真正不同的候选：

→ `REASONING`

## Reality Can Decide

可以低成本验证：

→ `EXPERIMENT`

## Ready to Execute

已经知道做什么：

→ `ACT`

## Simple Problem

Direct Answer 足够：

→ `DIRECT`

---

# 4. SEARCH TARGET

Brainstorm 开始前必须定义：

`SEARCH TARGET`

不是：

> 关于这个问题多想一些。

而是：

> **我们具体缺哪一类可能？**

例如：

用户问：

> 成年人怎么学英语更有趣？

Search Target 可以是：

> 找到不同于传统课程的学习机制。

而不是：

> 想 20 个英语学习产品。

---

# 5. LIGHT MODE — DEFAULT

默认只选择：

`3 Independent Search Directions`

它们应该尽量正交。

例如：

```text
Problem:
成年人如何持续学英语？

Direction A
学习机制

Direction B
娱乐 / 游戏机制

Direction C
真实使用场景
```

或者：

```text
商业问题

A
用户

B
商业机制

C
系统 / 行业结构
```

不要求每次召集完整 Cognitive Panel。

---

# 6. INDEPENDENT GENERATION

第一轮必须：

> **Independent Generation Before Interaction**

每个 Search Direction 独立生成。

禁止：

- 阅读其他方向后补充
- 围绕第一个答案变体
- “我同意 X”
- 提前批判
- 提前排名
- 提前形成共识

原因：

```text
Independent Search

A → Space A
B → Space B
C → Space C
```

而不是：

```text
Idea A
↓
所有方向围绕 A
↓
A1 / A2 / A3
```

Brainstorm 阶段：

> **最大化独立搜索。**

Deliberation 阶段：

> **最大化相互压力。**

---

# 7. LIGHT GENERATION PROMPT

每个 Search Direction 默认只回答两个问题：

## Q1

> **从这个方向看，最值得进入候选空间的 1–2 个不同机制是什么？**

## Q2

> **其中哪个洞察最可能改变我们现在对问题的理解？**

要求：

- 简短
- 具体
- 机制不同
- 不要求完整方案
- 不进行详细反驳

默认不要写长篇专家小作文。

---

# 8. CANDIDATE, NOT ANSWER

Brainstorm 产生的是：

`CANDIDATE`

不是：

`JUDGMENT`

每个 Candidate 只需要：

```text
Candidate

Mechanism
为什么可能有效？

Difference
与现有候选真正不同在哪里？

Key Unknown
什么还不知道？
```

必要时补：

`Evidence Status`

但 Brainstorm 不负责完整证据审查。

---

# 9. CLUSTER

生成后立即按：

> **Underlying Mechanism**

聚类。

不要按：

- 标题
- 包装
- 人物
- 表达方式

聚类。

例如：

```text
AI 英语短剧
连续剧情学英语
追剧学口语
剧情闯关英语
```

可能都属于：

`Narrative-driven Learning`

因此只能算：

> 一个机制家族。

---

# 10. LIGHT EXIT TEST

Cluster 后问：

> **现在是否已经存在 3–5 个真正不同、值得继续检查的候选？**

如果：

`YES`

停止 Brainstorm。

返回 Kernel。

如果：

`NO`

才允许升级。

---

# 11. ESCALATION LADDER

Brainstorm 逐级升级：

```text
LEVEL 1
Light Independent Search

↓

LEVEL 2
Add Cognitive Seats

↓

LEVEL 3
Cross-domain Search

↓

LEVEL 4
Assumption Breaking

↓

LEVEL 5
Deep Independent Brainstorm
```

不要默认 Level 5。

---

# 12. LEVEL 2 — COGNITIVE SEATS

如果 Light Search 仍高度同质，

选择 3–5 个 Cognitive Seats。

可能包括：

- Mechanism
- Practitioner
- User / Customer
- Behavioral
- Systems
- Cross-domain
- Contrarian
- Constraint Breaker
- Simplifier
- Future
- Local / Industry

选择标准：

> **哪个大脑最可能打开新的机制空间？**

不是：

> 谁最有名？

---

# 13. ORTHOGONALITY

Cognitive Seats 必须尽量：

`ORTHOGONAL`

例如：

差：

```text
营销专家
广告专家
增长专家
短视频专家
```

如果他们最终都使用：

> 流量漏斗模型，

认知多样性仍然很低。

更好的组合可能是：

```text
用户行为
内容叙事
平台机制
产品设计
反方
```

目标：

> **Mechanism Diversity > Profession Diversity**

---

# 14. LEVEL 3 — CROSS-DOMAIN SEARCH

如果同领域搜索仍然贫瘠，

问：

> **哪个表面无关领域解决过结构相似的问题？**

寻找：

> Mechanism Isomorphism

不是表面类比。

例如：

```text
成年人学英语
↓
真正问题：
如何让高延迟回报行为获得即时反馈？
↓
相邻结构：
游戏
健身
短剧
社交产品
习惯产品
```

然后问：

> 哪个机制可以迁移？

---

# 15. LEVEL 4 — ASSUMPTION BREAKING

如果搜索空间仍被默认条件限制，

建立：

`ASSUMPTION LIST`

问：

> **哪个限制其实只是默认假设？**

例如：

```text
英语学习必须：
有老师
有教材
每天学习
先背单词
系统推进
看起来像学习
```

逐个测试：

```text
If assumption removed
↓
Does new search space appear?
```

如果没有：

停止攻击该假设。

---

# 16. LEVEL 5 — DEEP INDEPENDENT BRAINSTORM

只有复杂、高价值且候选空间仍不足时使用。

此时每个 Cognitive Seat 独立回答五问。

---

## Q1 — Biggest Misunderstanding

> 这个问题最大的误解或错误默认前提是什么？

---

## Q2 — Strongest Possibilities

> 从你的认知模型出发，最值得进入候选空间的 2–3 个机制是什么？

---

## Q3 — Judgment-Changing Insight

> 如果只能保留一个会改变当前判断的洞察，它是什么？

---

## Q4 — Counterintuitive Possibility

> 有没有一个反直觉但值得认真检查的可能？

---

## Q5 — Mechanism / Case / Experiment

> 有没有机制、案例、实验或相邻领域现象让这个方向变得具体？

如果没有可靠事实依据：

标记：

`HYPOTHESIS`

禁止伪造成事实。

---

# 17. NO INTERACTION DURING GENERATION

即使进入 Deep Mode，

第一轮仍然禁止席位相互回应。

因为：

```text
Brainstorm
=
Search
```

不是：

```text
Brainstorm
=
Debate
```

所有互动、攻击、比较：

留给 Deliberation。

---

# 18. IDEA POOL

只有 Deep Mode 或候选较多时才建立完整：

`IDEA POOL`

字段：

```text
IDEA

MECHANISM

DIFFERENCE

POTENTIAL VALUE

EVIDENCE STATUS

KEY UNKNOWN
```

Light Mode 不需要完整表格。

---

# 19. DEDUPLICATION

判断两个 Candidate 是否实际上属于同一机制。

核心问题：

> **如果把名称和包装全部删掉，它们解决问题的方法是否相同？**

如果相同：

合并。

目标：

> **Mechanism Diversity**

而不是：

> Idea Quantity。

---

# 20. DIVERSITY TEST

只有怀疑 Fake Diversity 时调用。

检查：

## Mechanism Diversity

底层机制不同吗？

## Stakeholder Diversity

是否只站在一个参与者角度？

## Time-scale Diversity

是否全部只解决短期？

## Risk Diversity

是否全部是安全的小改良？

## Domain Diversity

是否全部来自同一行业模型？

不要求每次完整检查五项。

---

# 21. COGNITIVE RANK

只有 Candidate 数量仍然较多时调用。

Rank 的目标：

> **决定什么值得进一步验证。**

不是：

> 决定最终赢家。

可以检查：

- Distinctiveness
- Explanatory Power
- Evidence Potential
- Decision Relevance
- Information Value

不要求数值评分。

优先使用：

`HIGH / MEDIUM / LOW`

或者直接定性排序。

---

# 22. FALSIFIABILITY

对于现实 Claim，

额外检查：

> 原则上能否被验证或推翻？

但不要把：

> Falsifiability

机械用于纯创意概念。

创意早期允许：

`SPECULATIVE`

后续进入 Reasoning / Experiment 再增加验证压力。

---

# 23. WILDCARD

只有出现真正满足以下条件的 Candidate 才保留：

`WILDCARD`

条件：

- 与主流机制显著不同
- 当前证据可能较弱
- 不是纯随机幻想
- 如果成立会显著改变问题结构

最多：

`0–1`

不要为了格式固定制造 Wildcard。

---

# 24. SATURATION TEST

问：

> **再增加一个搜索方向，最可能产生新机制，还是新措辞？**

如果主要会产生：

> 新措辞，

Brainstorm Saturated。

立即停止。

---

# 25. DIMINISHING RETURNS

以下情况说明边际价值下降：

- 新 Idea 不断进入已有 Cluster
- Cross-domain 不再产生新机制
- Assumption Breaking 只产生牵强方案
- Candidate Map 连续一轮没有变化
- 当前瓶颈已经变成“哪个更可信”

此时：

> **STOP BRAINSTORMING**

---

# 26. BRAINSTORM OUTPUT — LIGHT

默认只返回：

## Search Target

我们在寻找什么？

## Candidate Map

```text
A — Mechanism
B — Mechanism
C — Mechanism
D — Mechanism
```

## Most Important New Insight

哪一点真正扩大了问题？

## Key Unknown

现在最值得验证什么？

## Next Operation

返回 Kernel。

---

# 27. BRAINSTORM OUTPUT — DEEP

只有 Deep Mode 才输出：

## Problem Reframe

问题是否被重新定义？

## Candidate Clusters

3–5 个高价值机制。

## Newly Discovered Variables

新增重要变量。

## Broken Assumptions

被打开的默认限制。

## Wildcard

如果存在。

## Key Unknown

最能区分候选的未知。

## Recommended Next Operation

例如：

```text
REASONING
SEARCH
ASK
EXPERIMENT
```

---

# 28. HANDOFF TO DELIBERATION

只有确实需要 Deliberation 时，

传递最小必要信息：

```text
REAL QUESTION

CANDIDATES

CORE MECHANISMS

KEY VARIABLES

KEY ASSUMPTIONS

KEY UNKNOWN

NEXT NEED
```

不要把 Brainstorm 的所有原始输出全部传过去。

---

# 29. HANDOFF DOES NOT FORCE DELIBERATION

Brainstorm 结束后：

不要默认：

```text
Brainstorm
→ Deliberation
```

重新交给 Kernel。

例如：

```text
Brainstorm
↓
发现真正只差市场规模
↓
SEARCH
```

或者：

```text
Brainstorm
↓
发现两个方案都能低成本测试
↓
EXPERIMENT
```

或者：

```text
Brainstorm
↓
已经出现明显可逆方案
↓
ACT
```

---

# 30. FAILURE MODE — IDEA SPAM

症状：

> 30 个点子。

修正：

```text
Cluster
↓
Mechanism Families
```

---

# 31. FAILURE MODE — FAKE DIVERSITY

症状：

```text
A
A+
A Pro
A Max
```

修正：

> Orthogonality + Cross-domain。

---

# 32. FAILURE MODE — CELEBRITY THEATER

症状：

> 五个名人各写一篇文章。

修正：

> Search Direction / Cognitive Seat first。

Brainstorm 默认甚至不需要真人。

---

# 33. FAILURE MODE — EARLY CRITICISM

症状：

Idea 刚出现：

> “但是……”

修正：

> Generation before Evaluation。

---

# 34. FAILURE MODE — NOVELTY ADDICTION

症状：

因为新颖就认为更好。

修正：

> Novel ≠ True.

Brainstorm 只判断：

> 值不值得继续检查。

---

# 35. FAILURE MODE — ENDLESS CREATIVITY

症状：

已有足够候选仍不断增加。

修正：

> Saturation Test。

---

# 36. FAILURE MODE — OVER-ENGINEERING

症状：

一个简单：

> “还有别的方法吗？”

却运行：

```text
5 Cognitive Seats
Five Questions
Cross-domain
Assumption Breaking
Cognitive Rank
Wildcard
```

修正：

> **Return to LIGHT MODE.**

---

# 37. FAILURE MODE — BRAINSTORM AS FINAL JUDGMENT

症状：

Brainstorm 后直接宣布：

> C 最好。

修正：

问：

> 我们现在拥有的是 Candidate，还是 Judgment？

如果只是 Candidate：

返回 Kernel。

---

# 38. FAILURE MODE — WRONG SEARCH TARGET

症状：

用户问：

> 为什么员工不投入？

系统 Brainstorm：

> 20 种激励员工的方法。

但真正需要搜索的是：

> 低投入的竞争原因。

修正：

```text
Problem Discovery
↓
Search Target Reframe
```

---

# 39. COMPLEXITY BUDGET

Brainstorm 的默认复杂度：

```text
LIGHT
3 Search Directions
1–2 Candidates each
Cluster
Return
```

只有明确失败才升级。

可以理解为：

```text
Need for Diversity ↑
+
Value of Missing Candidate ↑
+
Problem Complexity ↑

        ↓

Brainstorm Depth ↑
```

不是：

> 用户说“深度思考” → 自动生成更多内容。

---

# 40. QUALITY GATE

Brainstorm 结束前只检查最关键的六项：

## Search Target

我们搜索的是正确问题吗？

## Independence

是否避免了第一答案锚定？

## Mechanism Diversity

候选真的不同吗？

## Novel Information

有没有发现原来没进入模型的重要机制？

## Saturation

继续发散还有价值吗？

## Next Need

现在缺的是：

- 判断？
- 事实？
- 用户信息？
- 实验？
- 行动？

如果已经知道 Next Need：

返回 Kernel。

---

# 41. RELATIONSHIP WITH DELIBERATION

```text
BRAINSTORM
“What might we be missing?”
        │
        ▼
Candidate Space
        │
        ▼
KERNEL
        │
        ▼
必要时：
DELIBERATION
“Which candidates survive?”
```

注意 Kernel 位于两者之间。

不要硬编码：

```text
Brainstorm → Deliberation
```

---

# 42. RELATIONSHIP WITH REALITY

如果 Brainstorm 最终得到：

```text
A
B
```

且现实测试：

- 便宜
- 快
- 可逆
- 可观察

则：

```text
Brainstorm
↓
Experiment
```

而不是：

```text
Brainstorm
↓
更多 Brainstorm
↓
Reasoning
↓
更多 Reasoning
```

---

# 43. FINAL PRINCIPLE

Brainstorm Engine 最重要的能力不是：

> **产生很多 Idea。**

而是：

> **发现我们是否遗漏了一种完全不同的机制。**

因此：

```text
默认：
少量独立搜索
↓
形成机制不同的候选
↓
停止

只有失败：
增加 Cognitive Seats
↓
Cross-domain
↓
Assumption Breaking
↓
Deep Brainstorm
```

最终：

> **Search broadly enough, but no broader.**

Brainstorm 的职责只有两个：

1. 防止正确答案因为没被想到而输掉；
2. 在候选空间已经足够丰富时，立刻停止。

因为真正成熟的发散能力，

不是：

> **永远还能再想一个。**

而是：

> **知道什么时候已经想够了。**
