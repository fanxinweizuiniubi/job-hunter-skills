# Analysis Guide

This document provides detailed guidance for extracting, categorizing, and analyzing information from job descriptions and resumes.

## Part 1: Job Description Extraction

### Key Sections to Identify

Most job descriptions contain some or all of these sections. Extract from each:

| Section | What to Extract |
|---------|----------------|
| Job Title / Header | Title, department, location, employment type, seniority |
| Company Overview | Industry, company size, stage (startup/enterprise), culture indicators |
| Role Summary | High-level purpose of the role, reporting structure |
| Responsibilities / Duties | Day-to-day tasks, strategic responsibilities, team management |
| Required Qualifications | Must-have skills, experience, education, certifications |
| Preferred Qualifications | Nice-to-have skills and experience |
| Benefits / Compensation | Salary range, benefits (informational, not scored) |

### Extraction Categories

#### Hard Skills
Extract all explicitly mentioned:
- **Programming languages:** Python, Java, JavaScript, Go, Rust, C++, etc.
- **Frameworks/libraries:** React, Spring, Django, TensorFlow, PyTorch, etc.
- **Tools/platforms:** AWS, Docker, Kubernetes, Jira, Git, Tableau, Salesforce, etc.
- **Methodologies:** Agile, Scrum, DevOps, CI/CD, TDD, etc.
- **Domain knowledge:** FinTech, healthcare compliance, e-commerce, B2B SaaS, etc.
- **Data/analytical:** SQL, statistical modeling, A/B testing, data visualization, etc.

Mark each as **Required** or **Preferred** based on which section it appears in.

#### Soft Skills (DEPRECATED — no longer extracted or scored)

Do NOT extract soft skills from JD or resume. Soft skills cannot be reliably assessed from a resume — they are evaluated during interviews. The JD analysis (Phase 0) will flag red-flag keywords like "抗压" "吃苦耐劳" as culture signals, but these are NOT scored in the match calculation.

#### Experience Requirements
- **Years:** Extract specific numbers ("5+ years," "3-5 years")
- **Type:** What kind of experience (e.g., "experience in building scalable web applications")
- **Scale indicators:** "experience managing teams of 10+," "experience with millions of users"
- **Industry:** Specific industry experience requirements

#### Education Requirements
- **Degree level:** Bachelor's, Master's, PhD, or "degree or equivalent"
- **Field:** Specific field (e.g., "Computer Science or related field")
- **Equivalency clauses:** "or equivalent experience" — note this as it relaxes the requirement

#### Certifications
- Required: PMP, CPA, AWS Certified, CFA, etc.
- Preferred: Any listed under preferred qualifications

#### ATS Keywords
Compile a comprehensive keyword list for ATS matching:
- All hard skills (both required and preferred)
- Industry terms and jargon
- Methodology names
- Tool names (including abbreviations)
- Key action verbs from responsibilities
- Qualification phrases ("project management," "stakeholder communication")

### Handling Vague Job Descriptions

If the JD is short or vague:
- Infer requirements from the job title and industry norms
- Note assumptions made in the report
- Reduce confidence in the overall score
- Suggest the user provide a more detailed JD if available

---

## Part 2: Resume Extraction

### Key Sections to Identify

| Section | What to Extract |
|---------|----------------|
| Header / Contact | Name, location, LinkedIn, portfolio |
| Summary / Objective | Candidate's self-described positioning |
| Work Experience | Job titles, companies, dates, responsibilities, achievements |
| Skills | Listed skills (technical, tools, languages, soft) |
| Education | Degrees, institutions, graduation dates, relevant coursework |
| Certifications | Professional certifications and licenses |
| Projects | Personal/academic projects demonstrating skills |
| Volunteer / Leadership | Additional experience demonstrating soft skills |

### Extraction Categories

#### Work Experience
For each role, extract:
- **Job title** (map to standardized seniority level)
- **Company** and industry
- **Duration** (calculate years/months)
- **Key responsibilities** (what they did day-to-day)
- **Achievements** (quantified outcomes are gold: "increased revenue by 30%," "managed team of 12")
- **Technologies/tools used** (mentioned in context of the role)
- **Scope indicators** (team size, budget, user base, revenue impact)

**Total relevant experience calculation:**
- Sum durations of roles relevant to the target position
- Do not count unrelated experience (e.g., retail job from 10 years ago when applying for software engineering)
- If career change, count transferable experience at reduced weight

#### Skills
- **Listed skills:** Extract from dedicated skills section
- **Demonstrated skills:** Extract from experience descriptions (more valuable evidence)
- **Classify:** Hard skills, tools, soft skills, languages, domain knowledge
- Note skills that appear in both list and experience (strongest evidence)

#### Education
- Degree level and field
- Institution (note prestige if relevant)
- Graduation year (for recency assessment)
- Relevant coursework or academic projects (for recent graduates)
- GPA (if provided and relevant)

