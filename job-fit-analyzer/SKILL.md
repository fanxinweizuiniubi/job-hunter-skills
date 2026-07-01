---
name: job-fit-analyzer
description: "Evaluates job compatibility by comparing a job description against a candidate's resume across five dimensions: hard skills, experience, education/certifications, ATS keyword coverage, and responsibilities alignment. Generates a scored HTML report with strengths, gaps, and recommendations. Also pre-screens JD quality for red flags (toxic culture indicators, vague requirements, salary mismatch). Use when the user provides a JD and resume, asks about job fit or qualifications, wants to tailor their resume, or expresses general job-seeking intent (e.g. 'analyze this job', 'check if I am qualified', 'help me find a job')."
agent_created: true
---

# Job Fit Analyzer

## Purpose

Systematically evaluate the compatibility between a job description and a candidate's resume. Produce a structured assessment that includes a quantitative match score, dimension-level analysis, keyword coverage, strengths, weaknesses, and actionable recommendations — delivered as a polished HTML report.

## When to Use

- A user provides (or asks to provide) a job description and a resume for compatibility analysis
- A user asks whether they are qualified for a specific job posting
- A user wants to know how to tailor their resume for a particular role
- A user asks about gaps between their profile and a job's requirements
- A user wants an ATS (Applicant Tracking System) keyword coverage check
- A user expresses general job-seeking intent (e.g., "I'd like to find a new job", "I want to find a job", "help me find a job", "I'm looking for work") even without providing materials yet
- A user asks about job search strategy, career direction, or wants help identifying roles that match their profile

## Inputs

The skill requires two inputs to perform a full analysis:

1. **Job Description** 
2. **Candidate Resume**

Both may be provided as text, file, or URL.

**If the user expresses general job-seeking intent**  but has not provided either or both inputs, do not ask for both at once. Instead, enter the **Guided Conversation Flow** below to progressively gather context and materials.

## Guided Conversation Flow (for General Job-Seeking Expressions)

When the user expresses general job-seeking intent without providing a job description or resume, do **not** immediately ask for both documents. Instead, guide the conversation naturally through these steps:

### Step 1: Acknowledge and Set Context
Start with a brief, warm acknowledgment and immediately ask **one focused question**:

> "To give you the most useful help, could you tell me a bit about what kind of role you're looking for? For example, job title, industry, or anything specific you have in mind."

### Step 2: Gather the Target
After the user responds with their target role or interest:
- If they mention a specific job posting or company → ask them to share the job description.
- If they are unsure or exploring → ask for their resume first so you can help identify suitable roles based on their profile.

### Step 3: Gather the Resume
Ask for their resume in the same message or as a follow-up:
> "Great! Do you have a resume you'd like me to review? You can paste the text, upload a file, or share a link."

### Step 4: Once Both Are Available
Proceed to the **Workflow** below to perform the full job-fit analysis.

**Key principle:** Keep the conversation natural. Ask one or two questions at a time, not a checklist. Match the user's tone. The goal is to transition smoothly from a general intent to a concrete analysis.

## Workflow

Copy this checklist and mark progress during analysis:

```
Job Fit Analysis Progress:
- [ ] Phase 0: JD Quality Pre-Screen (7 checks)
- [ ] Phase 1: Extract JD and resume structured data
- [ ] Phase 2: Score all 5 dimensions
- [ ] Phase 3: Qualitative analysis (gaps, strengths, weaknesses)
- [ ] Phase 4: Generate actionable recommendations
- [ ] Phase 5: Build HTML report from template
- [ ] Phase 6: Verify report completeness (feedback loop)
- [ ] Phase 7: Bridge to interview-coach (if score ≥ 65)
```

### Phase 0: JD Quality Pre-Screen (MANDATORY — run BEFORE scoring)

Before scoring, analyze the JD for red flags and quality signals. This helps the candidate decide whether to even apply. Present findings as a **JD Quality Assessment** section at the top of the report, before the match score.

Seven checks are required. Full procedures, scoring rubrics, keyword tables, and interpretation guides are in [references/jd-quality-check.md](references/jd-quality-check.md). Summary:

| # | Check | What it flags |
|---|-------|---------------|
| 1 | Salary vs. Responsibility | Pay mismatch with implied seniority/duties |
| 2 | Red-Flag Keywords | Toxic culture or excessive workload signals (🔴 "抗压能力强", "996", etc.) |
| 3 | Concreteness Score (0–100) | How specific and measurable the JD requirements are |
| 4 | Generic/Specific Ratio | Ratio of vague soft-skill asks to concrete hard-skill requirements |
| 5 | PUA / Culture Indicators | Subtle red flags beyond obvious keywords ("薪资open", "期权激励"无细节) |
| 6 | Problem Diagnosis | Infer business problems behind each duty → map to candidate's experience |
| 7 | Role Scope Sanity Check | Detect "one person doing three people's jobs" (职责过载) |

