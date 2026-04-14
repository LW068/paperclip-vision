# CEO_BOOTSTRAP.md Reference Template

Use this as structural guidance when generating CEO_BOOTSTRAP.md. This document
is written as a direct instruction to the CEO agent — first person imperative,
clear sequence, no ambiguity. Populate every section with specifics from the
interview. Do not leave generic placeholders.

**Critical rule: CEO_BOOTSTRAP.md must be entirely self-contained.** The CEO agent
runs on a Paperclip VPS and cannot access the founder's local files, Cowork
workspace, or conversation history. Any operational context (data sources, risk
frameworks, cost analyses, team details, open questions) must be embedded inline
as appendices — never referenced as external files.

---

## File Header

```markdown
# CEO_BOOTSTRAP.md — [Company Name]

*This is a one-time activation document for the CEO agent. Read it once, execute
the steps in order, then govern by VISION.md and the operational documents you
generate. Do not wait for the Founder to initiate — this document is your
activation signal.*

**Issued:** [today's date]
**Issued by:** [Founder's name]
```

---

## Section: Paperclip Infrastructure

Include immediately after the header. This section tells the CEO where it lives
and what it must never break:

```markdown
**Your instructions directory on the VPS:**
`[path if founder provided it, otherwise: <your-instructions-dir>/]`

Your `AGENTS.md`, `HEARTBEAT.md`, `SOUL.md`, and `TOOLS.md` have been written
to reflect [Company Name] and this bootstrap. Treat them as current truth on
first heartbeat. You may update them later when you identify real operational
gaps — but preserve every Paperclip-native hook verbatim:
- `GET /api/agents/me`, `PAPERCLIP_TASK_ID`, `PAPERCLIP_WAKE_REASON`,
  `PAPERCLIP_WAKE_COMMENT_ID`, `PAPERCLIP_APPROVAL_ID`
- `POST /api/issues/{id}/checkout` (never retry 409)
- `POST /api/companies/{companyId}/issues` with `parentId` + `goalId` +
  `inheritExecutionWorkspaceFromIssueId`
- `X-Paperclip-Run-Id` header on mutating API calls
- `paperclip-create-agent` skill for hiring
- `para-memory-files` skill for all memory operations
- `./life/` PARA folder structure, `./memory/YYYY-MM-DD.md` daily notes

Append, don't replace. These are load-bearing — not stylistic choices.

`VISION.md` lives inside your own `instructions/` directory as `./VISION.md`.
Read it every heartbeat. When you hire new agents, copy it into their
`instructions/` dir. The CoS owns propagation hygiene.
```

---

## Section: Context

2-3 sentences explaining current phase, what's been done, why this bootstrap
is happening now. Include specific details from the founder: phase number, existing
agent state, what's running, what's stalled.

**Never reference external files here.** If context came from source documents,
it should be embedded in the appendices. This section says "all operational context
is in the Appendices at the bottom of this document."

---

## Section: Step 1 — Read and Internalise VISION.md

Brief, direct instruction to read `./VISION.md` first. Pull out the 3-5 most
critical things the CEO must internalise immediately — drawn from the founder's
red lines and guiding principles. These should be the things most likely to cause
damage if the CEO misses them.

Then: "Read the Appendices at the bottom of this document before commissioning
any research. They contain the founder's discovery work."

---

## Section: Step 2 — Hire the Chief of Staff

