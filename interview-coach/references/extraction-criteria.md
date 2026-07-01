# Extraction Criteria for Interview Prep

## Purpose
Provide consistent, structured parsing rules for Job Description and Resume to feed all downstream phases (question generation, STAR answers, gap analysis).

## Job Description Extraction

### 1. Hard Skills
Categorize clearly:
- **Programming Languages & DSLs**
- **Frameworks & Libraries**
- **Infrastructure & Tools** (Cloud, CI/CD, Monitoring, etc.)
- **Methodologies & Practices** (Agile, TDD, Domain-Driven Design, etc.)
- **Domain Knowledge** (Finance, Healthcare, Advertising, etc.)

### 2. Soft Skills & Competencies
Map common JD phrases to competencies:
- Leadership, Ownership, Stakeholder Management, Communication, Collaboration, Prioritization, Adaptability, Conflict Resolution, Mentorship, etc.

### 3. Seniority & Scope
Determine level:
- **Junior**: Fundamentals + learning agility
- **Mid-level**: Independent delivery + problem solving
- **Senior**: System design + mentoring + cross-team impact
- **Staff+**: Architecture strategy + organizational influence + ambiguity handling

### 4. Culture & Context
Extract signals: pace, collaboration style, decision-making approach, values.

## Resume Extraction

### 1. Strong Achievement Bullets (STAR Fodder)
Prioritize bullets containing:
- Strong action verbs (led, designed, optimized, launched...)
- Quantifiable impact (%, $, users, time saved, revenue...)
- Scope & complexity indicators

### 2. Risk & Question Flags
- **Employment Gaps** (> 4 months)
- **Short Tenures** (< 12 months)
- **Career Transitions** (role/industry/tech/company type)
- **Seniority Mismatch**
- **Unexplained Overlaps or Missing Dates**

### 3. Skills Mapping
- Explicitly listed skills + demonstrated usage
- Transferable skills from adjacent experience

## Cross-Analysis Tension Points (Prioritized)

**High Priority (几乎必然被问):**
- JD-required skill missing or weak in resume
- Significant seniority gap
- Major domain or leadership experience gap
- Notable employment gaps during relevant periods

**Medium Priority:**
- Preferred (nice-to-have) skills missing
- Similar but not exact tool/framework experience
- Short or unclear tenures
- Overqualified signals

**Low Priority:**
- Minor certification/education gaps
- Easily learnable domain knowledge

## Output Format Recommendation

For each analysis, produce:
1. Structured summary of JD requirements
2. Structured resume profile
3. Ranked list of tension points with supporting evidence from both documents

**Next Step:** Use this analysis directly to generate personalized questions and identify preparation gaps.