---
name: interview-coach
description: Provide comprehensive, personalized interview preparation for job candidates. Generate tailored questions, STAR answers, follow-ups, gaps analysis, and role-specific tips based on JD and resume. Use for 'interview prep', 'mock interview', 'prepare for interview', '面试准备', '模拟面试', or when job-hunter / job-fit-analyzer reaches interview phase.
metadata:
  type: workflow
  version: "1.1"
  domain: career
---

# Interview Coach

## Purpose

Deliver high-quality, personalized interview preparation by analyzing a candidate’s resume against a target job description. Generate relevant questions, craft realistic STAR answers, predict follow-ups, identify gaps, and provide actionable tactics.

## When to Use

- User requests interview preparation, mock interview, or coaching
- User provides (or previously shared) a job description and resume
- `job-hunter` skill reaches Phase 3 (Interview Preparation)
- `job-fit-analyzer` skill reaches Phase 4 and user wants interview support

**If JD or resume is missing:** Ask the user to provide both before proceeding. Reuse data from previous job-fit-analyzer runs when available.

## Inputs

**Required:**
- Target Job Description (text, file, or URL)
- Candidate Resume (text or file)

**Optional (recommended):**
- Interview stage and format
- Company name

## Workflow

### Phase 1: Extract and Analyze

Parse JD and resume. Refer to `references/extraction-criteria.md`.

**Cross-analysis:** Identify mismatches, gaps, career transitions, and likely probing areas.

### Phase 2: Generate Personalized Questions

Create a categorized question bank. Refer to `references/question-bank-guide.md`.

**Categories:**
- Role-Specific Technical (5-10)
- Behavioral (8-12)
- Resume Deep-Dive (5-8)
- Situational / Case (3-5)
- Company-Specific (3-5)
- Questions for the Interviewer (5-8)

### Phase 3: Craft STAR Answers

For all behavioral questions, provide STAR-structured sample answers. Refer to `references/star-framework-guide.md`.

- Use real resume evidence only
- Keep answers concise and metric-driven
- Include mapping to resume, key takeaway, and confidence level

### Phase 4: Predict Follow-Ups

Anticipate drill-downs, hypotheticals, and probing questions for major categories. Provide response guidance.

### Phase 5: Highlight Preparation Gaps

Rank gaps by severity (Critical / High / Medium / Low) with specific action items. Refer to `references/preparation-gaps.md`.

### Phase 6: Role-Specific Tips

Deliver practical advice on technical approach, communication, format nuances, and red flags to avoid.

### Phase 7: Output

1. Generate a clean, structured HTML report (`interview-prep-report.html`)
2. Present it using `render_file` or `present_files`
3. Provide a concise conversation summary (top 3 questions + top 3 gaps)

Use `assets/interview-prep-template.html` if available.

## References

- `references/extraction-criteria.md` — Detailed parsing rules
- `references/question-bank-guide.md` — Question taxonomy and patterns
- `references/star-framework-guide.md` — STAR methodology and examples
- `references/preparation-gaps.md` — Gap analysis framework

## Language

- Match the user’s query language as primary output
- Use English for technical content when JD is in English
- Keep STAR answers in the same language as the user’s request

## Integration Notes

- **job-hunter**: Call this skill in Phase 3
- **job-fit-analyzer**: Use extracted gaps and data in Phase 5

## Important Rules

- Never fabricate experiences not supported by the resume
- Calibrate difficulty to the role’s seniority level
- Research company via tools when needed for realistic questions
- Be honest and constructive about weaknesses

---

### 推荐配套目录结构

创建以下文件来进一步完善：

1. `references/extraction-criteria.md`
2. `references/question-bank-guide.md`
3. `references/star-framework-guide.md`
4. `references/preparation-gaps.md`
5. `assets/interview-prep-template.html`（可选）

---

**这个版本是否符合你的预期？**

如果你需要，我可以继续帮你：
- 撰写其中一个 `references/` 文件
- 创建完整的 `assets/interview-prep-template.html`
- 进一步微调某个部分

直接告诉我下一步怎么调整即可！