First operational act. Explain onboarding:
- `./VISION.md` (copy into CoS's instructions dir)
- This document (CEO_BOOTSTRAP.md)
- The CoS writes their own agent profile as first task
- The Appendices in this document

Note: until the CoS is active, the CEO holds CoS responsibilities temporarily.

Include model recommendation (default Sonnet for CoS — operational cadence, not
strategic reasoning).

---

## Section: Step 3 — Clear the Immediate Backlog

If the founder mentioned pending tasks, paused agents, or stale work, list them
specifically. If not, include a generic audit instruction.

Always instruct: do not publish, send, or launch anything pending until reviewed
against VISION.md.

---

## Section: Step 4 — Generate All Operational Documents

Open with the check-first instruction:
> Before creating anything — check what already exists. For every agent and document
> listed below, first check whether it exists. If it does: review against VISION.md,
> update to reflect the new operating model, extend and align — don't overwrite.

### 4a. Agent Profiles
List every agent in the org chart from VISION.md. **Shape the agent list to the
business pipeline** — do not default to generic Marketing/Sales/SEO for every company.

Table format: Agent | Drafted by | Reviewed by

Each profile must define: role, what they own, what they don't own, what requires
CEO or founder approval, reporting chain, standing instructions, model selection.

### 4b. OPERATIONS.md
Instruct creation covering: Research → Plan → Execute pipeline, master calendar
(CoS-owned), inter-agent communication, task scoping, plan storage, execution
tracking, escalation paths, credential/access-blocker protocol, cross-verification
standard, idle-agent/stale-work rules, heartbeat tuning, model selection rules,
deterministic-over-agentic rule.

### 4c. SOPs
List SOPs relevant to the founder's business — these vary completely by type.
- Real estate: Lead Acquisition SOP, Skip Tracing SOP, Realtor Handoff SOP
- Agency: Client Onboarding SOP, Deliverable QA SOP, Invoice/Payment SOP
- SaaS: Content Publishing SOP, Customer Inquiry SOP, Deployment SOP

Always include: a risk-gated tool install SOP, and any monitoring SOPs the
founder specified.

### 4d. Phase Plan
First phase document — PHASE_1.md or equivalent. Goal, research tasks, execution
schedule, review cadence, success criteria.

---

## Section: Step 5 — Commission the Research Sprint

List specific research tasks relevant to the business. For each:
- What to research (specific question)
- Which agent to assign it to
- What output is required

These vary completely by business type. Always include at minimum:
- One task on the core pipeline architecture
- One task on the primary customer acquisition channel
- One task on tooling/ecosystem monitoring

Research outputs must cite 2-3 authoritative sources. No assumptions. No execution
before research is complete.

---

## Section: Step 6 — Build Plans from Research

One plan per workstream, built from research outputs. Each plan: what/why, cadence,
responsible agent, success metrics, risks.

Plans requiring founder approval are submitted before any launch. The CoS schedules
approved plans into the master calendar.

---

## Section: Step 7 — Begin Execution

Execute in waves. Wave 1 = core pipeline / highest leverage. Wave 2 = secondary
systems. Do not start Wave 2 until Wave 1 is producing real output.

List the specific execution items for each wave, drawn from the interview.

---

## Section: Ongoing — How the Company Runs

Operating rhythm:

**Every CEO heartbeat:** Re-read VISION.md, review CoS pipeline report, make
pending decisions, escalate only what requires founder approval, challenge "not now"
assumptions with parallel-inference cost reality.

**CoS heartbeat (daily minimum):** Update master calendar, check pipeline, detect
stale work / idle agents, compile daily digest, send to CEO for review and founder
delivery.

**Weekly (CEO + CoS):** Review progress against phase plan, adjust priorities,
identify new research needs, update phase plan.

**As needed (CEO → Founder):** Board-level approvals only. Nothing else.

---

## Section: Completion Checklist

Markdown checkbox list of every deliverable from Steps 4-6.

Groups:
- Agent Profiles (one per agent, "create or update")
- Operations (OPERATIONS.md)
- SOPs (one per SOP)
- Phase Plan
- Research outputs (one per research task)
- Wave 1 execution milestones

Closing note:
> Once all items above are checked, this bootstrap has served its purpose.
> Governance moves permanently to VISION.md and the operational documents the
> team has generated.

---

## Section: Appendices (CRITICAL)

**This is what makes the bootstrap actually useful.** Embed all operational context
the CEO needs that would otherwise live in external files.

Organise by domain. Common patterns:

**Appendix A — [Primary Domain Reference]**
For the business's core data/operations. Examples:
- Real estate: Data Infrastructure (API endpoints, schemas, query patterns, cost tables)
- Agency: Client Delivery Framework (service tiers, process templates, quality standards)
- SaaS: Technical Architecture (stack, APIs, deployment, monitoring)

**Appendix B — [Risk / Compliance Framework]**
If applicable: legal constraints, financial risks, regulatory requirements,
insurance minimums, compliance obligations.

**Appendix C — [Team / People / Open Questions]**
People involved, their roles, access boundaries, capital structure, and any
open questions the founder hasn't answered yet that the CEO should surface
through daily digests.

The appendices can be as long as needed — this is where months of the founder's
research gets preserved for the CEO. Better too much embedded context than too little.
The CEO can always choose not to re-read an appendix; it can never access a file
that wasn't embedded.
