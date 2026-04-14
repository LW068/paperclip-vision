# Paperclip Vision

**A Claude skill that interviews a founder of any kind of company and produces the constitution their AI team needs to run itself.**

Paperclip Vision runs a structured strategic interview, then writes the machine-readable documents that let an AI-run company on [Paperclip](https://usepaperclip.com) (or any agent platform) operate autonomously — without the founder in the loop for day-to-day decisions.

> **Read this README fully before invoking the skill.** The skill itself prompts for confirmation that you've read it. The philosophy, extensibility notes, and "does NOT do" boundaries below aren't repeated inside SKILL.md — they live here.

---

## Industry-Agnostic By Design

This skill is not a SaaS template. It works for **any business that can be run by an AI team**:

- Real estate investing (flips, wholesaling, BRRRR, rent-to-own, tax-deed)
- Agencies (creative, web, marketing, consulting)
- SaaS and digital products
- E-commerce and DTC brands
- Service businesses (coaching, freelancing, local services)
- Professional services (law, accounting, advisory)
- Anything else where a founder wants an AI CEO running the show

The interview adapts dynamically once it detects your business type. Questions, org chart shape, red-line scenarios, risk prompts, and output terminology all reshape around what you actually do. A real estate flipper doesn't get asked about SaaS pricing tiers; a creative agency doesn't get a Head of SEO by default.

---

## What It Generates

| Document | Purpose |
|---|---|
| `VISION.md` | The company constitution. Mission, revenue model, target customer, growth strategy, org structure, CEO mandate, red lines, risk guardrails, guiding principles. Read by the CEO agent every heartbeat. |
| `CEO_BOOTSTRAP.md` | One-time activation instructions for the CEO agent — a self-contained package with every operational context embedded as appendices (because the CEO on a Paperclip VPS can't read your local files). |
| `AGENTS.md` *(optional)* | CEO role definition, delegation rules, org routing. Lives in the CEO agent's `instructions/` directory. |
| `HEARTBEAT.md` *(optional)* | CEO's heartbeat checklist, fused with Paperclip-native primitives (checkout flow, PARA memory, delegation). |
| `SOUL.md` *(optional)* | CEO persona, voice, strategic posture. |

---

## What This Skill Does NOT Do

Clear expectations up front. This skill is a **constitution writer**, not a company operator.

- ❌ **It does not run your company.** The CEO agent you activate with these documents runs the company. The skill only produces the documents.
- ❌ **It does not replace founder judgment.** You still decide direction, red lines, and risk appetite. The skill surfaces and structures your thinking; it doesn't think for you.
- ❌ **It does not connect to external tools.** No API integrations, no Slack installs, no database writes. Just document generation.
- ❌ **It does not guarantee success.** A clear constitution is necessary, not sufficient. Bad strategy becomes an efficient bad strategy.
- ❌ **It does not maintain itself.** VISION.md is a living document — you and your CEO update it as direction changes. The skill only writes v1.
- ❌ **It does not lock you into Paperclip.** The generated docs work on any agent platform. Paperclip-native hooks are additive — strip them if you're hosting elsewhere.

---

## How the CEO Agent Handles Context Files

A critical thing the skill teaches the CEO agent, and worth understanding up front:

### VISION.md propagates per-agent, not centrally

Paperclip (and most agent platforms) don't have a shared "company root docs" folder. Each agent has its own `instructions/` directory. So:

1. `VISION.md` lives in the **CEO agent's** `instructions/` directory as `./VISION.md`
2. **When the CEO hires a new agent** (e.g. Chief of Staff, department head) via `paperclip-create-agent` — the bootstrap instructs it to **copy VISION.md into that new agent's `instructions/` directory** as part of onboarding, and to add a "read VISION.md every heartbeat" directive to the new agent's AGENTS.md
3. **When VISION.md is amended** later — the Chief of Staff sweeps every active agent's `instructions/` dir and updates their copies. Propagation hygiene is a standing CoS responsibility.

This pattern is built into the generated CEO_BOOTSTRAP.md. You don't configure it; the CEO inherits the behaviour automatically.

### The same pattern works for any document you want to propagate

If you add your own docs (see Extensibility below), you can tell the CoS in VISION.md to propagate those too. For example: "`STATUS.md` is the live project one-pager, maintained by the CEO, copied to the CoS's instructions dir on update."

---

## The Polish Round (Built Into the Skill)

Here's what most "generate my docs" tools skip and what we insist on:

**After the skill generates your VISION.md + CEO_BOOTSTRAP.md + instruction files, it runs a mandatory polish round before declaring done:**

1. **Skill self-audit.** The skill re-reads everything it just produced and flags vague sections, generic language, contradictions, missing context, and any section still marked `⚠️ Assumed from context`. It presents a numbered list; you say "fix 1, 3, 7" and it edits.

2. **Founder polish prompt.** The skill explicitly asks you to read VISION.md and AGENTS.md end-to-end *before activating the CEO*. Any wording, priority, org chart, or red-line line that feels off — you flag it, the skill edits. Iterates until you say "done."

3. **CEO-side polish on first heartbeat.** CEO_BOOTSTRAP includes a directive: on first heartbeat, after reading VISION.md, the CEO identifies vague sections / contradictions / gaps and surfaces them to you through the daily digest. Alignment is continuous, not a one-shot event.

This is non-negotiable — the constitution is load-bearing for everything downstream.

---

## Extensibility: Fork It and Make It Yours

**You are actively encouraged to edit this skill.** Once installed in your Claude / Claude Code / agent provider of choice, the skill files are yours to modify:

- Add new questions to the interview
- Remove sections that don't apply to your business
- Change the output document list
- Swap the Research → Plan → Execute framing for a different operating model
- Rewrite the polish round prompts to match your voice
- Add industries the current skill doesn't cover well

The skill is a **starting point**, not a prescription.

### Generating more docs than VISION + BOOTSTRAP

The two default documents are the minimum viable constitution. Many founders want more. Common extensions:

- **`STATUS.md`** — a live one-pager the CEO keeps continuously updated with current project state, blockers, wins, and open decisions. You read it instead of sifting through daily digests. (This is how some of us use it day-to-day.)
- **`METRICS.md`** — canonical definitions of the numbers you care about and how they're calculated.
- **`RUNBOOK.md`** — operational playbooks for recurring situations (e.g. a client escalation, a market shift, a new channel launch).
- **`CAPITAL.md`** — for real estate or any capital-intensive business, a live view of deployed capital, liquidity, and exposure.
- **Industry-specific SOPs** — flipping protocols, client onboarding flows, editorial standards, deployment checklists — whatever your business actually does.
- **`PEOPLE.md`** — the humans in your orbit: partners, contractors, vendors, advisors, and how the CEO should interact with each.

To add any of these: edit SKILL.md to ask the relevant questions during the interview, add a template under `references/`, and update the file-output section to generate and propagate the new doc. The extensibility pattern matches how VISION.md itself is handled.

**Not every founder wants these extras.** That's why they're opt-in, not defaults. Keep your skill lean — generate only what you'll actually use.

---

## Installation

This skill runs inside Claude (Claude Code, the desktop app, or any environment that supports skills).

```bash
# Install into your Claude skills folder
git clone https://github.com/LW068/paperclip-vision ~/.claude/skills/paperclip-vision
```

Or install from the original upstream:

```bash
git clone https://github.com/aronprins/paperclip-vision ~/.claude/skills/paperclip-vision
```

Then invoke it from any project directory:

```
/paperclip-vision
```

The skill will prompt you to confirm you've read this README. Type `yes` and it'll scan your working directory, pre-fill from the conversation context, and begin the interview.

---

## Requirements

- Claude (CLI, desktop, web, or any skill-supporting environment)
- A working directory that represents your company (even if mostly empty)
- ~30 minutes for the interview + polish round (longer if the conversation is rich — the skill skips anything it can pre-fill)

---

## Tips to Run This Smoothly

A few Paperclip settings worth checking once your CEO is activated. These aren't hard requirements — the skill works without them — but they make the difference between a CEO that actually operates autonomously and one that's constantly pinging you.

- **Turn off "Require board approval for new hires."** Under your Paperclip company settings → `Hiring` section → toggle it off. Once VISION.md is aligned and the CEO has a clear org-chart mandate, requiring founder sign-off on every hire defeats the whole point of delegation. The CEO is aligned now — trust it to hire within the mandate. (If a red line is crossed, the CEO escalates per VISION.md anyway.)
- **Let the CEO set its own heartbeat cadence.** Don't micromanage the rhythm. The bootstrap gives the CEO a sensible default; if the business needs a different cadence, the CEO will propose it through the daily digest.

Revisit these as the company matures. Early on you may want more oversight; once you trust the CEO's judgement, loosen the reins.

---

## What's New In This Fork

This fork extends the original `aronprins/paperclip-vision` with:

- **Industry-agnostic interview** — adapts to real estate, agencies, SaaS, services, e-commerce, consulting, and more
- **Conversation-context pre-fill** — skips questions the conversation already answered
- **Self-contained CEO_BOOTSTRAP** — embeds all operational context as appendices so VPS-hosted CEOs work without local-file access
- **Paperclip-native file structure** — per-agent `instructions/` layout, VISION.md propagation pattern on hire
- **Optional AGENTS.md / HEARTBEAT.md / SOUL.md** generation for the CEO's instructions directory
- **Pipeline-shaped org charts** — not default Marketing/Sales/SEO for every company
- **Red-line stress test** — scripted hypotheticals to surface implicit red lines
- **Industry-specific risk prompts** — tailored compliance/risk questions by business type
- **Confidence markers** — pre-filled sections visibly flagged for verification
- **Internal consistency auto-check** — automated pre-output consistency pass
- **Mandatory polish round** — skill self-audits + founder re-reads + CEO polishes on first heartbeat

---

## Part of the Paperclip Ecosystem

Paperclip Vision is one skill in the broader **Paperclip** framework for building AI-run companies. Other skills in the ecosystem handle agent hiring, task coordination, control plane management, and plugin creation.

> Paperclip is a framework for companies that run on AI agents — not companies that use AI as a tool.

---

## Credits

Originally built by [Aron Prins](https://github.com/aronprins) — follow him on X: **[@aronprins](https://x.com/aronprins)** for updates on Paperclip and the core skill.

This fork is maintained by [LW068](https://github.com/LW068) and extends the original with industry-agnostic support, the polish round, and VPS-ready self-containment.

---

## License

MIT
