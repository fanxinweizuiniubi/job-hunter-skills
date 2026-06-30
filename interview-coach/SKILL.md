name: interview-coach
description: "Provide comprehensive, personalized interview preparation for job candidates. Generate tailored interview questions based on a target job description and candidate resume, suggest high-quality answers using the STAR framework where appropriate, identify likely follow-up questions, highlight areas requiring additional preparation, and provide practical interview tips tailored to the target role. Use when the user mentions 'interview prep', 'prepare for interview', 'mock interview', 'interview questions', '面试准备', '面试辅导', '模拟面试', or when the job-hunter or job-fit-analyzer skills reach the interview preparation phase."
agent_created: true
---

# Interview Coach

## Purpose

Provide comprehensive, personalized interview preparation for job candidates based on their resume and target job description. Generate tailored interview questions, craft high-quality STAR-framework answers, predict follow-up questions, flag weak spots, and deliver role-specific interview tactics.

## When to Use

- User explicitly asks for interview preparation help (e.g., "帮我准备面试", "prepare for my interview", "interview coaching")
- User mentions an upcoming interview and provides or is willing to provide a job description and resume
- The `job-hunter` skill reaches Phase 3 (Interview Preparation)
- The `job-fit-analyzer` skill reaches Phase 4 (Recommendations) and the user wants interview prep
- User asks for mock interview practice
- User wants to know what questions they might be asked for a specific role

## Inputs

**Required:**
1. **Target Job Description (JD)** — Full text of the job posting, including title, responsibilities, requirements, and qualifications. May be provided as pasted text, a file path, or a URL.
2. **Candidate Resume** — Full text of the resume, including work experience, projects, skills, and education. May be provided as pasted text or a file path.

**Optional (but improves quality):**
3. **Interview Stage** — Which round is this? (HR screen / Technical round 1 / Technical round 2 / Manager / Director / Final)
4. **Interview Format** — Video / In-person / Phone / Panel / Take-home assignment
5. **Company Name** — For company-specific question generation

**If the user has not provided both JD and resume**, do not proceed with question generation. Instead, ask them to share both materials first. If they already went through `job-fit-analyzer`, reuse the extracted JD and resume data.

## Workflow

### Phase 1: Extract and Analyze

Parse both documents and build a structured understanding. Refer to `references/extraction-criteria.md` for detailed extraction logic.

**From the Job Description, extract:**
- Job title, seniority level, and reporting structure
- Required hard skills (technologies, tools, methodologies, languages)
- Required soft skills and leadership expectations
- Key responsibilities and ownership areas
- Industry/domain knowledge requirements
- Company culture indicators (from tone, values, mission statements)
- Preferred/bonus qualifications

**From the Resume, extract:**
- Current/most recent role and responsibilities
- Key achievements with quantifiable results (these become STAR answer fodder)
- Technical skills and proficiency levels
- Projects with scope, outcomes, and technologies used
- Career trajectory and transitions (flag potential "why did you...?" questions)
- Gaps or short tenures (flag likely probing questions)
- Education and certifications

**Cross-Analysis — Identify tension points (likely interview focus areas):**
- Skills listed in JD but not prominently in resume → anticipate "How do you handle X?" questions
- Career gaps or short job stints → anticipate "Tell me about this period" questions
- Major role transitions → anticipate "Why this change?" questions
- Junior applying for senior role → anticipate leadership/scope questions
- Overqualified candidate → anticipate "Why this role?" questions
- Missing required qualifications → anticipate "How would you learn X?" questions

### Phase 2: Generate Personalized Interview Questions

Generate a comprehensive question bank organized by category. Each question should be personalized based on the JD-resume cross-analysis. Refer to `references/question-bank-guide.md` for question taxonomy and generation patterns.

**Categories to cover:**

1. **Role-Specific Technical Questions** (5-10 questions)
   - Based on the core skills required in the JD
   - Calibrated to the seniority level
   - Include both theoretical and practical/scenario-based questions
   - For each, note whether it is a "must-know" or "nice-to-know"

2. **Behavioral Questions** (8-12 questions)
   - Tailored to the soft skills and culture indicators from the JD
   - Prioritize questions that probe areas where the resume shows limited evidence
   - Use common frameworks: leadership, conflict resolution, failure, teamwork, prioritization, stakeholder management
   - For each, suggest the most relevant experience from the resume to use as the STAR story

3. **Resume Deep-Dive Questions** (5-8 questions)
   - Questions an interviewer would naturally ask after reading the resume
   - Focus on: biggest achievements, career transitions, gaps, technologies used, team size, project scope
   - Flag any part of the resume that is likely to attract skepticism or curiosity

4. **Situational / Case Questions** (3-5 questions)
   - Hypothetical scenarios based on the JD responsibilities
   - "How would you handle X?" questions
   - Calibrated to the role's scope and seniority

5. **Company-Specific Questions** (3-5 questions)
   - Based on the company's stated mission, values, products, or recent news
   - "Why do you want to join us?" type questions
   - Research the company if possible (web search)

6. **Candidate Questions to Ask the Interviewer** (5-8 questions)
   - Smart questions the candidate should prepare to ask
   - Categorized by: role expectations, team dynamics, growth, company strategy, culture

### Phase 3: Craft STAR-Framework Answers

For every **behavioral question** generated in Phase 2, provide a high-quality suggested answer using the STAR framework. Refer to `references/star-framework-guide.md` for detailed STAR methodology.

