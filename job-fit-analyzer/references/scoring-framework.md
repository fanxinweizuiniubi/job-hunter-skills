# Scoring Framework

This document defines the exact scoring methodology used by the Job Fit Analyzer.

## Overall Score Calculation

Overall Score = (Hard Skills × 0.25) 
              + (Experience × 0.25) 
              + (Responsibilities Alignment × 0.20)
              + (Education & Certifications × 0.15)
              + (ATS Keyword Coverage × 0.15)

Score range: 0–100.

## Score Bands

Range | Label | Meaning
--- | --- | ---
85–100 | Excellent Fit | Outstanding match, strong competitive edge
70–84 | Good Fit | Solid candidate with minor addressable gaps
55–69 | Moderate Fit | Viable but has notable gaps
40–54 | Stretch Fit | Significant gaps, application is a stretch
0–39 | Poor Fit | Does not meet core requirements

## Dimension Scoring Rubrics

### 1. Hard Skills Match (25%)

Formula:
Score = [(Direct Matches × 1.0) + (Transferable Matches × 0.6)] / Total Required Skills × 100

- Direct Match: Clear evidence in experience descriptions or strong contextual use.
- Transferable Match: Closely related skill (60% credit).
- Skills only listed (no context): 80% credit.
- "Required or equivalent" → strong alternatives count as Direct.

### 2. Experience Match (25%)

Sub-weights:
- Relevant years: 35%
- Seniority level: 30%
- Domain / Role relevance: 35%

Years Scoring:
- Meets or exceeds → 100
- Within 1 year short → 80
- Within 2 years short → 60
- 3+ years short → 40 or lower

Seniority Levels:
Entry (0-2) → Junior (2-4) → Mid (4-7) → Senior (7-10) → Lead/Staff (10-15) → Principal+

### 3. Responsibilities Alignment (20%)

Extract 5–10 key responsibilities from the JD.  
For each, assess if candidate has performed similar duties:
- Directly / Near-exact → 100%
- Partially → 50%
- None → 0%

Dimension Score = Sum of credits / Total responsibilities × 100

### 4. Education & Certifications (15%)

- Education (60%): Degree level + field relevance
- Certifications (40%): Fulfillment rate of required vs preferred

Education Scoring:
- Meets or exceeds → 100
- One level below + strong experience → 70
- One level below without compensation → 50
- Does not meet → 25

### 5. ATS Keyword Coverage (15%)

Score = (Found Keywords / Total Significant Keywords) × 100

- Prioritize keywords from "Required" sections and high-frequency terms.
- Distinguish "demonstrated in experience" (strong) vs "listed only" (moderate).
- Flag keyword stuffing risk.

## Transferable Skill Mapping (Reference)

JD Skill | Strong Transferables | Credit Level
--- | --- | ---
Kubernetes | Docker Swarm, ECS, Mesos | High (80%)
AWS | Azure, GCP | High (80%)
React | Vue, Angular, Svelte | High (80%)
Python | Ruby, JS (scripting) | Medium (60%)
Tableau | Power BI, Looker, Qlik | High (80%)
Salesforce | HubSpot, Dynamics 365 | Medium (60%)

Unmapped cases: judge by conceptual similarity (50–70% credit).

## Penalty Modifiers (applied last)

Condition | Modifier
--- | ---
Missing central required hard skill | -5 ~ -10
Significantly overqualified (2+ levels) | -5 ~ -8
Heavy irrelevant experience padding | -3 ~ -6
Keyword stuffing (list but no proof) | Note risk
Noticeable resume quality issues | -2 ~ -5

Final score is clamped between 0–100.

**Note**: Soft skills are deliberately excluded from scoring. They are better evaluated in interviews.
