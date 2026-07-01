# JD Quality Pre-Screen Checks

This file contains the detailed procedures for Phase 0 — JD quality assessment. Each check is mandatory and must run BEFORE scoring the candidate.

## Contents
- Check 1: Salary vs. Responsibility Match
- Check 2: Red-Flag Keywords Scan
- Check 3: JD Concreteness Score
- Check 4: Generic vs. Specific Ratio
- Check 5: PUA / Toxic Culture Indicators
- Check 6: Problem Diagnosis
- Check 7: Role Scope Sanity Check (职责范围合理性)
- Summary Table Template

---

## Check 1 — Salary vs. Responsibility Match

Compare the listed salary range with the responsibilities described:
- Does the salary match the seniority implied by the responsibilities?
- If responsibilities are senior-level (e.g., "制定核心策略," "推动业务增长") but salary is entry-level → 🚩 Flag
- If salary is high but JD is vague → 🚩 Flag (might be bait-and-switch or inflated listing)
- Summarize: "薪资X vs 职责复杂度Y → 匹配/偏高/偏低"

---

## Check 2 — Red-Flag Keywords Scan

Scan the JD for terms that hint at toxic culture or excessive workload:

| Keyword Pattern | Signal | Risk Level |
|----------------|--------|------------|
| "抗压能力强" "承压能力" "有服务意识" | 工作强度大，可能有频繁加班 | 🔴 High |
| "996" "大小周" "弹性工作=随时响应" | 明确的长工时文化 | 🔴 High |
| "24小时响应" "随叫随到" | 无边界的工作侵入个人时间 | 🔴 High |
| "吃苦耐劳" "以公司为家" | PUA前兆，期望员工无条件奉献 | 🔴 High |
| "拥抱变化" "快速迭代" × 3+ | 可能意味着方向频繁变动、缺乏规划 | 🟡 Medium |
| "结果导向" "狼性文化" | 可能意味高压淘汰制 | 🟡 Medium |
| "扁平化管理" + 薪资偏低 | 可能用"扁平"掩盖晋升通道缺失 | 🟡 Medium |
| "创业氛围" + 大厂JD | 可能是内部赛马、资源紧张 | 🟡 Medium |
| "热爱工作" "有责任感" "责任心强" "敬业" | 正面词汇但可能用来包装加班文化、期望无条件付出 | 🟡 Medium |

If any 🔴 keywords found → prominently flag in JD Assessment.
If 3+ 🟡 keywords → flag as "需面试时深入了解".

---

## Check 3 — JD Concreteness Score

Assess how specific the JD is. A good JD has concrete, measurable duties. A vague JD suggests the hiring manager hasn't thought through the role.

不好的jd会用一些大词，比如负责数据分析、内容策划、活动跟进、社区运营，那说明招聘者自己没想清楚。
好的jd会写的很具体，比如基于用户分层制定运营策略，并通过A/B测试持续优化，实现转换率提升，这样你能知道具体要做什么，以及KPI是什么。

Interpretation:
- 80+: 企业想得很清楚，岗位目标明确
- 60-79: 基本清晰，大部分职责可落地
- 40-59: 中等，部分模糊，面试时需追问具体职责
- 20-39: 较模糊，企业可能没想清楚招人来做什么 → 🚩
- <20: 极度模糊 → 🚩🚩 强烈建议面试时问清楚

---

## Check 4 — Generic vs. Specific Ratio

Calculate ratio of generic soft-skill requirements to specific hard-skill requirements:
- Count "generic" requirements (沟通能力、团队协作、抗压能力、学习能力、积极主动、责任心...)
- Count "specific" requirements (技术栈、工具名、行业经验、项目类型、年限...)
- Generic/Specific ratio:
  - < 0.5: 要求很具体，企业知道要什么人 ✅
  - 0.5–1.0: 平衡正常
  - 1.0–2.0: 通用要求偏多，可能意味着"什么都想要"或自己没想清楚
  - > 2.0: 🚩 太多虚的要求，说明JD质量低，企业可能缺乏明确的用人标准

**好词识别 — 区分"空洞套话"与"真正有价值的软技能":**

并非所有通用要求都是空洞的。以下词汇虽然属于软技能范畴，但它们反映了企业对候选人"能主动解决问题、不需要保姆式管理"的真实期待，是正面信号：

| 好词 | 含义 | 为什么好 |
|------|------|---------|
| 独立思考能力 | 不盲从、能独立判断并做出决策 | 意味着上级不需要事无巨细地指导，省心 |
| 主人翁精神 / ownership | 对结果负责、不推诿、主动推进 | 区别于"合伙人意识"（后者常伴随低薪画饼） |
| 学习能力 / 自驱力 | 能快速掌握新知识、不需要被push | 在快速变化的行业中至关重要 |

**评分处理**: 在统计通用/具体比时，将上述"好词"单独标记为 ✅ 好词，**不计入"虚"的那一侧**，也不与"沟通能力""团队协作"等空洞套话混为一谈。报告中可单独说明"JD提到了X个好词，说明企业看重候选人的主动性和成长性"。

---

## Check 5 — PUA / Toxic Culture Indicators

Scan for subtle cultural red flags beyond the obvious keywords:
- "我们希望你热爱加班" / "有创业精神" → 暗示无薪加班
- "薪资open" / "上不封顶" → 通常薪资本身不高，靠画饼
- "期权激励" 但没有具体说明 → 早期公司画饼风险
- "合伙人意识" "owner心态" → 给基层员工的title inflation，期望超职责付出
- JD反复强调"价值观""文化认同"但对技能要求很少 → 可能洗脑式管理
- "试用期X个月" 在JD中显著强调 → 可能试用期压薪或试用期后不转正
- "热爱工作" / "有责任感"  在JD中反复出现且伴随其他加班信号 → 用正面词汇包装加班文化、期望员工无条件奉献
- JD中出现"我们是一家人" "温暖的大家庭" → 警惕"家庭式"PUA管理

