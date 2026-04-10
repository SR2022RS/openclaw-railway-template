# AGENTS.md — Levelup Agent Ecosystem Registry & Routing

The complete map of all 44 agents in the Levelup Portfolio across 10 companies. Use this to understand who does what, how to route work, and when to delegate.

---

## How Builder-Agent Routes Work

Builder-Agent receives requests and determines:
1. **Scope Check:** Is this within Builder-Agent's defined domain (see SOUL.md)?
2. **Capability Check:** Does Builder-Agent have the tools or access to complete it?
3. **Route Decision:** If yes, execute. If no, delegate to the appropriate agent.
4. **Escalation:** If unclear, escalate to Rodney. Never guess.

**Principle:** Route early, route clearly, always include context.

---

## Fleet Summary

| Metric | Count |
|--------|-------|
| Total companies | 10 |
| Total agents | 44 |
| Live webhook agents | 40 |
| Local agents | 4 (CarePortal-Dev, STR-Dev, DVTOL-Dev, Content-Agent) |
| CEO-tier agents | 10 |
| Monthly fleet cost | $285 |

---

## Agent Registry — All 44 Agents

### Holigenix (HGL) — Healthcare — CEO: Ava — 5 Agents

| Agent | Emoji | Role | Domain | Type | Reports To | Status |
|-------|-------|------|--------|------|-----------|--------|
| **Ava** | 🏥 | CEO, Healthcare Leadership | Company strategy, revenue oversight, compliance | Webhook | Rodney | Active |
| CareOps | 📋 | Clinical Operations | Daily ops, staff scheduling, nursing notes, care delivery | Webhook | Ava | Active |
| OnboardBot | 📝 | Caregiver Onboarding | New hire processing, credentials, orientation | Webhook | Ava | Active |
| Growth Engine | 📈 | Patient Acquisition & Referrals | Marketing, referral pipelines, census growth | Webhook | Ava | Active |
| CarePortal-Dev | 💻 | Engineering | CarePortal app development, bug fixes, features | Local | Ava | Active |

### STR PM (STR) — Workforce Housing — CEO: STR-Ops — 9 Agents

| Agent | Emoji | Role | Domain | Type | Reports To | Status |
|-------|-------|------|--------|------|-----------|--------|
| **STR-Ops** | 🏘️ | CEO, Housing Operations | Portfolio strategy, investor relations, property development | Webhook | Rodney | Active |
| Rex | 🤖 | Telegram Bot / Direct Line | Conversational interface, guest queries, quick actions | Webhook | STR-Ops | Active |
| CrewIQ | 📞 | Voice AI / Inbound Calls | Call handling, lead qualification, crew scheduling | Webhook | STR-Ops | Active |
| RateBrain | 💰 | Pricing Intelligence | Dynamic pricing via PriceLabs, rate optimization, comp analysis | Webhook | STR-Ops | Active |
| Pen | ✍️ | Content & Marketing | Listing copy, marketing materials, SEO content | Webhook | STR-Ops | Active |
| Scout | 🔍 | Property Scouting | Market research, deal analysis, new property identification | Webhook | STR-Ops | Active |
| GuestSync | 🔄 | Guest Communications & Sync | Guest messaging, booking sync via Hospitable, review management | Webhook | STR-Ops | Active |
| Watchtower | 👁️ | Monitoring & Alerts | Property monitoring, security alerts, maintenance flags | Webhook | STR-Ops | Active |
| STR-Dev | 💻 | Engineering | STR platform development, integrations, automation | Local | STR-Ops | Active |

### DVTOL Systems (DVT) — SaaS Platform — CEO: Vance — 5 Agents

| Agent | Emoji | Role | Domain | Type | Reports To | Status |
|-------|-------|------|--------|------|-----------|--------|
| **Vance** | 🚀 | CEO, Platform Orchestrator | Product roadmap, customer strategy, revenue, multi-service architecture | Webhook | Rodney | Active |
| Bridge | 🌉 | Operations / Service Health | System uptime, service health, operational coordination | Webhook | Vance | Active |
| Echo | 📡 | Communications / Notifications | User notifications, system alerts, external comms | Webhook | Vance | Active |
| Nova | ⚙️ | Pipeline Monitor / CI-CD | Build pipelines, deployment automation, infrastructure | Webhook | Vance | Active |
| DVTOL-Dev | 💻 | Engineering (Local) | Platform development, bug fixes, feature engineering | Local | Vance | Active |

### Ad Whisperer (AD) — Digital Advertising — CEO: Maestro — 8 Agents

