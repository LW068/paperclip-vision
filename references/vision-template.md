# VISION.md Reference Template

Use this as structural guidance when generating the founder's VISION.md.
Every section must be populated with real content from the interview.
Do not copy this template verbatim — adapt every section to the specific company,
industry, and business model. This template is industry-agnostic by design.

---

## File Header

```markdown
# VISION.md — [Company Name]

*This is the Founder's strategic vision document. The CEO reads this every heartbeat
to guide all decisions. It is the constitution of the company — stable, authoritative,
and rarely changed. All operational documents derive from this.*

**Last updated:** [today's date]
**Author:** [Founder's name]
```

---

## Section: Mission

1-2 sentences. What the company does, who it serves, and the one thing it never is.
Should be memorable and specific enough to guide decisions.

Adapt to business type — a real estate flipper's mission is different from a SaaS
company's. No generic startup language. Use the founder's own words where possible.

---

## Section: 12-Month Goal

One concrete, measurable target derived from the interview. Include the revenue or
output figure and a statement about the founder's involvement level.

Examples by type:
- Real estate: "6–10 completed flips, $300K+ net profit, autonomous lead pipeline"
- Agency: "15 active retainer clients, $20K/month recurring, standardised delivery"
- SaaS: "$10K MRR, 500 paying users, self-serve onboarding"
- Service: "Fully booked 3 months ahead, $15K/month, first hire"

---

## Section: 3-Year Vision

Where the company is heading at scale. Extrapolate from the 12-month goal.
Include geographic expansion, team growth, revenue milestones, or platform ambitions
as relevant to the business type.

---

## Section: Revenue Model / How We Make Money

**Adapt completely to business type.** This is NOT always SaaS pricing tiers.

- Real estate: exit strategies table (flip / wholesale / BRRRR / rent-to-own),
  margin floors, capital structure, lender relationships
- Agency: service packages, retainer vs project pricing, upsell paths
- SaaS: pricing tiers, freemium model, enterprise deals
- Service: hourly vs fixed, retainer, package pricing

Bold the core value proposition. State what requires founder approval for pricing.
Note the live source of truth if pricing lives elsewhere.

---

## Section: Target Customer

**Primary:** One sentence defining the lead persona — who they are, what pain they
have, why they're the primary focus.

**Secondary:** Other valid customer types. Note they're in scope but messaging and
pipeline lead with the primary.

Adapt completely — a real estate company's "customer" might be distressed property
owners. An agency's might be local contractors. Don't force a SaaS persona onto
every business.

---

## Section: Growth Strategy / Lead Generation

State the budget first. Then list channels in priority order with approach notes.
Include restrictions and principles.

Shape this around the actual business. A real estate company's growth strategy is
a data pipeline + skip tracing + realtor handoff — not SEO + content marketing.
An agency might rely on referrals + portfolio + local networking.

---

## Section: Sales Model / Deal Flow

How a lead becomes a customer/deal. Describe the full pipeline from acquisition
through close. What does each step look like? Who owns it? Where are the handoffs?

---

## Section: Product / Service Direction

State the current state of what the company delivers. Then list the roadmap or
evolution path. Note what the CEO cannot change without founder involvement.

For service businesses, this is about service standardisation, SOPs, and delivery
quality. For product businesses, it's the product roadmap. For real estate, it's
the acquisition pipeline tooling and process.

---

## Section: Organisational Structure

Include an ASCII org chart showing the hierarchy. Always include:
- Founder at top
- CEO below Founder
- Chief of Staff below CEO
- Department heads below CoS — **shaped by the actual business pipeline**

**Critical: Do NOT default to generic Marketing/Sales/SEO heads.** Shape the org
around the company's value chain. Examples:
- Real estate: Head of Data Pipeline, Head of Enrichment, Head of Underwriting,
  Head of Deal Flow, Head of Airtable Ops, Head of Back-Office, Head of Cutting Edge
- Agency: Head of Client Delivery, Head of Design, Head of Web Dev,
  Head of Client Acquisition, Head of Project Management
- SaaS: Head of Engineering, Head of Marketing, Head of Customer Success

Include a paragraph on VISION.md propagation:
> Paperclip's native layout is per-agent. VISION.md lives in each agent's own
> `instructions/` directory. When the CEO hires a new agent, it copies VISION.md
> into the new agent's instructions dir and adds a "read VISION.md every heartbeat"
> directive to that agent's AGENTS.md. The CoS owns propagation hygiene.

---

## Section: Operating Philosophy

Always included regardless of founder's answers. Explain Research → Plan → Execute:

1. **Gate 1 — Research**: What it means, who does it, what output it produces
2. **Gate 2 — Plan**: What a plan must contain, who approves it, who holds it
3. **Gate 3 — Execute**: How execution is scheduled (CoS → master calendar)

Include one concrete example relevant to the founder's specific industry.

Additional principles as surfaced in the interview (deterministic over agentic,
DIY over SaaS, challenge "not now" assumptions, etc.) go here with explanation.

---

## Section: CEO Mandate

Three subsections:

**Autonomous — no founder approval needed**
List from Q11. Always append:
- "Commission and delegate research tasks to appropriate agents"
- "Hire and onboard the Chief of Staff agent"
- All items note they operate "within an approved plan" where relevant

**Requires Founder Approval — always, no exceptions**
List from Q12. Phrase as absolute. Always include "any external human contact"
and "any spending" unless the founder explicitly overrides.

**Reporting Cadence**
From Q13. Note reports are never skipped and include pipeline snapshots.

---

## Section: Guiding Principles

3-6 principles from Q16 and the overall interview. Each principle:
- Bold title
- 1-3 sentences explaining what it means in practice for THIS company
- Feels specific, not generic startup wisdom

Always include Research → Plan → Execute as one principle.

---

## Section: Risk Guardrails (if applicable)

If the interview surfaced specific risk factors (legal, financial, compliance,
regulatory), include them as constitutional guardrails the CEO re-reads every
heartbeat. Examples:
- Tax-deed redemption periods affecting deal timelines
- Licensing requirements
- Insurance minimums
- Compliance obligations

These belong in VISION because they're strategic constraints, not operational details.

---

## Section: What Success Looks Like

Three time horizons (3 months, 12 months, 3 years) drawn from the interview.
Keep concrete and measurable.