---

## Check 6 — Problem Diagnosis: Why are they hiring?

The single most powerful thing a candidate can do in an interview is show: "I understand what problem you're trying to solve, and I've solved it before." This check reverse-engineers the JD, then cross-references the candidate's resume.

### Step 1: Infer problems from each JD responsibility

For each responsibility, ask: "What pain point or business need would cause someone to write this as a job duty?"

| JD Responsibility | Inferred Business Problem |
|---|---|
| "探索AI技术的产品化方向，挖掘用户痛点" | 公司有AI技术能力但缺乏产品化落地路径，技术团队和业务之间存在gap |
| "设计AI辅助数据生产流程" | 数据标注/生产依赖人工，效率低、成本高、难以规模化 |
| "协同算法、工程及业务团队推进项目落地" | 跨团队协作存在阻力，缺乏能把技术语言翻译成业务需求的人 |
| "模型效果评估与优化" | 当前模型评估体系不完善或缺失，无法量化衡量AI产品效果 |
| "跟踪行业动态与竞品发展" | 产品方向缺乏外部视角，可能在跟风而非引领 |

### Step 2: Cross-reference with candidate's resume

For each inferred problem, check the candidate's resume for evidence of having solved a similar problem:

- **🟢 Attack Point** — Direct experience solving this exact problem. Highlight in interview: "I noticed you're looking for X — I solved the same challenge at Y company..."
- **🟡 Partial Match** — Adjacent or partially relevant experience. Can be framed with preparation.
- **🔴 Blind Spot** — No relevant experience. Prepare a thoughtful answer showing understanding even without direct experience.

### Step 3: Generate the problem-solution mapping table

```
| JD职责 | 推断的业务问题 | 你的经验 | 攻击性 |
|--------|---------------|----------|--------|
| ... | ... | ... | 🟢/🟡/🔴 |
```

### Step 4: Generate "Interview Attack Strategy" summary

Produce 2-4 specific talking points formatted as:

> 🎯 **Attack Point #1:** "从JD看你们需要X能力——我在[前公司]做Y项目时恰好解决过类似问题，当时通过Z方法把指标从A提升到B。如果加入你们，我可以把同样的方法论带过来。"

This gives the candidate a concrete script, not just abstract advice.

---

## Check 7 — 职责范围合理性 (Role Scope Sanity Check)

检查JD的职责是否涵盖过多不相关的职能领域。本质上是"花一个人的钱干三个人的活"——候选人很难在任何一个方向获得深度成长。

### 判断标准

**第一步：列出JD中出现的所有职能领域。** 按职责描述归类，例如：

| 职能领域 | 典型关键词 |
|---------|-----------|
| 内容策划 | 内容创作、文案撰写、选题策划、短视频制作 |
| 用户增长 | 拉新、促活、裂变、渠道投放、增长黑客 |
| 数据分析 | 数据报表、用户画像、AB测试、ROI分析 |
| 商务拓展 | BD、渠道合作、异业合作、资源对接 |
| 产品运营 | 产品需求、功能迭代、用户反馈、原型设计 |

**第二步：标注角色级别。**
- 基础执行岗（0–3年经验 / 专员/助理）
- 中级岗（3–5年 / 经理/主管）
- 高级岗（5年+ / 总监/负责人）

**第三步：判定合理性。**

| 职能领域数量 | 基础执行岗 | 中级岗 | 高级岗 |
|-------------|-----------|--------|--------|
| 1–3个 | ✅ 正常 | ✅ 正常 | ✅ 正常 |
| 4–5个 | 🟡 偏多，可能难以深入 | ✅ 正常 | ✅ 正常 |
| 6–7个 | 🔴 超载，几乎不可能有深度 | 🟡 偏多 | 🟡 偏多 |
| 8+个 | 🔴🔴 严重超载，万金油岗位 | 🔴 超载 | 🟡 偏多 |

**第四步：检查领域间的相关性。** 如果多个职能领域之间存在自然关联（如"内容策划 + 社群维护 + 数据分析"常见于新媒体运营岗），则严重程度可降一级。如果领域之间毫无关联（如"数据分析 + 视觉设计 + 商务拓展"），则升级风险。

### 输出格式

报告中应包含：
1. 识别出的职能领域列表（打勾标记）
2. 角色级别
3. 合理性判断 + 风险说明
4. 对候选人的建议：如果投递，面试时追问"这个岗位最核心的前三项职责是什么"来判断真实预期

### 典型案例

**🚩 红旗案例（基础执行岗，JD涵盖7个领域）：**
> "负责品牌内容策划与文案撰写；制定用户增长策略并执行渠道投放；搭建数据监控体系并输出周报；策划并落地线上线下营销活动；维护核心用户社群与私域流量；协助商务团队完成异业合作对接；参与产品需求讨论与功能验收。"

→ 判定：花一个人的钱干三个人的活（内容运营+增长运营+数据分析+活动运营+社群运营+BD+产品），建议慎投。

---

## Summary Table Template

Generate this table in the report:

| 检查项 | 结果 | 风险 |
|--------|------|------|
| 薪资vs职责 | 匹配/偏高/偏低 | - |
| 红色关键词 | 找到X个 | 🔴/🟡/✅ |
| JD具体性 | XX分 | - |
| 通用/具体比 | X:1 | - |
| PUA检测 | 通过/有X个危险信号 | 🔴/✅ |
| 职责范围 | X个领域 / 正常·偏多·超载 | 🔴/🟡/✅ |
| **综合可投性** | **建议投递 / 慎投 / 需面试验证** | - |
