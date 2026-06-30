# Scoring Framework

This document defines the detailed scoring methodology for the Job Fit Analyzer skill.

## Overall Score Calculation

The overall match score is a weighted average of six dimension scores:

```
Overall Score = (HardSkills × 0.25) + (Experience × 0.20) + (EducationCerts × 0.15)
              + (KeywordCoverage × 0.15) + (Responsibilities × 0.15) + (SoftSkills × 0.10)
```

Score range: 0–100.

## Score Bands

| Range | Label | Meaning |
|-------|-------|---------|
| 85–100 | Excellent Fit | Candidate meets or exceeds nearly all requirements; strong competitive position |
| 70–84 | Good Fit | Candidate meets most core requirements; minor gaps that can be addressed |
| 55–69 | Moderate Fit | Candidate meets some requirements; notable gaps exist; may still be viable |
| 40–54 | Stretch Fit | Candidate meets few requirements; significant gaps; application is a stretch |
| 0–39 | Poor Fit | Candidate does not meet core requirements; recommend skill-building before applying |

## Dimension Scoring Rubrics

### 1. Hard Skills Match (Weight: 25%)

Measures the overlap between skills required by the JD and skills the candidate possesses.

**Scoring procedure:**
1. List all required hard skills from the JD (technologies, tools, programming languages, methodologies, domain knowledge).
2. Classify each as: Direct Match, Transferable Match, or Missing.
3. Calculate:

```
Dimension Score = ((DirectMatches × 1.0) + (TransferableMatches × 0.6)) / TotalRequiredSkills × 100
```

**Direct Match criteria:**
- Skill name appears in resume (exact or close synonym)
- Skill is demonstrated through work experience entries (not just listed)
- e.g., JD requires "Python" and resume shows "Developed data pipeline in Python"

**Transferable Match criteria:**
- Candidate has a closely related skill that could reasonably substitute
- e.g., JD requires "Kubernetes" but candidate has deep "Docker Swarm" experience
- e.g., JD requires "Salesforce" but candidate has extensive "HubSpot" experience
- Transferable matches are credited at 60% weight

**Missing:**
- No direct or transferable evidence in resume
- Required skills that are missing carry full negative weight

**Edge cases:**
- If JD lists "required or equivalent" — treat alternatives as direct matches
- If a skill appears only in a "skills" list with no contextual evidence, credit at 80% (listed but not demonstrated)
- If the JD has fewer than 3 required hard skills, broaden the scope to include preferred skills in the denominator

### 2. Experience Match (Weight: 20%)

Measures whether the candidate's experience level and relevance meet the JD's requirements.

**Sub-factors:**
- **Years of experience (40% of dimension):**
  - Meets or exceeds required years → 100
  - Within 1 year below → 80
  - Within 2 years below → 60
  - Within 3 years below → 40
  - More than 3 years below → 20

- **Seniority level (30% of dimension):**
  - Matches or exceeds → 100
  - One level below (e.g., JD wants Senior, candidate is Mid) → 70
  - Two levels below → 40
  - One level above (overqualified) → 85 (slight penalty for potential flight risk)

- **Relevance of experience (30% of dimension):**
  - Same industry/role → 100
  - Related industry/role → 75
  - Different industry but transferable role → 50
  - Largely unrelated → 25

```
Dimension Score = (YearsScore × 0.4) + (SeniorityScore × 0.3) + (RelevanceScore × 0.3)
```

**Seniority levels (standardized):**
- Entry-level (0–2 years)
- Junior (2–4 years)
- Mid-level (4–7 years)
- Senior (7–10 years)
- Lead/Staff (10–15 years)
- Principal/Director (15+ years)

### 3. Education & Certifications (Weight: 15%)

**Scoring procedure:**

*Education (60% of dimension):*
- Meets or exceeds degree requirement → 100
- One level below but strong experience compensates → 70
- One level below without compensating experience → 50
- Does not meet requirement → 25

*Degree levels:*
- High School / equivalent
- Associate's / Diploma
- Bachelor's
- Master's
- PhD / Doctorate

*Field relevance:*
- Exact field match → 100% credit
- Related field → 80% credit
- Unrelated field but degree level met → 60% credit

*Certifications (40% of dimension):*
- All required certifications present → 100
- Most present (≥75%) → 80
- Some present (50–74%) → 60
- Few present (25–49%) → 35
- None present but certifications are "preferred" not "required" → 70
- None present and certifications are required → 20

```
Dimension Score = (EducationScore × 0.6) + (CertScore × 0.4)
```

### 4. Keyword Coverage / ATS Optimization (Weight: 15%)

Measures how well the resume's keywords align with the JD for Applicant Tracking System (ATS) filtering.

