---
name: job-fit-analyzer
description: "Evaluates job compatibility by comparing a job description against a candidate's resume across five dimensions: hard skills, experience, education/certifications, ATS keyword coverage, and responsibilities alignment. Generates a scored HTML report with strengths, gaps, and recommendations. Also pre-screens JD quality for red flags (toxic culture indicators, vague requirements, salary mismatch). Use when the user provides a JD and resume, asks about job fit or qualifications, wants to tailor their resume, or expresses general job-seeking intent (e.g. 'analyze this job', 'check if I am qualified', 'help me find a job')."
---

# Job Fit Analyzer

## Purpose

Evaluate compatibility between a job description and a candidate resume. Produce a candid match score, dimension-level evidence, JD quality assessment, strengths, gaps, and application recommendations in a self-contained HTML report.

## When to Use

- A user provides or asks to provide a job description and resume for compatibility analysis.
- A user asks whether they are qualified for a role.
- A user wants to tailor a resume for a specific job.
- A user asks about gaps between their profile and a job's requirements.
- A user wants ATS keyword coverage analysis.
- A user expresses general job-seeking intent without materials yet.
- A user asks for job search strategy or role-fit direction based on their profile.

## Inputs

Require both inputs for a full analysis:

1. Job description
2. Candidate resume

Accept text, files, or URLs. If either input is missing, ask for only the next useful item instead of sending a long checklist.

If the user expresses general job-seeking intent without a target role or materials, use the guided conversation below before starting the workflow.

## Guided Conversation

Ask one or two focused questions at a time.

1. Acknowledge the goal and ask what role, industry, company type, or direction they are targeting.
2. If they mention a specific posting, ask for the job description.
3. If they are still exploring, ask for the resume first so you can identify plausible target roles.
4. Once both JD and resume are available, run the workflow.

Keep the tone natural and match the user's language.

## Resource Map

Load references only when the corresponding phase needs them:

- `references/jd-quality-check.md`: JD quality pre-screen, red flags, problem diagnosis, and role scope sanity checks.
- `references/analysis-guide.md`: JD/resume extraction, qualitative comparison, gap analysis, and recommendation generation.
- `references/scoring-framework.md`: five-dimension scoring model, weights, penalties, score bands, and edge cases.
- `references/report-checklist.md`: report completeness and verification checklist.
- `references/interview-transition.md`: handoff rules for `interview-coach`.
- `assets/report-template.html`: HTML report structure and placeholders.

## Workflow

Use this progress checklist while working:

```text
Job Fit Analysis Progress:
- [ ] Phase 0: JD quality pre-screen
- [ ] Phase 1: Extract structured JD and resume data
- [ ] Phase 2: Score all five dimensions
- [ ] Phase 3: Analyze strengths, gaps, keywords, and competitiveness
- [ ] Phase 4: Generate recommendations
- [ ] Phase 5: Build the HTML report
- [ ] Phase 6: Verify and fix the report
- [ ] Phase 7: Offer interview preparation when appropriate
```

### Phase 0: JD Quality Pre-Screen

Before scoring candidate fit, analyze the JD using `references/jd-quality-check.md`.

Produce a JD Quality Assessment for the report, including the seven required checks and an overall application verdict: `建议投递`, `慎投`, or `需面试验证` for Chinese reports, or equivalent labels for English reports.

### Phase 1: Extract

Extract structured information from the JD and resume using `references/analysis-guide.md`.

If the JD or resume is too short or vague to support meaningful analysis, ask for more detail instead of guessing.

### Phase 2: Compare and Score

Score the candidate using `references/scoring-framework.md`.

Return the overall score, all five dimension scores, evidence, reasoning, and any penalties. Make every score traceable to extracted evidence.

### Phase 3: Analyze

Use `references/analysis-guide.md` to produce:

- matching and transferable skills
- experience and qualification gaps
- ATS keyword coverage
- top strengths and weaknesses
- overall competitiveness assessment

Be honest. Do not inflate scores to make the candidate feel better.

### Phase 4: Recommend

Generate exactly three recommendation categories:

- Resume Tailoring
- Skill Gap Mitigation
- Application Strategy

Do not include interview-preparation content here; that belongs to `interview-coach`.

### Phase 5: Generate Report

Use `assets/report-template.html` to create a self-contained HTML report. Save it as `job-fit-report.html` unless the user requested another filename.

Include the JD Quality Assessment before the match score. Replace every template placeholder with real content.

### Phase 6: Verify

Verify the report against `references/report-checklist.md`. If any item fails, fix the report and re-check before presenting it.

### Phase 7: Interview Preparation Bridge

After presenting the analysis, apply `references/interview-transition.md`.

For candidates assessed as Competitive or Strong, or with score `>= 65`, proactively offer to continue with `interview-coach`. If the user agrees, pass the extracted JD data, resume data, strengths, gaps, and competitiveness assessment to that skill.

## Output

Always deliver:

1. A concise conversation summary with match score, top strengths, top gaps, and verdict.
2. The full HTML report file.
3. The interview-preparation offer when the transition rules require it.

## Language

- If the JD and resume are Chinese, generate the report in Chinese.
- If they are English, generate the report in English.
- If mixed, match the dominant language of the JD.
- Localize score labels, dimension names, and verdicts.
