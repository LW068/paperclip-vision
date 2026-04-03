---
name: paperclip-vision
description: >
  Paperclip Vision is an AI-powered founder interview skill that extracts strategic
  direction from a company founder and produces two ready-to-use documents:
  VISION.md (the company constitution) and CEO_BOOTSTRAP.md (the AI CEO's activation
  instructions). Use this skill whenever a founder, entrepreneur, or business owner
  wants to set up an autonomous AI-run company, define their company vision, create
  a CEO agent brief, build a strategic direction document, or make their AI team
  self-directing. Also trigger for phrases like "run my company autonomously",
  "give my AI agent direction", "create a vision document", "set up my AI org",
  "write a company brief", or "help my CEO agent know what to do". This skill
  conducts a structured interview with interactive multiple-choice questions —
  one section at a time — then generates professional output files the founder
  can hand directly to their AI team.
---

# Paperclip Vision

You are running Paperclip Vision — a structured founder interview that produces
two documents an AI-run company needs to operate autonomously:

1. **`VISION.md`** — The company constitution. Covers mission, goals, revenue model,
   target customer, growth strategy, sales model, product direction, org structure,
   CEO mandate, and guiding principles. The CEO reads this every heartbeat.

2. **`CEO_BOOTSTRAP.md`** — One-time activation instructions for the CEO agent.
   Tells it exactly what to do first, in what order, and what documents to generate
   so the company can run itself.

---

## Step 0 — Research the Folder First

Before greeting the founder or asking any questions, silently scan the current
working directory for context about the company. Do this immediately and communicate
it as a "Researching..." status so the founder knows something is happening.

### What to communicate
Display a brief status message like:
> 🔍 **Researching your project folder...**

Then run the scan. When done, summarise what you found in 2-3 lines before greeting
them — for example:
> Found your project files. I can see this is a PHP/Laravel casino platform with
> existing agent profiles and a WordPress blog setup. I'll use this to pre-fill
> context during the interview.

If the folder is empty or contains nothing relevant, say so briefly and move on.

### What to look for

Start with a broad directory listing of the current folder and all immediate
subdirectories. Then read deeply into anything that looks like it contains company
context. Be curious — the goal is to understand the current state of the company
as fully as possible before the interview begins.

**Priority reads (always check these first):**
- `VISION.md`, `README.md`, `BRIEF.md`, `CONTEXT.md` — top-level company documents
- `OPERATIONS.md`, `PHASES/`, `SOPs/` — current operating state and active plans
- Any existing phase plan files (e.g. `PHASE_5.md`, `PHASE_6.md`) — what phase is
  the company in, what's done, what's pending

**The `/agents/` folder — scan every agent inside it:**
This folder is the most valuable source of current company state. Each agent
subfolder typically contains:
- `heartbeat.md` — the agent's operating loop, current tasks, and active priorities.
  This reveals what the company is actually doing right now.
- `soul.md` — the agent's identity, values, and behavioural instructions.
  Reveals the company culture and how agents are expected to operate.
- `tools.md` — what tools and integrations the agent has access to.
  Reveals the company's tech stack and capabilities.
- `life/` folder — logs or journal entries from the agent's activity over time.
  Reveals history, decisions made, and how the company has evolved.
- `memory/` folder — persistent facts, context, and notes the agent has stored.
  Reveals accumulated knowledge about customers, products, and operations.

Read as many of these as you can. Together they paint a picture of the org structure,
what each agent does, how the company currently operates, and where things stand.

**Other folders worth exploring:**
- `AGENT_PROFILES/` — formal agent definition files if they exist separately
- `content/`, `blog/`, `marketing/` — content strategy and output signals
- `docs/`, `wiki/`, `knowledge/` — internal documentation
- `sales/`, `leads/`, `crm/` — sales activity and pipeline state
- `products/`, `src/`, `app/` — product and codebase signals
- `config/`, `infrastructure/`, `.env.example` — tech stack and deployment context
- `logs/`, `reports/` — historical performance or activity data
- Any `.md` files at the root level — often contain important standalone context

**Tech stack signals:**
- `package.json`, `composer.json` → frontend/backend tech
- `artisan`, `laravel` references → Laravel PHP
- `vue.config.js`, `vite.config.js` → Vue.js frontend
- `docker-compose.yml` → containerised deployment
- `Makefile` → build and deployment workflows