| Agent | Emoji | Role | Domain | Type | Reports To | Status |
|-------|-------|------|--------|------|-----------|--------|
| **Maestro** | 🎭 | CEO, Creative Director | Campaign strategy, creative direction, team orchestration | Webhook | Rodney | Active |
| Scout | 🔍 | Research & Targeting | Audience research, targeting strategy, competitor analysis | Webhook | Maestro | Active |
| Quill | ✒️ | Copywriting | Ad copy, headlines, CTAs, landing page text | Webhook | Maestro | Active |
| Canvas | 🎨 | Visual Creative | Ad visuals, design briefs, creative assets | Webhook | Maestro | Active |
| Trader | 📊 | Media Buying & Performance | Ad spend management, bid optimization, ROAS tracking | Webhook | Maestro | Active |
| Sentinel | 🛡️ | Compliance & QA | Ad policy compliance, quality checks, brand safety | Webhook | Maestro | Active |
| Beacon | 📡 | Analytics & Reporting | Campaign analytics, performance dashboards, insights | Webhook | Maestro | Active |
| Creative-Agent | 🎬 | Production Engine | Creative production pipeline, asset generation, rendering | Webhook | Maestro | Active |

### Ops Hub (OPS) — Infrastructure — CEO: Sage — 3 Agents

| Agent | Emoji | Role | Domain | Type | Reports To | Status |
|-------|-------|------|--------|------|-----------|--------|
| **Sage** | 🧠 | CEO, Chief of Staff | Systems architecture, vendor management, n8n workflows, automation | Webhook | Rodney | Active |
| Arlo | 📋 | ClientTrack / Project Status | Project tracking, client status updates, task coordination | Webhook | Sage | Active |
| Ledger | 📒 | Fleet Optimizer / Spend Monitor | Railway spend tracking, fleet health, cost optimization | Webhook | Sage | Active |

### GeniusPrompts (GEN) — Products — CEO: Content-Agent — 1 Agent

| Agent | Emoji | Role | Domain | Type | Reports To | Status |
|-------|-------|------|--------|------|-----------|--------|
| **Content-Agent** | ✍️ | CEO, Product Lead | Prompt library curation, quality, distribution, marketing | Webhook | Rodney | Active |

### Personal Ops (PER) — CEO: Aria — 1 Agent

| Agent | Emoji | Role | Domain | Type | Reports To | Status |
|-------|-------|------|--------|------|-----------|--------|
| **Aria** | 🌟 | CEO, Personal Chief of Staff | Calendar, priorities, research, cross-project coordination | Webhook | Rodney | Active |

### Agent Builder (AGE) — Meta — CEO: Builder-Agent — 1 Agent

| Agent | Emoji | Role | Domain | Type | Reports To | Status |
|-------|-------|------|--------|------|-----------|--------|
| **Builder-Agent** | 🏗️ | CEO, Agent Architect | Framework research, templates, deployment, fleet upgrades | Webhook | Rodney | Active |

### GrantIQ (GRA) — Grant Research & Applications — CEO: Director — 10 Agents

| Agent | Emoji | Role | Domain | Type | Reports To | Status |
|-------|-------|------|--------|------|-----------|--------|
| **Director** | 🎯 | CEO, Grant Operations Lead | Grant strategy, pipeline oversight, team coordination | Webhook | Rodney | Active |
| Finder | 🔎 | Grant Discovery & Search | Finding matching grants, eligibility screening, opportunity alerts | Webhook | Director | Active |
| Writer | 📝 | Grant Proposal Writing | Drafting proposals, narratives, supporting documents | Webhook | Director | Active |
| Analyst | 📊 | Grant Data Analysis | Data gathering, impact metrics, statistical support | Webhook | Director | Active |
| Tracker | 📍 | Application Status Tracking | Submission tracking, deadline management, status updates | Webhook | Director | Active |
| Monitor | 👁️ | Compliance & Deadline Monitoring | Compliance checks, reporting deadlines, regulatory requirements | Webhook | Director | Active |
| Reporter | 📰 | Reporting & Dashboards | Grant performance reports, dashboards, stakeholder updates | Webhook | Director | Active |
| Vault | 🔐 | Document Storage & Retrieval | Document management, version control, secure storage | Webhook | Director | Active |
| BudgetGen | 💵 | Budget Generation & Modeling | Grant budgets, cost models, financial projections | Webhook | Director | Active |
| Applicator | 📤 | Application Submission Engine | Form filling, submission automation, portal management | Webhook | Director | Active |

### K1 Contracting (K1) — Government Contracting — CEO: K1 Portal — 1 Agent

| Agent | Emoji | Role | Domain | Type | Reports To | Status |
|-------|-------|------|--------|------|-----------|--------|
| **K1 Portal** | 🏛️ | CEO, Contracting Operations | Government contracting intelligence, proposals, compliance | Webhook | Rodney | Active |

---

## CEO Quick Reference

All CEO agents report directly to Rodney. Use this table for fast routing:

| Company | CEO Agent | Domain | Fast Route |
|---------|-----------|--------|------------|
| Holigenix | Ava | Healthcare | Clinical ops, onboarding, patient growth |
| STR PM | STR-Ops | Housing | Properties, pricing, guests, crews |
| DVTOL Systems | Vance | SaaS | Platform, deployments, service health |
| Ad Whisperer | Maestro | Advertising | Campaigns, creative, media buying |
| Ops Hub | Sage | Infrastructure | Workflows, monitoring, automation |
| GeniusPrompts | Content-Agent | Products | Prompts, content, distribution |
| Personal Ops | Aria | Personal | Calendar, tasks, research |
| Agent Builder | Builder-Agent | Meta | Agent framework, fleet upgrades |
| GrantIQ | Director | Grants | Discovery, proposals, submissions |
| K1 Contracting | K1 Portal | Gov Contracting | Federal proposals, compliance |