**STAR Answer Structure:**
- **Situation** — Brief context (1-2 sentences)
- **Task** — Specific responsibility or challenge faced
- **Action** — Step-by-step what the candidate did (emphasize "I" not "we")
- **Result** — Quantifiable outcome, ideally with metrics; include lessons learned if applicable

**Guidelines for crafting answers:**
- Draw from actual resume achievements whenever possible
- Keep answers concise (2-3 minutes spoken = ~250-350 words)
- Include specific numbers and metrics from the resume
- Ensure the "Action" section is the longest and most detailed
- End with a positive, forward-looking result
- If the resume lacks a perfect story, suggest how to frame a related experience

**For each STAR answer, also provide:**
- The specific resume bullet point or experience it maps to
- A "key takeaway" line that summarizes the competency demonstrated
- A confidence rating (Strong / Moderate / Weak) based on how well the resume supports the story

### Phase 4: Identify Follow-Up Questions

For each major question category, predict likely follow-ups and probing questions an interviewer might ask.

**Types of follow-ups to anticipate:**
- **Drill-downs** — "Can you walk me through the specific steps you took?"
- **Counterfactuals** — "What would you have done if X hadn't worked?"
- **Scale questions** — "How would that approach work with a team of 50?"
- **Failure pivots** — "Tell me about a time when that approach didn't work."
- **Alternative perspectives** — "What did your teammates think about that decision?"
- **Hypothetical extensions** — "How would you apply that to our specific problem of Y?"

**For each predicted follow-up:**
- Explain why the interviewer might ask it
- Provide a suggested response direction
- Note which resume experience to anchor the response in

### Phase 5: Highlight Preparation Gaps

Identify and rank areas where the candidate needs to do additional preparation before the interview.

**Gap categories:**
1. **Knowledge Gaps** — Technical concepts, tools, or domain knowledge required by the JD but not evident in the resume
2. **Experience Gaps** — Responsibilities or scopes the JD expects but the resume doesn't demonstrate
3. **Weak STAR Stories** — Behavioral competencies where the resume lacks strong evidence
4. **Company Knowledge Gaps** — Things the candidate should know about the company but likely doesn't
5. **Common Pitfalls** — Areas where the candidate's profile might raise red flags

**For each gap:**
- Assign severity: Critical / High / Medium / Low
- Provide a specific preparation action (e.g., "Review system design concepts for X", "Prepare a story about Y", "Research the company's Z product")
- Suggest resources if applicable (documentation, courses, practice platforms)

### Phase 6: Deliver Role-Specific Interview Tips

Provide practical, actionable interview tips tailored to the specific role, seniority, and format.

**Tip categories:**
1. **Technical Interview Tactics** — How to approach coding, system design, or case studies for this specific role
2. **Behavioral Interview Tactics** — How to present experience, handle weaknesses, and sell transferable skills
3. **Communication Tips** — How to structure answers, when to pause, how to handle "I don't know"
4. **Format-Specific Tips** — Video, in-person, panel, phone nuances
5. **Stage-Specific Tips** — HR vs. technical vs. final round expectations
6. **Red Flags to Avoid** — Common mistakes for this role level and type

### Phase 7: Generate Output

Deliver the interview preparation materials as a polished, structured HTML document. Use the template at `assets/interview-prep-template.html` if available, or generate a clean HTML document with the following sections:

1. **Cover Summary** — Job title, company, interview stage, overall readiness assessment
2. **Question Bank** — All questions organized by category with the suggested STAR answers for behavioral questions
3. **Follow-Up Guide** — Anticipated follow-ups with response directions
4. **Preparation Checklist** — Gaps ranked by severity with action items
5. **Interview Tips** — Role-specific tactical advice
6. **Quick Reference Card** — One-page summary of top 5 questions and key talking points

Save the output as `interview-prep-report.html` in the current working directory and present it to the user.

**Always also deliver:**
1. A concise conversation summary highlighting the top 3 most likely questions and the 3 most critical preparation gaps
2. The full HTML report via `present_files`

## Language

- Match the dominant language of the job description and resume
- If mixed, default to the language of the JD
- STAR answers and tips should be in the same language as the user's query

## Integration with Other Skills

| Skill | Integration Point | How to Use |
|-------|-------------------|------------|
| `job-hunter` | Phase 3 (Interview Preparation) | When job-hunter reaches interview prep, invoke this skill with the JD and resume collected during job-hunter flow |
| `job-fit-analyzer` | Phase 4 (Recommendations) | After fit analysis, if the user wants interview prep, pass the extracted JD/resume data and the identified gaps to this skill for targeted question generation |
| `job-fit-analyzer` | Gap data | Use the gaps identified by job-fit-analyzer as the starting point for Phase 5 (Preparation Gaps) in this skill |

## Important Notes

- Be honest about gaps. Do not generate fake-sounding STAR answers that claim experiences the resume doesn't support.
- If a resume lacks strong evidence for a behavioral competency, suggest how to frame the best available experience rather than inventing one.
- Calibrate question difficulty to the seniority level. A Staff Engineer interview should have harder system design questions than a Junior Engineer interview.
- Research the company if possible (web search) to generate company-specific questions and demonstrate genuine interest in the prep materials.
- When the user requests a mock interview, use the generated question bank to role-play as the interviewer, adapting follow-up questions based on the user's answers.
- If the user provides no JD or resume, ask for them before proceeding. Do not generate generic questions.
