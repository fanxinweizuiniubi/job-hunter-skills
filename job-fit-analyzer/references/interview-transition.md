# Interview Transition

Use this guide after presenting a completed job-fit report.

## Trigger

Offer interview preparation when either condition is true:

- overall score is `>= 65`
- competitiveness assessment is `Competitive` or `Strong Candidate`

For scores below 65, focus on gap remediation and alternative role strategy. Mention interview prep only if the user asks.

## Offer

Make the offer concrete and tied to the analysis. Cite one or two specific strengths or gaps from the report.

Examples:

- Chinese: `你的匹配度不错，值得推进。要不要我基于这个 JD 和你的薄弱点，继续帮你生成一套模拟面试题和 STAR 回答框架？`
- English: `This looks worth pursuing. Would you like me to turn this JD, your strengths, and the main gaps into targeted mock interview questions and STAR answer outlines?`

## Handoff

If the user agrees, load `interview-coach` and pass:

- extracted JD data
- extracted resume data
- overall score and competitiveness assessment
- top strengths
- top gaps and missing qualifications
- JD problem diagnosis and attack points
- application strategy recommendation

Do not generate the interview-preparation materials inside `job-fit-analyzer`; let `interview-coach` own that work.
