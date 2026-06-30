# JD Quality Pre-Screen Checks

This file contains the detailed procedures for Phase 0 — JD quality assessment. Each check is mandatory and must run BEFORE scoring the candidate.

## Contents
- Check 1: Salary vs. Responsibility Match
- Check 2: Red-Flag Keywords Scan
- Check 3: JD Concreteness Score
- Check 4: Generic vs. Specific Ratio
- Check 5: PUA / Toxic Culture Indicators
- Check 6: Problem Diagnosis
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
| "抗压能力强" "承压能力" "高压环境" | 工作强度大，可能有频繁加班 | 🔴 High |
| "996" "大小周" "弹性工作=随时响应" | 明确的长工时文化 | 🔴 High |
| "24小时响应" "随叫随到" | 无边界的工作侵入个人时间 | 🔴 High |
| "吃苦耐劳" "以公司为家" | PUA前兆，期望员工无条件奉献 | 🔴 High |
| "拥抱变化" "快速迭代" × 3+ | 可能意味着方向频繁变动、缺乏规划 | 🟡 Medium |
| "结果导向" "狼性文化" | 可能意味高压淘汰制 | 🟡 Medium |
| "扁平化管理" + 薪资偏低 | 可能用"扁平"掩盖晋升通道缺失 | 🟡 Medium |
| "创业氛围" + 大厂JD | 可能是内部赛马、资源紧张 | 🟡 Medium |

If any 🔴 keywords found → prominently flag in JD Assessment.
If 3+ 🟡 keywords → flag as "需面试时深入了解".

---

## Check 3 — JD Concreteness Score

Assess how specific the JD is. A good JD has concrete, measurable duties. A vague JD suggests the hiring manager hasn't thought through the role.

Scoring (0-100):
- Each responsibility with: measurable outcome / specific technology / concrete scenario → +15
- Each responsibility that is generic ("负责XX工作" "参与XX项目") → +5
- Each requirement with: specific skill name / years / certification → +10
- Each requirement that is generic ("良好的沟通能力" "积极主动") → +2
- Bonus: JD mentions team size, reporting structure, or project stage → +10

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

---

## Check 5 — PUA / Toxic Culture Indicators

Scan for subtle cultural red flags beyond the obvious keywords:
- "我们希望你热爱加班" / "有创业精神" → 暗示无薪加班
- "薪资open" / "上不封顶" → 通常薪资本身不高，靠画饼
- "期权激励" 但没有具体说明 → 早期公司画饼风险
- "合伙人意识" "owner心态" → 给基层员工的title inflation，期望超职责付出
- JD反复强调"价值观""文化认同"但对技能要求很少 → 可能洗脑式管理
- "试用期X个月" 在JD中显著强调 → 可能试用期压薪或试用期后不转正
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

## Summary Table Template

Generate this table in the report:

| 检查项 | 结果 | 风险 |
|--------|------|------|
| 薪资vs职责 | 匹配/偏高/偏低 | - |
| 红色关键词 | 找到X个 | 🔴/🟡/✅ |
| JD具体性 | XX分 | - |
| 通用/具体比 | X:1 | - |
| PUA检测 | 通过/有X个危险信号 | 🔴/✅ |
| **综合可投性** | **建议投递 / 慎投 / 需面试验证** | - |
