# Analysis Guide

Guidance for Phase 1 (Extraction), Phase 2 (Scoring), and Phase 3 (Analysis).

## Part 1: Extraction Rules

### Job Description Extraction
Extract and categorize the following:

- **Job Title & Metadata**: title, level, location, type, reporting line
- **Responsibilities**: day-to-day duties and strategic goals (distinguish clearly)
- **Hard Skills**: programming languages, frameworks, tools, platforms, methodologies, domain knowledge. Mark as **Required** or **Preferred**
- **Experience Requirements**: years, type, scale (team size, user base, revenue), industry
- **Education & Certifications**: degree, field, certifications (required vs preferred)
- **ATS Keyword List**: compile comprehensive list from all technical terms, tools, action verbs, and jargon

**Important**: Do NOT extract or score soft skills from JD. Handle culture signals only in Phase 0 JD Quality Check.

### Resume Extraction
For each relevant role, extract:
- Job title, company, dates, industry
- Responsibilities + quantified achievements (prioritize numbers)
- Technologies and tools used in context
- Scope (team size, budget, impact)

**Skills**:
- Listed skills + demonstrated skills from experience descriptions
- Prioritize demonstrated skills over listed ones

**Other**:
- Education, certifications (with dates and relevance)
- Total relevant experience (only count roles aligned with target JD)

If JD or resume is vague/short, note assumptions and lower confidence.

## Part 2: Comparison Rules

### Hard Skill Matching
- **Direct Match**: exact or synonym match in skills section or experience
- **Transferable Match**: use mapping from `scoring-framework.md`
- **Missing**: no evidence

### Gap Analysis
- Experience gaps (years, scope, domain, recency)
- Qualification gaps (degree, certifications, key tools)
- Keyword coverage % (especially Required items)

### Strengths & Weaknesses
Select top 3-5 each:
- **Strengths**: exceeding requirements, strong quantified achievements, unique differentiators
- **Weaknesses**: critical missing skills, large experience gaps, low keyword coverage

### Competitiveness Levels
- **Strong** (80+): no critical gaps, clear differentiators
- **Competitive** (65-79): minor gaps, solid match
- **Viable** (50-64): notable gaps, needs tailoring
- **Stretch** (35-49): significant gaps
- **Unlikely** (<35): fails core requirements

## Part 3: Output Guidelines

- Always be candid. Do not sugarcoat major gaps.
- In report, provide clear evidence for every score and conclusion.
- For recommendations, focus only on:
  1. Resume Tailoring (keywords, reframing, structure)
  2. Skill Gap Mitigation (specific actions)
  3. Application Strategy

**Do not** generate detailed interview scripts here — that belongs to interview-coach skill.

Keep all analysis traceable to extracted evidence from JD and resume.