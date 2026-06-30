---
name: job-fit-analyzer
description: "Analyze a job description and a candidate's resume to evaluate job compatibility. This skill should be used when a user wants to assess how well a resume matches a job posting, identify matching skills, experience gaps, missing qualifications, keyword coverage for ATS optimization, and overall competitiveness. It generates a structured assessment with a match score, key strengths, weaknesses, and actionable recommendations. Triggers include phrases like 'analyze this job', 'check my fit', 'am I qualified', 'resume match', 'job compatibility', 'tailor my resume', 'I'd like to find a new job', 'I want to find a job', 'I'm looking for a new job', 'help me find a job', 'job search', or when a user provides both a job description and a resume for evaluation. Also triggers when a user expresses general job-seeking intent without providing materials yet, or when they ask to analyze a job posting or resume in isolation."
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

1. **Job Description** — Full text of the job posting, including title, responsibilities, requirements, qualifications, and any stated preferences. May be provided as pasted text, a file path (PDF/DOCX/TXT/HTML), or a URL.
2. **Candidate Resume** — Full text of the resume, including summary, work experience, skills, education, certifications, and projects. May be provided as pasted text or a file path (PDF/DOCX/TXT/HTML).

**If the user expresses general job-seeking intent** (e.g., "I'd like to find a new job", "I want a job", "help me find a job") but has not provided either or both inputs, do not ask for both at once. Instead, enter the **Guided Conversation Flow** below to progressively gather context and materials.

## Guided Conversation Flow (for General Job-Seeking Expressions)

When the user says something broad like *"I'd like to find a new job"*, *"I want a job"*, *"help me find a job"*, or similar expressions without providing a job description or resume, do **not** immediately ask for both documents. Instead, guide the conversation naturally through these steps:

### Step 1: Acknowledge and Set Context
Start with a brief, warm acknowledgment (e.g., *"Happy to help you with your job search!"*) and immediately ask **one focused question**:

> "To give you the most useful help, could you tell me a bit about what kind of role you're looking for? For example, job title, industry, or anything specific you have in mind."

### Step 2: Gather the Target
After the user responds with their target role or interest:
- If they mention a specific job posting or company → ask them to share the job description (paste text, file, or URL).
- If they are unsure or exploring → ask for their resume first so you can help identify suitable roles based on their profile.

### Step 3: Gather the Resume
Ask for their resume in the same message or as a follow-up:
> "Great! Do you have a resume you'd like me to review? You can paste the text, upload a file, or share a link."

### Step 4: Once Both Are Available
Proceed to the **Workflow** (Phase 1–5 below) to perform the full job-fit analysis.

**Key principle:** Keep the conversation natural. Ask one or two questions at a time, not a checklist. Match the user's tone. The goal is to transition smoothly from a general intent to a concrete analysis.

## Workflow

### Phase 1: Extract

Parse both documents and extract structured information.

**From the Job Description, extract:**
- Job title and seniority level
- Required hard skills (technologies, tools, methodologies)
- Required soft skills
- Minimum years of experience
- Education requirements (degree, field, level)
- Certifications or licenses required
- Key responsibilities and duties
- Preferred/bonus qualifications
- Industry/domain knowledge requirements
- Keywords likely used by ATS (compile a keyword list)

**From the Resume, extract:**
- Current/most recent job titles
- Total years of relevant experience
- Hard skills listed or demonstrated through experience
- Soft skills demonstrated through achievements
- Education (degree, field, institution)
- Certifications held
- Key achievements and responsibilities
- Industry/domain experience
- All keywords present in the resume

Record extracted data in a structured format for comparison. Refer to `references/analysis-guide.md` for detailed extraction criteria and category definitions.

### Phase 2: Compare and Score

Run a multi-dimensional comparison using six evaluation dimensions. Each dimension is scored 0–100 and weighted to produce an overall match score.

| Dimension | Weight | What it measures |
|-----------|--------|------------------|
| Hard Skills Match | 25% | Overlap between JD required skills and resume skills (direct + transferable) |
| Experience Match | 20% | Years, seniority level, and relevance of experience |
| Education & Certifications | 15% | Degree level, field relevance, required certifications |
| Keyword Coverage (ATS) | 15% | Percentage of JD keywords present in resume |
| Responsibilities Alignment | 15% | Overlap between JD duties and candidate's past responsibilities |
| Soft Skills & Culture Fit | 10% | Alignment of soft skills and working style indicators |

**Overall Match Score** = weighted sum of all dimension scores (0–100).

Refer to `references/scoring-framework.md` for detailed scoring rubrics, transferable-skill mapping rules, and edge-case handling.

### Phase 3: Analyze

Beyond the score, produce qualitative analysis:

1. **Matching Skills** — Skills the candidate has that directly match JD requirements. Group by category (technical, tools, domain, soft skills).
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
3. **Interview Preparation** — Anticipated tough questions based on identified gaps; suggested talking points for strengths. For a comprehensive, personalized interview prep report with STAR answers, follow-up predictions, and role-specific tips, delegate to the `interview-coach` skill and pass the extracted JD/resume data along with the identified gaps.
4. **Application Strategy** — Whether to apply directly, network first, or address gaps before applying.

### Phase 5: Generate Report

Produce a self-contained HTML report using the template at `assets/report-template.html`. The report includes:

- Header with job title, candidate name, and analysis date
- Overall match score with a visual gauge
- Dimension score breakdown (bar chart or progress bars)
- Matching skills summary
- Gaps and missing qualifications
- Keyword coverage table
- Strengths and weaknesses
- Actionable recommendations
- Detailed appendix with full extraction data

Save the report to the current working directory as `job-fit-report.html` (or a user-specified filename) and present it to the user.

### Phase 6: Bridge to Interview Preparation (MANDATORY for recommended applications)

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
3. For scores ≥ 65: **MUST follow up with Phase 6**, proactively offering interview preparation with the `interview-coach` skill

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