**Rule:** If you don't know where to route, route to the CEO of the most relevant company. If still unclear, escalate to Rodney.

---

## This Agent's Routing Rules

Builder-Agent delegates to other agents according to these rules:

| Condition | Route To | Priority | Notes |
|-----------|----------|----------|-------|
| Healthcare operations question | Ava → CareOps | NORMAL | Ava's team owns all clinical ops |
| Pricing or rate question (STR) | STR-Ops → RateBrain | NORMAL | RateBrain owns PriceLabs integration |
| Ad campaign request | Maestro | HIGH | Maestro coordinates the full Ad Whisperer team |
| Infrastructure / Railway issue | Sage | HIGH | Sage owns all automation and Railway monitoring |
| Grant opportunity or application | Director | NORMAL | Director coordinates the full GrantIQ team |
| Fleet health or spend question | Sage → Ledger | NORMAL | Ledger tracks Railway spend and fleet optimization |
| Cross-company or ambiguous | Rodney | CRITICAL | Always escalate ambiguity to The Orchestrator |

**Default:** If not in this table, escalate to Rodney.

---

## Standard Delegation Packet Format

When Builder-Agent delegates work to another agent, include this structure:

```
TO: Builder-Agent
FROM: Builder-Agent
PRIORITY: [CRITICAL / HIGH / NORMAL / LOW]
DELEGATION ID: [Unique ID for tracking]

TASK:
[Clear one-sentence summary of what is needed]

CONTEXT:
[2-3 sentences explaining why and relevant background]

REQUIRED OUTPUT:
[Specific format expected, e.g., "CSV file with columns X, Y, Z"]

DEADLINE:
[Specific time or "ASAP"]

RODNEY CONTEXT:
[Any special notes Rodney has given about this task]

---
Builder-Agent
```

**Receiving Agent Acknowledgment:**
The receiving agent responds immediately with:
```
ACKNOWLEDGED: [Delegation ID]
ETA: [Time to completion]
Builder-Agent
```

---

## Inter-Agent Communication Protocol

1. **Direct delegation:** Use the packet format above.
2. **Questions:** Route through Rodney if the delegating agent cannot clarify.
3. **Status updates:** Originating agent may request status during long-running tasks.
4. **Escalation:** If the delegated agent encounters a blocker, escalate immediately with full context.
5. **Handoff:** Always confirm completion and mark delegation as closed.

---

## Cross-Company Delegation Patterns

| Scenario | Primary | Supporting | Notes |
|----------|---------|------------|-------|
| Holigenix grant application | Director (GrantIQ) | Ava (Holigenix) | GrantIQ writes, Holigenix provides data |
| Ad campaign for Holigenix | Maestro (Ad Whisperer) | Ava (Holigenix) | Ad Whisperer runs creative, Holigenix provides clinical context |
| K1 grant opportunity | Director (GrantIQ) | K1 Portal (K1) | GrantIQ writes, K1 provides contracting context |
| Fleet-wide deployment | Builder-Agent | Sage (Ops Hub) | Builder-Agent deploys, Sage monitors health |
| New agent onboarding | Builder-Agent | [Company CEO] | Builder-Agent builds, CEO provides domain context |

**Always involve Rodney if unsure who owns cross-company responsibility.**

---

## Emergency Escalation Path

If a critical issue impacts multiple companies:

1. Detect issue (any agent).
2. Alert Rodney immediately with severity [CRITICAL].
3. Route context to all affected company CEOs.
4. Sage (Ops Hub) takes lead on infrastructure/system issues.
5. Rodney makes final decisions on priorities and resource allocation.

---

## Agent Status Legend

| Status | Meaning | Action |
|--------|---------|--------|
| Active | Fully operational, ready to receive work | Route normally |
| Staging | In testing, not yet production-ready | Route only with Rodney approval |
| Paused | Temporarily offline (maintenance, debugging) | Do not route; escalate to Rodney |
| Deprecated | No longer in use; replaced by newer agent | Do not route; escalate to Rodney |
| On-Call | Available but not primary | Route secondary requests only |

---

## Quarterly Registry Review

This registry is accurate as of April 2026. Builder-Agent should verify current status quarterly:
- New agents added?
- Status changes (Active → Paused, etc.)?
- Telegram handles updated?
- Routing rules changed?

**Update trigger:** If AGENTS.md is more than 90 days old, alert Rodney to review.

---

## Sign-Off

This registry is the source of truth for agent identity and routing. Keep it synchronized with deployments. Any agent not listed here does not exist in the Levelup ecosystem.

**Last Updated:** April 2026
**Maintained by:** Builder-Agent or designated registry owner
**Owner:** Rodney Williams, The Orchestrator
**Ecosystem Size:** 44 agents across 10 companies
