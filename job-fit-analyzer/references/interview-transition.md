# Interview Transition Guide

Use this guide after delivering the completed job-fit report.

## Trigger Conditions

Proactively offer interview preparation **only** when **one** of the following is met:

- Overall score **≥ 65**
- Competitiveness assessment is **"Competitive"** or **"Strong Candidate"**

If score < 65, focus on gap remediation and application strategy. Only discuss interview prep if the user explicitly asks.

## Offer Style

Make the offer natural, specific, and tied to the analysis. Reference 1–2 concrete points from the report (strengths or key gaps).

### Chinese Examples
- “你的匹配度达到XX分，核心技能和经验都比较契合。要不要我基于这个JD和你的情况，帮你准备一套针对性的模拟面试题和STAR回答框架？”
- “这个职位值得投递，我已经看到你在X和Y方面的优势。要继续帮你做面试准备吗？我可以针对这个JD生成重点问题和回答思路。”

### English Examples
- “This is a solid match with a score of XX. Would you like me to create targeted mock interview questions and STAR responses based on this JD and your profile?”
- “You have strong alignment in [specific strength]. Shall I prepare customized interview coaching, including likely questions and strong answer outlines?”

## Handoff Rules (if user agrees)

Switch to / load `interview-coach` skill and pass the following data:

- Full extracted JD data
- Full extracted resume data
- Overall score + competitiveness assessment
- Top 3–5 strengths
- Top 3–5 gaps and missing qualifications
- JD problem diagnosis and Attack Points (from Phase 0)
- Application strategy recommendations

**Important**: Do **not** generate mock interview questions or answer frameworks inside `job-fit-analyzer`. Hand off cleanly to `interview-coach`.

## Low-Score Handling

For scores below 65:
- Emphasize resume tailoring and skill gap closure first.
- Offer to analyze other roles or help with long-term preparation strategy.
- Only provide interview support upon user request.