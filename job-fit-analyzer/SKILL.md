---
name: job-fit-analyzer
description: Evaluates job compatibility by comparing a job description against a candidate's resume across five dimensions — hard skills depth, past achievements & business impact, role scope/complexity/seniority match, domain/scenario relevance, and learning ability & potential (12%). Also pre-screens JD quality for red flags. Use when the user provides a JD and resume, asks about job fit or qualifications, wants to tailor their resume, or expresses general job-seeking intent. (e.g. 'analyze this job', 'check if I am qualified', 'help me find a job').
metadata:
  type: workflow
  version: "1.0"
  domain: career
---

# Job Fit Analyzer

## Purpose

Evaluate compatibility between a job description and a candidate resume. Produce a candid match score, dimension-level evidence, JD quality assessment, strengths, gaps, and actionable recommendations in a self-contained HTML report.

## When to Use

- User provides both JD and resume (text, file, or URL)
- User asks if they are qualified for a role
- User wants resume tailoring for a specific job
- User asks for gaps analysis or ATS optimization
- General job-seeking support (use guided conversation)

## Inputs

Require both inputs for a full analysis:

1. Job description
2. Candidate resume

If either is missing, ask for the missing piece only.

## Guided Conversation

Ask one or two focused questions at a time.

1. Clarify target role/industry if not provided.
2. Ask for JD if they mention a specific posting.
3. Ask for resume if they are still exploring.
4. Once both are available, proceed to analysis.

## Resource Map

Load references only when the corresponding phase needs them:

- `references/jd-quality-check.md` — JD quality pre-screen and red flags
- `references/analysis-guide.md` — Extraction, comparison, gap analysis
- `references/scoring-framework.md` — Five-dimension scoring rules and weights
- `references/report-checklist.md` — Final report verification
- `references/interview-transition.md` — Handoff rules to `interview-coach`
- `assets/report-template.html` — HTML report template

## Workflow

Follow this checklist:

- [ ] Phase 0: JD quality pre-screen (using jd-quality-check.md)
- [ ] Phase 1: Extract structured data from JD and resume (using analysis-guide.md)
- [ ] Phase 2: Score five dimensions (using scoring-framework.md)
- [ ] Phase 3: Analyze strengths, gaps, ATS keywords, competitiveness
- [ ] Phase 4: Generate three recommendation categories
- [ ] Phase 5: Build HTML report from template
- [ ] Phase 6: Verify report against checklist
- [ ] Phase 7: Offer interview preparation if score >= 65 or "Competitive/Strong"

## Core Instructions

1. Always start with **Phase 0** JD quality assessment before candidate scoring.
2. Be honest and candid — do not inflate scores.
3. Generate report in the dominant language of the JD (Chinese or English).
4. Save the final report as `job-fit-report.html`.
5. After presenting the report, follow interview-transition rules to offer next steps when appropriate.

For detailed guidance on any phase, read the corresponding reference file.