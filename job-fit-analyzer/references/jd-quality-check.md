# JD Quality Pre-Screen Checks

Phase 0 mandatory checks. Run **before** candidate scoring.

## Check 1: Salary vs Responsibility Match
Compare salary range with implied seniority:
- Senior responsibilities (策略制定、业务增长等) 但薪资偏低 → 🚩
- 高薪但职责模糊 → 🚩（可能 bait-and-switch）
- 输出："薪资X vs 职责复杂度Y → 匹配/偏高/偏低"

## Check 2: Red-Flag Keywords
Scan for toxic culture / overwork signals:

| Pattern | Risk |
|--------|------|
| 抗压能力强、996、大小周、24h响应、吃苦耐劳、有服务意识 | 🔴 High |
| 狼性文化、结果导向、拥抱变化（多次） | 🟡 Medium |
| 合伙人意识、owner心态、创业氛围（低薪） | 🟡 Medium |

≥1个 🔴 或 ≥3个 🟡 → 在报告中显著标记。

## Check 3: JD Concreteness Score (1-100)
评估职责是否具体、可衡量。
- 80+：优秀，目标清晰
- 60-79：基本合格
- 40-59：中等，面试需追问
- <40：模糊 → 🚩 建议慎投

判断哲学：不好的jd会用一些大词，好的jd会写的很具体。

## Check 4: Generic vs Specific Ratio
统计「通用软技能要求」vs「具体硬技能要求」比例。
- <0.5：优秀
- 0.5-1.0：正常
- 1.0-2.0：偏泛
- >2.0：🚩 质量较低

**好词例外**（不计入通用虚词）：
- 独立思考能力、主人翁精神、自驱力、ownership → 标记为正面信号


## Check 5: PUA / Toxic Culture Indicators
额外扫描：
- 薪资open、上不封顶、期权（无细节）、我们是一家人、试用期重点强调等
- 反复出现“热爱工作”“责任心强”并伴随加班信号 → 警惕

## Check 6 — Problem Diagnosis: Why are they hiring?
为每个主要职责推断业务痛点，并与候选人经历匹配，生成攻击点（Attack Points）。

哲学：面试官期望招人来帮他解决问题，所以可以推断JD背后的业务痛点。

## Check 7 — 职责范围合理性 (Role Scope Sanity Check)

检查JD的职责是否涵盖过多不相关的职能领域。看公司是否想要"花一个人的钱干三个人的活"。

统计JD覆盖的职能领域数量及相关性：
- 基础岗 >4个领域 → 超载风险高
- 中高级岗 >6个领域 → 需谨慎
输出领域列表 + 合理性判断。

## Summary Table Template

Generate this table in the report:

| 检查项 | 结果 | 风险 |
|--------|------|------|
| 薪资匹配 | ... | ... |
| 红旗关键词 | ... | 🔴/🟡 |
| JD具体性 | XX分 | ... |
| 通用/具体比 | X:1 | ... |
| PUA/毒性文化 | ... | ... |
| 职责范围 | X个领域 | ... |
| **综合可投性** | **建议投递 / 慎投 / 需面试验证** | -