After analysis, generate the summary table (template in reference) and produce a "综合可投性" verdict: **建议投递 / 慎投 / 需面试验证**.

### Phase 1: Extract

Parse both documents and extract structured information.

**From the Job Description, extract:**
- Job title and seniority level
- Required hard skills (technologies, tools, methodologies)
- Minimum years of experience
- Education requirements (degree, field, level)
- Certifications or licenses required
- Key responsibilities and duties
- Preferred/bonus qualifications
- Industry/domain knowledge requirements
- Keywords likely used by ATS (compile a keyword list)
- **JD quality signals** (already analyzed in Phase 0 — carry forward to report)

**From the Resume, extract:**
- Current/most recent job titles
- Total years of relevant experience
- Hard skills listed or demonstrated through experience
- Education (degree, field, institution)
- Certifications held
- Key achievements and responsibilities
- Industry/domain experience
- All keywords present in the resume

Record extracted data in a structured format for comparison. Refer to `references/analysis-guide.md` for detailed extraction criteria and category definitions.

### Phase 2: Compare and Score

Run a multi-dimensional comparison using five evaluation dimensions. Each dimension is scored 0–100 and weighted to produce an overall match score. **Note: Soft Skills & Culture Fit has been intentionally removed** — soft skills cannot be reliably assessed from a resume, and are better evaluated during interviews.

| Dimension | Weight | What it measures |
|-----------|--------|------------------|
| Hard Skills Match | 30% | Overlap between JD required skills and resume skills (direct + transferable) |
| Experience Match | 25% | Years, seniority level, and relevance of experience |
| Education & Certifications | 15% | Degree level, field relevance, required certifications |
| Keyword Coverage (ATS) | 15% | Percentage of JD keywords present in resume |
| Responsibilities Alignment | 15% | Overlap between JD duties and candidate's past responsibilities |

**Overall Match Score** = weighted sum of all dimension scores (0–100).

Refer to `references/scoring-framework.md` for detailed scoring rubrics, transferable-skill mapping rules, and edge-case handling.

### Phase 3: Analyze

Beyond the score, produce qualitative analysis:

1. **Matching Skills** — Skills the candidate has that directly match JD requirements. Group by category (technical, tools, domain).
2. **Transferable Skills** — Skills not explicitly required but demonstrably applicable to the role.
3. **Experience Gaps** — Areas where the candidate's experience falls short of requirements (years, scope, domain).
4. **Missing Qualifications** — Required or preferred qualifications the candidate lacks entirely.
5. **Keyword Coverage Analysis** — List of JD keywords found in the resume vs. missing. Flag high-priority missing keywords.
6. **Key Strengths** — Top 3–5 advantages the candidate brings to this role.
7. **Weaknesses** — Top 3–5 areas of concern a recruiter might flag.
8. **Overall Competitiveness Assessment** — A candid assessment of the candidate's position relative to likely competition (Strong / Moderate / Stretch / Unlikely).

### Phase 4: Recommend

Generate actionable, specific recommendations to improve the candidate's chances:

1. **Resume Tailoring** — Specific changes to make (keywords to add, achievements to reframe, sections to reorder).
2. **Skill Gap Mitigation** — How to address missing skills (courses, certifications, projects, framing transferable experience).
3. **Application Strategy** — Whether to apply directly, network first, or address gaps before applying.

**Do NOT include interview preparation advice here.** Interview preparation (with STAR answers, mock Q&A, follow-up predictions) is the exclusive domain of the `interview-coach` skill. The job-fit-analyzer's role is to identify gaps and strengths; the interview-coach's role is to turn those into interview tactics. This is a clean separation of concerns.

### Phase 5: Generate Report

Produce a self-contained HTML report using the template at `assets/report-template.html`. The report includes:

- **JD Quality Assessment** (from Phase 0) — MUST appear at the top, before the match score. Include: salary match, red-flag keyword scan with specific findings, concreteness score, generic/specific ratio (with "好词识别"), PUA detection, problem diagnosis with Problem→Resume mapping table, role scope sanity check, and an overall "可投性" verdict
- Header with job title, candidate name, and analysis date
- Overall match score with a visual gauge
- Dimension score breakdown (bar chart or progress bars) — 5 dimensions, NOT 6
- Matching skills summary
- Gaps and missing qualifications
- Keyword coverage table
- **MANDATORY: Detailed Dimension Scoring Breakdown** — For every dimension, include a collapsible `<details>` section that shows:
  - The exact calculation formula used
  - A table listing every sub-factor with individual scores and judgment rationale
  - For Experience dimension specifically: always show Years/Seniority/Relevance sub-scores AND all penalty deductions with specific amounts and reasons
  - A final weighted-summary table showing all 5 dimension scores × weights = total
  - The user must be able to trace every single point in the score back to its justification