#### Certifications
- Certification name
- Issuing organization
- Date (check if current/expired)
- Relevance to the JD

#### Achievements (High-Value Signal)
Prioritize quantified achievements:
- "Increased X by Y%"
- "Reduced costs by $Z"
- "Managed team of N people"
- "Launched product serving M users"
- "Improved process efficiency by P%"

These demonstrate skills more powerfully than a skills list entry.

### Inferring Skills from Context

When a skill is not explicitly listed but can be reasonably inferred from experience:

| Experience Description | Inferred Skill |
|----------------------|----------------|
| "Led weekly team meetings and presented to leadership" | Communication, leadership |
| "Managed project timeline across 3 teams" | Project management, cross-functional collaboration |
| "Optimized database queries reducing latency by 40%" | Performance optimization, SQL/database |
| "Built automated testing pipeline" | CI/CD, testing, automation |
| "Handled customer escalations and resolved within SLA" | Customer service, problem-solving, stress tolerance |
| "Mentored 5 junior developers" | Mentorship, leadership |
| "Drove migration from monolith to microservices" | Architecture, system design |

Credit inferred skills at 80% weight (strong but not explicitly stated).

---

## Part 3: Comparison and Analysis

### Matching Skills Analysis

**Direct Match identification:**
1. For each required hard skill in JD, search resume for:
   - Exact term match in skills section
   - Exact term match in experience descriptions
   - Synonym match (e.g., "JS" = "JavaScript")
2. Classify as: Demonstrated (in experience), Listed (in skills section only), or Missing

**Transferable Match identification:**
1. For each missing required skill, assess if candidate has related experience
2. Use transferable skill mapping table in `scoring-framework.md`
3. Apply judgment for unlisted pairs based on conceptual similarity
4. Note the reasoning for each transferable match

### Gap Analysis

**Experience Gaps:**
- Calculate years gap (candidate years vs. required years)
- Identify scope gaps (e.g., JD requires managing 20+ person team, candidate managed 5)
- Identify domain gaps (e.g., JD requires FinTech experience, candidate has only e-commerce)
- Identify recency gaps (skill used 8 years ago but not since)

**Qualification Gaps:**
- Missing required degree (note if "or equivalent experience" clause exists)
- Missing required certifications
- Missing specific tool/platform experience

### Keyword Coverage Analysis

1. Build keyword list from JD (as described in Part 1)
2. For each keyword, search resume:
   - **Found in experience:** Strongest signal (green)
   - **Found in skills section:** Moderate signal (yellow)
   - **Not found:** Gap (red)
3. Calculate coverage percentage
4. Identify high-priority missing keywords (those in "Required" section or mentioned multiple times)
5. Flag keyword stuffing risk (many keywords in skills section but few in experience)

### Strengths and Weaknesses Identification

**Strengths** (select top 3–5):
- Skills that exceed JD requirements
- Highly relevant achievements with quantified impact
- Unique differentiators (rare skills, prestigious experience, domain expertise)
- Strong keyword coverage in critical areas
- Perfect or near-perfect dimension scores

**Weaknesses** (select top 3–5):
- Missing required skills or qualifications
- Experience gaps (years, scope, domain)
- Low keyword coverage in critical areas
- Career trajectory concerns (frequent job changes, employment gaps, downward trajectory)
- Resume quality issues (vague descriptions, lack of quantification, formatting)

### Competitiveness Assessment

Based on the overall score and qualitative analysis, assign one of:

| Assessment | Criteria |
|-----------|----------|
| **Strong Candidate** | Score 80+, no critical gaps, multiple differentiating strengths |
| **Competitive** | Score 65–79, minor gaps, solid matching skills, some differentiators |
| **Viable but needs work** | Score 50–64, notable gaps but core requirements met, needs resume tailoring |
| **Stretch** | Score 35–49, significant gaps, missing multiple core requirements |
| **Unlikely** | Score below 35, does not meet core requirements |

### Recommendation Generation

Generate recommendations in three categories:

#### 1. Resume Tailoring
- Specific keywords to add (from gap analysis)
- Achievements to reframe or highlight (align with JD responsibilities)
- Sections to add, remove, or reorder
- Skills to feature more prominently
- Summary/objective to customize for this role

#### 2. Skill Gap Mitigation
- Courses or certifications to pursue (name specific ones if possible)
- Projects to build that demonstrate missing skills
- Ways to frame transferable experience to cover gaps
- Timeline estimates for gap closure

#### 3. Application Strategy
- Apply directly / Network first / Build skills first / Consider a different role
- If stretching: suggest reaching out to recruiter with a tailored message
- If strong: suggest applying with confidence and preparing for advancement discussions
- Referral opportunities to explore (if company/industry is identifiable)
