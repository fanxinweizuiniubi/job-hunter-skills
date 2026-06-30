---
name: job-hunter
description: Help users find jobs and analyze job fit. Use when the user wants to search for jobs, analyze job descriptions against their resume, prepare for interviews, or optimize their career search strategy. Should be triggered by phrases like "find a job", "job search", "career", "求职", "找工作", "跳槽".
agent_created: true
---

# Job Hunter

Help users find the right job by collecting structured preferences and providing actionable job search support.

## Core Principles

1. **Structured Discovery** — Use the native structured-question UI (`AskUserQuestion`) to collect all job preferences at once, not through back-and-forth chat.
2. **Show, Don't Just Ask** — After collecting preferences, present concrete job search actions (resume analysis, job fit scoring, interview prep) rather than generic advice.
3. **Proactive Matching** — Once profile is complete, proactively suggest next steps: analyze a JD, optimize resume, or search job boards.

## Phase 0: Detect Intent

Determine what the user wants:

- **Mode A: Start Job Search** — New search, build profile. Go to Phase 1.
- **Mode B: Analyze Job Fit** — User has a resume + JD. Go to Phase 2.
- **Mode C: Interview Prep** — User has an interview coming. Go to Phase 3.
- **Mode D: Resume Optimization** — Improve existing resume. Go to Phase 4.

If unclear, default to Mode A and build a profile first.

## Phase 1: Profile Discovery (New Job Search)

**Ask ALL questions together** using the native structured-question UI (`AskUserQuestion`). Do not ask one by one in chat.

**Question 1 — Target Role** (header: "目标职位"):
What role are you looking for? Options:
- 前端工程师
- 后端工程师
- 全栈工程师
- 产品经理
- 数据分析师
- 算法工程师
- UI/UX设计师
- 运营

**Question 2 — Location** (header: "期望城市"):
Where do you want to work? (Single-choice question) Options:
- 北京
- 上海
- 深圳
- 杭州
- 广州
- 成都
- 远程/Remote
- 不限

**Question 3 — Experience Level** (header: "工作经验"):
What's your experience level? (Single-choice question) Options:
- 应届生 / 实习生
- 1-3年
- 3-5年
- 5-10年
- 10年以上

**Question 4 — Salary Expectation** (header: "薪资期望"):
What's your expected salary range (monthly, before tax)? (Single-choice question) Options:
- 10k以下
- 10k-20k
- 20k-30k
- 30k-50k
- 50k以上
- 面议

**Question 5 — Company Size** (header: "公司偏好"):
What company size do you prefer? (multi-select)
Options:
- 大厂（BAT/字节/美团等）
- 中型公司（500-5000人）
- 初创公司（<500人）
- 外企
- 国企/事业单位
- 不限

**Question 6 — Resume Ready** (header: "简历状态"):
Do you have a resume ready? (Single-choice question) Options:
- 已准备好，可以上传
- 有但需优化
- 还没有，需要帮忙写

After the user submits all answers, summarize their profile and proceed to Phase 2 (if they have a resume + JD) or ask them to share their resume and target JD.

## Phase 2: Job Fit Analysis

When the user has a resume and a job description (JD):

1. **Read the resume** — Ask the user to upload or paste their resume
2. **Read the JD** — Ask the user to paste the job description
3. **Use `job-fit-analyzer` skill** — Call the `job-fit-analyzer` skill with the resume and JD to get a detailed compatibility analysis
4. **Present results** — Show the user:
   - Match score (0-100)
   - Key strengths
   - Gaps and risks
   - Actionable suggestions to improve their application

If the user does not have both resume and JD, ask which one they need help with first.

## Phase 3: Interview Preparation

When the user has an upcoming interview:

1. **Identify the company and role** — Use AskUserQuestion if not already known:
   - **Question 1** (header: "面试公司"): Company name? (text input)
   - **Question 2** (header: "面试岗位"): Role? (text input)
   - **Question 3** (header: "面试轮次"): Which round? Options: HR面 / 技术一面 / 技术二面 / 总监面 / 终面
   - **Question 4** (header: "面试形式"): Format? Options: 线上视频 / 线下现场 / 电话

2. **Delegate to `interview-coach` skill** — After collecting interview details, call the `interview-coach` skill with:
   - The job description (collected earlier or ask for it)
   - The candidate's resume (collected earlier or ask for it)
   - Interview stage and format
   - Company name (for company-specific research)

   The `interview-coach` skill will generate a comprehensive interview prep report including personalized questions, STAR answers, follow-ups, gap analysis, and role-specific tips.

3. **Mock interview** (optional) — After the user reviews the prep report, ask if they want to do a mock interview. If yes, use the generated question bank to role-play as the interviewer, adapting follow-up questions based on the user's answers.

## Phase 4: Resume Optimization

When the user wants to improve their resume:

1. **Read the current resume** — Ask the user to upload or paste it
2. **Identify issues** — Common problems:
   - Too long / too short
   - Missing keywords for ATS
   - Weak action verbs
   - No quantifiable achievements
   - Formatting issues

3. **Rewrite suggestions** — Provide specific line-by-line suggestions
4. **Generate optimized version** — If the user approves, generate a polished resume in a clean format (Markdown or HTML)

## Supporting Resources

| Resource | Purpose | When to Use |
|----------|---------|-------------|
| `job-fit-analyzer` skill | Analyze resume vs JD compatibility | Phase 2 |
| `interview-coach` skill | Generate personalized interview questions, STAR answers, and prep materials | Phase 3 |
| Web search | Research companies, roles, salary benchmarks | Throughout |
| `westock-data` / `westock-tool` | If user is interested in finance/quant roles | As needed |