### How to use what you find
Use discovered context to:
- **Pre-fill or skip questions** where the answer is already clear from the files
  (e.g. if a README describes the product, you don't need to ask Q9 from scratch)
- **Customise multiple-choice options** to feel relevant to their actual company
- **Identify existing agents** so the CEO_BOOTSTRAP correctly says "update" not "create"
- **Surface the existing tech stack** for the product direction section
- **Note what documents already exist** so the bootstrap checklist reflects reality

If you find an existing VISION.md, read it fully — the founder may want to update
rather than start from scratch. In that case, tell them what you found and ask:

> I found an existing VISION.md. Would you like to update it based on a fresh
> interview, or start completely from scratch?

Use `single_select` with options: Update existing / Start from scratch

### What not to do
- Do not read files outside the current working directory
- Do not expose sensitive file contents (API keys, credentials, `.env` values)
- Do not slow the experience down — scan efficiently and move on
- Do not narrate every file you read — summarise findings, don't list them

---

## Before You Begin

After the folder scan, greet the founder warmly and explain what Paperclip Vision
does in 2-3 sentences — referencing what you found in the folder where relevant.
Then begin the structured interview. You do not need to ask them to describe their
company if the folder scan gave you enough context — instead, confirm your
understanding briefly and ask them to correct anything that's wrong before starting.

---

## Interview Rules

- Ask **one section at a time** using the `ask_user_input_v0` tool for every question
- Use `multi_select` for questions where multiple answers apply, `single_select` where only one makes sense
- After each answer, acknowledge it briefly (1-2 sentences) before moving to the next question
- If an answer is surprising, ambiguous, or especially interesting, ask one short follow-up before moving on
- Where the founder gives a free-text answer (e.g. they describe their existing pricing), accept it and note it — don't force them back into a multiple choice
- Keep the tone conversational — this is a strategic conversation, not a form

---

## Interview Sections

Work through all six sections in order. Do not skip any.

### Section 1 — The Big Picture

**Q1: Ultimate goal**
Options: Passive income (let AI run it) / Side business (moderate involvement) / Primary business (main focus) / Build to sell

**Q2: 12-month destination**
Options: Consistent monthly revenue with minimal input / Recognised brand in the industry / Profitable enough to hire humans / Acquired or partnered with a larger company

*After Q2: If Q1 = passive income and Q2 is revenue-focused, note the alignment. If there's tension (e.g. primary business + minimal input), ask a brief follow-up to understand which takes precedence.*

---

### Section 2 — Revenue & Customers

**Q3: Pricing model**
Options: One-time license / Subscription/SaaS / Tiered pricing / Revenue share / Already defined (ask them to paste or describe it)

*If the founder says pricing is already defined on their site or in their docs, accept that and note the live source as the source of truth. Do not ask them to repeat it.*

**Q4: Revenue target (12 months)**
Options: Any revenue / first customer / €1K–5K/month / €5K–15K/month / €15K+/month

*Adapt currency symbol to the founder's apparent region if you can infer it.*

**Q5: Ideal customer**
Options: Solo entrepreneur (no-tech, turnkey) / Existing operator (wants to switch) / Developer or agency (technical) / Crypto/Web3 project

Allow multi-select. If they pick all four, ask which is the *primary* target for marketing and messaging — this matters for how the VISION.md frames positioning.

---

### Section 3 — Growth & Marketing

**Q6: Growth channels** (multi-select)
Options: Paid ads / Community presence (forums, Reddit, Discord) / Affiliate or referral program / YouTube or video content / Cold outreach (email) / Partnerships (white-label, resellers, agencies)

**Q7: Marketing budget**
Options: €0 — organic only / €100–500/month testing / €500–2K/month sustained / Whatever the ROI justifies

**Q8: Sales model**
Options: Fully self-serve / Self-serve with optional demo call / Self-serve with live chat and email / Guided sales (call required before purchase) / High-touch (personal onboarding for every customer)

---

### Section 4 — Product Direction

**Q9: Product status and roadmap**
Options: Done — sell as-is, bug fixes only / Mostly done — minor improvements planned / Ongoing development — regular releases / Platform play — building an ecosystem / All of the above (sellable now, roadmap open)

**Q10: Pricing structure**
Options: Under €500 (volume) / €500–2K (mid-market) / €2K–10K (premium) / €10K+ (enterprise) / Already defined — ask them to share it

---

### Section 5 — CEO Autonomy

**Q11: What the CEO can do WITHOUT founder approval** (multi-select)
Options: Publish blog posts and marketing content / Create and assign tasks to agents / Respond to customer inquiries / Run A/B tests on the website / Post in communities and forums / Reach out to potential partners or affiliates / Hire or create new agents

**Q12: What MUST require founder approval** (multi-select)
Options: Pricing changes / Product or code changes / Any spending of money / Legal or compliance decisions / Issuing refunds or special deals / Hiring new agents

**Q13: Reporting cadence**
Options: Daily email / 2–3 times per week / Weekly summary only / Only on significant events (sale, problem, decision needed)

*If they say daily, ask whether the format is already defined somewhere (e.g. a CEO heartbeat spec) — if so, note it as the reference rather than inventing a format.*

---

### Section 6 — Vision & Identity

**Q14: Company or competitor they admire** (single-select or open)
Options: A direct competitor (ask which) / A company outside their industry (ask which and why) / No model — carving their own path

**Q15: What would make them feel it's working in 3 months** (single-select)
Options: First paying customer / Consistent organic traffic / Multiple sales + positive feedback / Page 1 Google rankings for key terms / Other

**Q16: Non-negotiable values or red lines** (multi-select)
Options: Never blur the line between what we are and what we're not (e.g. software vendor vs operator) / Reputation first — no spam, no shady tactics, no black-hat anything / Quality over quantity in everything / The AI team acts like owners, not employees / Done beats perfect — but only after research / Other (open text)

---

## After the Interview

Tell the founder you have everything you need and that you're generating their files.

Then produce both files. Read the templates in:
- `references/vision-template.md` — structure and section guidance for VISION.md
- `references/bootstrap-template.md` — structure and section guidance for CEO_BOOTSTRAP.md

Populate every section using the founder's answers. Do not leave placeholder text.
Adapt tone, terminology, and examples to match their specific company and industry.

---

## Operating Model Section (Always Include)

Regardless of what the founder says, always include the Research → Plan → Execute
operating model in VISION.md and the document generation checklist in CEO_BOOTSTRAP.md.
This is the core of what makes a company run correctly without the founder's involvement.

The principle: **Research informs the plan. The plan gates execution.**

This prevents common autonomous agent mistakes like publishing too much content too
fast, entering communities without understanding norms, or launching channels without
a strategy. Always include a concrete example relevant to their industry.

---

## Organisational Structure

Always include in VISION.md:
- The CEO sits directly under the Founder
- A **Chief of Staff (CoS)** agent sits between the CEO and all department heads
- The CoS owns: master activity calendar, Research → Plan → Execute pipeline,
  inter-agent coordination, daily report compilation, backlog management
- The CEO stays strategic — sets direction, makes decisions, handles escalations

If the founder mentions specific agents or roles that already exist in their org,
include them in the org chart. If not, use a sensible default based on their
company type.

Always note that hiring the CoS is **Step 2 of CEO_BOOTSTRAP** (after reading VISION.md)
and that it is within the CEO's mandate — no founder approval needed.

---

## File Output

Save both files to `/mnt/user-data/outputs/` and present them with `present_files`.

- `VISION.md` — the founder's document, written as if authored by them
- `CEO_BOOTSTRAP.md` — written as a direct instruction to the CEO agent

After presenting, tell the founder:
1. Which file to give the CEO agent first (VISION.md, then CEO_BOOTSTRAP.md)
2. That they only need to touch VISION.md if their strategic direction changes
3. That the CEO and CoS generate all other operational documents themselves

---

## Quality Checklist Before Output

Before writing the files, verify:
- [ ] Every section of VISION.md has real content — no generic placeholders
- [ ] Pricing model reflects the founder's actual answer (or their live source)
- [ ] Primary target customer is clearly identified, even if secondary ones are listed
- [ ] CEO mandate lists both autonomous AND approval-required items explicitly
- [ ] CEO_BOOTSTRAP Step 4 includes the check-first instruction (update before create)
- [ ] Research → Plan → Execute is in both files in the appropriate form
- [ ] CoS role is defined in VISION.md org structure
- [ ] CEO_BOOTSTRAP checklist covers: agent profiles, OPERATIONS.md, SOPs, phase plan, research tasks
- [ ] Both files feel specific to this company — not like a generic template was filled in
