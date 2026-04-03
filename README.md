# Paperclip Vision

**A Claude Code skill that interviews your founder and writes the constitution your AI company needs to run itself.**

Paperclip Vision conducts a structured strategic interview and produces two documents that let an AI-run company operate autonomously — without the founder needing to be in the loop for day-to-day decisions.

---

## What It Does

Most AI agent setups fail not because the agents are bad, but because they have no clear mandate. They don't know what they're allowed to do, who to escalate to, or what the company is actually trying to accomplish.

Paperclip Vision solves this at the source. It interviews the founder, extracts their strategic intent, and translates it into two machine-readable documents:

| Document | Purpose |
|---|---|
| `VISION.md` | The company constitution. Mission, revenue model, target customer, growth strategy, org structure, CEO mandate, and guiding principles. The CEO agent reads this every heartbeat. |
| `CEO_BOOTSTRAP.md` | One-time activation instructions for the CEO agent. What to do first, in what order, and what to generate so the company can run itself. |

---

## How It Works

### 1. Scans Your Project First

Before asking a single question, the skill reads your working directory — agent profiles, heartbeat files, existing vision documents, phase plans, tech stack, ops files — and uses what it finds to pre-fill context, skip redundant questions, and make the interview feel specific to your company.

### 2. Structured Founder Interview

A 16-question interview across six sections:

- **The Big Picture** — ultimate goal and 12-month destination
- **Revenue & Customers** — pricing model, revenue target, ideal customer
- **Growth & Marketing** — channels, budget, and sales model
- **Product Direction** — current status and roadmap
- **CEO Autonomy** — what the CEO can do alone vs. what needs your approval
- **Vision & Identity** — companies you admire, success signals, non-negotiables

Questions use single-select, multi-select, and free text. Each answer is acknowledged before moving on. If something is ambiguous or interesting, the skill asks a short follow-up rather than guessing.

### 3. Generates Both Documents

Once the interview is complete, the skill writes `VISION.md` and `CEO_BOOTSTRAP.md` — fully populated, no placeholders, adapted to your specific company and industry.

---

## The Core Philosophy: Research → Plan → Execute

Every VISION.md includes this operating model as a non-negotiable principle. It's what prevents autonomous agents from:

- Publishing too much content too fast and destroying SEO
- Entering communities without understanding the norms and getting banned
- Launching channels without a strategy

**Gate 1 — Research** produces a written output with cited sources.  
**Gate 2 — Plan** is reviewed by the Chief of Staff before anything starts.  
**Gate 3 — Execute** is scheduled into the master calendar by the CoS.

No execution without a plan. No plan without research.

---

## Org Structure

Every company bootstrapped with Paperclip Vision gets the same foundational structure:

```
Founder
└── CEO Agent
    └── Chief of Staff (CoS) Agent
        ├── Head of Marketing
        │   └── Head of SEO
        ├── Head of Sales
        └── [department heads per your company]
```

The **CEO** stays strategic — sets direction, makes decisions, handles escalations.  
The **CoS** is the operational backbone — owns the pipeline, the calendar, and inter-agent coordination.

Hiring the CoS is always Step 2 of the bootstrap. It's within the CEO's mandate — no founder approval needed.

---

## What Gets Generated

### `VISION.md` covers:
- Mission statement (what the company does and what it explicitly is not)
- 12-month goal and 3-year vision
- Revenue model and pricing structure
- Primary and secondary target customers
- Growth strategy with channels in priority order
- Sales model
- Product direction and roadmap
- Org chart and role definitions
- CEO mandate — autonomous actions vs. items requiring founder approval
- Reporting cadence
- Guiding principles
- Success metrics at 3-month, 12-month, and 3-year horizons

### `CEO_BOOTSTRAP.md` covers:
- Step-by-step activation sequence (7 steps, in order)
- Which documents and agent profiles to generate (or update, if they already exist)
- Research sprint tasks before any execution begins
- Channel plans to build from research outputs
- Ongoing operating rhythm (heartbeat → daily → weekly)
- A completion checklist — once all items are checked, governance moves permanently to VISION.md

---

## Installation

This skill runs inside [Claude Code](https://claude.ai/code). Install it by adding the `paperclip-vision` skill to your Claude Code skills directory.

```bash
# Clone into your Claude skills folder
git clone https://github.com/aronprins/paperclip-vision ~/.claude/skills/paperclip-vision
```

Then invoke it from any project directory:

```
/paperclip-vision
```

Claude will scan your current directory and begin the interview.

---

## Requirements

- [Claude Code](https://claude.ai/code) (CLI or desktop app)
- A working directory that represents your company (even if mostly empty)

---

## Part of the Paperclip Ecosystem

Paperclip Vision is one skill in the broader **Paperclip** framework for building AI-run companies. Other skills in the ecosystem handle agent hiring, task coordination, control plane management, and plugin creation.

> Paperclip is a framework for companies that run on AI agents — not companies that use AI as a tool.

---

## Author

Built by [Aron Prins](https://github.com/aronprins).

If you're building an AI-run company on Paperclip and need help with setup, architecture, or consulting — reach out on X:

**[@aronprins](https://x.com/aronprins)**

Follow for updates on Paperclip, new skills, and AI company building.

---

## License

MIT