**Scoring procedure:**
1. Extract all significant keywords and phrases from the JD:
   - Technical terms and tool names
   - Methodology names (Agile, Scrum, DevOps, etc.)
   - Industry-specific terminology
   - Action verbs tied to responsibilities
   - Qualification phrases
2. Search for each keyword in the resume (exact match or close variant)
3. Calculate:

```
Dimension Score = KeywordsFoundInResume / TotalKeywordsFromJD × 100
```

**Keyword extraction rules:**
- Ignore common stop words (the, and, with, etc.)
- Include multi-word phrases (e.g., "project management," "machine learning")
- Include abbreviated and full forms (e.g., "ML" and "Machine Learning" count as one keyword if both appear)
- Weight priority keywords (those mentioned multiple times or in requirements section) at 1.5× in the numerator

**Quality check:**
- If keyword density is high but in a "skills dump" section with no context, note this as a risk (ATS may pass but human reviewers may discount)
- Flag keywords that appear only in the skills section vs. those demonstrated in experience entries

### 5. Responsibilities Alignment (Weight: 15%)

Measures overlap between the JD's listed responsibilities and the candidate's past role responsibilities.

**Scoring procedure:**
1. Extract 5–10 key responsibilities from the JD
2. For each, determine if the candidate has performed similar duties:
   - Directly performed (exact or near-exact match) → full credit
   - Partially performed (some aspects match) → 50% credit
   - Not performed → 0
3. Calculate:

```
Dimension Score = SumOfCredits / TotalResponsibilities × 100
```

**Matching guidance:**
- Look beyond job titles; focus on described duties and achievements
- "Led a team of 15 engineers" matches "manage and grow engineering team"
- "Built CI/CD pipeline from scratch" matches "establish DevOps practices"
- Context matters: a responsibility performed 5+ years ago is still valid but note recency

### 6. Soft Skills & Culture Fit (Weight: 10%)

Measures alignment between soft skills sought in the JD and those demonstrated in the resume.

**Scoring procedure:**
1. Extract implied/explicit soft skills from JD:
   - Explicit: "excellent communication skills," "strong leadership"
   - Implicit: "cross-functional collaboration" → collaboration; "fast-paced environment" → adaptability
2. Match against evidence in resume:
   - Achievement descriptions that demonstrate the soft skill → full credit
   - Soft skill listed in a skills section → 60% credit (claimed but not demonstrated)
   - No evidence → 0
3. Calculate:

```
Dimension Score = SumOfCredits / TotalSoftSkills × 100
```

**Common soft skill categories:**
- Leadership / management
- Communication (written, verbal, presentation)
- Collaboration / teamwork
- Problem-solving / analytical thinking
- Adaptability / learning agility
- Initiative / proactivity
- Project / time management
- Mentorship / coaching
- Stakeholder management
- Customer focus

## Transferable Skill Mapping Reference

Use these common mappings when assessing transferable matches:

| JD Skill | Transferable From | Confidence |
|----------|-------------------|------------|
| Kubernetes | Docker Swarm, Mesos, ECS | High |
| AWS | Azure, GCP | Medium-High |
| React | Vue, Angular, Svelte | High |
| Python | Ruby, JavaScript (for scripting) | Medium |
| Salesforce | HubSpot, Zoho, Dynamics 365 | Medium |
| Tableau | Power BI, Looker, Qlik | High |
| Jira | Asana, Monday, Trello | Medium |
| Scrum/Agile | Kanban, SAFe | High |
| Google Analytics | Adobe Analytics, Mixpanel | Medium-High |
| Kubernetes | Docker + CI/CD experience | Medium |

When encountering a pair not listed here, apply judgment: if the transferable skill involves similar concepts, workflows, or problem domains, credit at 50–70%.

## Penalty Modifiers

Apply these modifiers to the overall score after dimension calculation:

| Condition | Modifier |
|-----------|----------|
| Missing a "required" hard skill that is central to the role | −5 to −10 per skill |
| Resume has significant irrelevant experience padding | −3 to −5 |
| Candidate is significantly overqualified (2+ levels above) | −5 to −8 |
| Resume has typos, formatting issues, or inconsistencies (noted during extraction) | −2 to −5 |
| Keyword stuffing detected (skills listed but zero contextual evidence) | ATS score unaffected, but note as risk |

Final score is clamped to 0–100 after applying modifiers.

## Tied/Edge Cases

- **Career changers:** Weight transferable skills and responsibilities alignment more heavily. Reduce penalty for missing domain-specific skills if the core competencies transfer.
- **Recent graduates:** If the JD is entry-level, weight education and internships/projects more heavily. Do not penalize lack of full-time experience if internships demonstrate relevant skills.
- **Boomerang candidates:** If the candidate previously worked at the same company (detectable from resume), note this as a positive culture-fit signal.
- **Vague JDs:** If the JD lacks specific requirements, note this in the report and base scoring on available information with reduced confidence.