- Strengths and weaknesses
- Actionable recommendations (Resume Tailoring, Skill Gap Mitigation, Application Strategy — do NOT include interview preparation, that belongs to interview-coach)
- Detailed appendix with full extraction data

Save the report to the current working directory as `job-fit-report.html` (or a user-specified filename) and present it to the user.

### Phase 6: Verify Report Completeness (Feedback Loop)

Before presenting the final result, verify the report against this checklist. If any item fails, fix it and re-verify.

```
Report Verification:
- [ ] JD Quality Assessment is at the top, before match score
- [ ] All 7 JD checks are present with specific findings (not generic)
- [ ] Problem Diagnosis table maps each duty → problem → candidate experience
- [ ] Overall score matches the weighted sum of 5 dimensions (recalculate)
- [ ] Every dimension has a collapsible <details> with formula + sub-scores
- [ ] Experience dimension shows Years/Seniority/Relevance sub-scores AND all penalties
- [ ] Keyword coverage table includes priority-weighted items
- [ ] Strengths and weaknesses are specific (not generic praise/criticism)
- [ ] Recommendations section has exactly 3 categories: Resume Tailoring, Skill Gap Mitigation, Application Strategy
- [ ] NO interview preparation content in recommendations (this belongs to interview-coach)
- [ ] All template placeholders ({{...}}) are replaced with real content
- [ ] Language matches the dominant language of JD/resume
```

If verification reveals issues:
1. Note each issue with the specific section reference
2. Fix the issue in the report
3. Re-run the relevant checklist item
4. Only proceed to Phase 7 when all items pass

### Phase 7: Bridge to Interview Preparation (MANDATORY for recommended applications)

After presenting the analysis report, **check the competitiveness assessment immediately**:

| Competitiveness | Score Range | Bridge Action |
|----------------|-------------|---------------|
| Strong Candidate | 80–100 | **MUST proactively suggest** mock interview prep with `interview-coach` skill. Say something like: "你的匹配度很高，建议趁热打铁做一次模拟面试，我可以针对 BOSS直聘 这个岗位生成个性化面试题和 STAR 回答框架。" |
| Competitive | 65–79 | **MUST proactively suggest** mock interview prep with `interview-coach` skill. Say something like: "你的匹配度不错，值得推进。要不要我用这个 JD 帮你做一次模拟面试？我可以针对你的薄弱点（如 [cite specific gaps]）生成专项训练。" |
| Viable but needs work | 50–64 | **Optionally suggest** interview prep, but focus more on skill gap remediation first. |
| Stretch / Unlikely | < 50 | Do NOT suggest interview prep. Focus on gap analysis and alternative roles. |

**When the user agrees to do mock interview prep**, immediately:
1. Load the `interview-coach` skill via the Skill tool
2. Pass the extracted JD data, resume data, identified strengths, gaps, and the competitiveness assessment
3. Follow the `interview-coach` skill workflow to generate personalized interview questions, STAR answers, and prep materials

This bridge is **not optional** — it is a mandatory step in the workflow for any analysis where the candidate is recommended to apply (score ≥ 65). Do not skip this transition; the whole point of fit analysis is to get the user interview-ready.

## Output Format

Always deliver:
1. A concise text summary in the conversation (match score, top 3 strengths, top 3 gaps, overall verdict)
2. The full HTML report file presented via `present_files`
3. For scores ≥ 65: **MUST follow up with Phase 7**, proactively offering interview preparation with the `interview-coach` skill

## Language

- If the job description and resume are in Chinese, generate the report in Chinese.
- If they are in English, generate the report in English.
- If mixed, match the dominant language of the job description.
- Score labels and dimension names should be localized accordingly.

## Important Notes

- Be honest and specific. Do not inflate scores to please the candidate. A false-positive "great match" is unhelpful.
- Distinguish between "required" and "preferred" qualifications in the JD. Missing a preferred qualification should not tank the score; missing a required one should significantly lower it.
- When the resume lacks explicit skill mentions but demonstrates the skill through achievements (e.g., "led a team of 10" implies leadership), credit it as demonstrated rather than listed.
- Transferable skills should be credited at reduced weight (typically 50–70% of a direct match) — note this in the analysis.
- If the JD or resume is too short or vague to analyze meaningfully, tell the user and ask for more detail rather than guessing.
- **MANDATORY Bridge to Interview Coach:** After completing the analysis for any candidate assessed as "Competitive" or "Strong" (score ≥ 65), you MUST proactively suggest mock interview preparation using the `interview-coach` skill. This is not optional — do not wait for the user to ask. Pass the extracted JD data, resume data, identified strengths, and gaps to the `interview-coach` skill when the user agrees. The fit analysis is incomplete without this handoff.
