# GLOBAL-DEFAULTS.md — Levelup Ecosystem Constants
**Version:** 1.0 | **Owner:** Rodney Williams | **Last Updated:** April 2026

---

> This file contains the constants that apply to every agent built in this ecosystem.
> Read this file FIRST before building any agent workspace files.
> Do not hardcode these values anywhere else — always reference this file.

---

## 1. Owner Identity

| Field | Value |
|-------|-------|
| Name | Rodney Williams |
| Title | The Orchestrator |
| Timezone | America/New_York |
| Primary channel | Telegram |
| Role | Founder & Orchestrator — Levelup Portfolio |
| Email | admin@holigenixhealthcare.com |

---

## 2. The Levelup Portfolio — Companies

| Company | Code | Domain | Description | Monthly Cost |
|---------|------|--------|-------------|-------------|
| Holigenix | HGL | Healthcare | Georgia Medicaid and private-pay home health agency — clinical staff, credentials, nursing notes, care delivery | $55/mo |
| STR PM | STR | Short-Term Rentals | AI-driven workforce housing — contractor, insurance, and government long-term stays via Hospitable and PriceLabs | $55/mo |
| DVTOL Systems | DVT | SaaS Platform | Platform with 4+ production services — multi-service architecture | $30/mo |
| Ad Whisperer | AD | Advertising | AI creative studio producing ad copy and campaigns for Meta and Google Ads | $55/mo |
| Ops Hub | OPS | Infrastructure | n8n workflows, Railway service monitoring, and all automation pipelines | $25/mo |
| GeniusPrompts | GEN | Products | Prompt engineering product — creating and marketing high-quality prompt packs | $25/mo |
| Personal Ops | PER | Personal | Rodney's personal operations — calendar, tasks, research, cross-project coordination | $25/mo |
| Agent Builder | AGE | Meta | Research, prototype, and deploy new AI agents — expanding the agent workforce | $25/mo |
| GrantIQ | GRA | Grant Research | AI grant research and application system — finds, drafts, and submits grant applications for Holigenix, K1, etc. | $60/mo |
| K1 Contracting | K1 | Government Contracting | K1Management LLC — government contracting intelligence, proposals, and compliance for minority-owned federal ops | $30/mo |

**Total fleet cost:** $285/mo

---

## 3. GitHub

| Field | Value |
|-------|-------|
| GitHub owner | `SR2022RS` |
| Primary repos | See Section 8 — Agent Registry for per-agent repos |
| Agent workspace convention | `agents/[agent-name]/` within each repo |

---

## 4. Railway Projects

| Project | Companies/Agents |
|---------|-----------------|
| Holigenix | Ava, CareOps, OnboardBot, Growth Engine, CarePortal-Dev |
| STR PM | STR-Ops, Rex, CrewIQ, RateBrain, Pen, Scout, GuestSync, Watchtower, STR-Dev |
| DVTOL Systems | Vance, Bridge, Echo, Nova, DVTOL-Dev |
| Ad Whisperer | Maestro, Scout, Quill, Canvas, Trader, Sentinel, Beacon |
| Ad Whisperer Creative Service | Creative-Agent (separate Railway project with Postgres) |
| Ops Hub | Sage, Arlo, Ledger |
| GeniusPrompts | Content-Agent |
| Personal Ops | Aria |
| Agent Builder | Builder-Agent |
| GrantIQ | Director, Finder, Writer, Analyst, Tracker, Monitor, Reporter, Vault, BudgetGen, Applicator |
| K1 Contracting | K1 Portal |

**Default project for new agents:** Ops Hub unless told otherwise.

---

## 5. OpenClaw Deployment

| Field | Value |
|-------|-------|
| Workspace dir | `/data/workspace` |
| State dir | `/data/.openclaw` |
| Default auth provider | OpenRouter |
| Deploy file endpoint | `POST /api/deploy-file` |
| Setup trigger endpoint | `POST /setup/api/run` |
| Health check endpoint | `GET /setup/api/debug` |

---

## 6. LLM Configuration

| Field | Value |
|-------|-------|
| Default agent LLM | MiniMax M2.5 via OpenRouter |
| OpenRouter model string | `minimax/MiniMax-M2.5` |
| Auth method | `openrouter-api-key` |
| API key env var | `OPENROUTER_API_KEY` |
| Design tool | Claude (used to write workspace files) |
| Runtime tool | MiniMax M2.5 (runs the deployed agents) |

---

## 7. Standard Agent File Package

Every agent gets exactly these 9 files:

| File | Purpose |
|------|---------|
| `SOUL.md` | Role, responsibilities, thinking framework, boundaries |
| `IDENTITY.md` | Name, voice, presentation style |
| `USER.md` | Rodney's profile and preferences |
| `MEMORY.md` | Permanent knowledge base |
| `HEARTBEAT.md` | Proactive check schedule |
| `BOOTSTRAP.md` | Session startup identity anchor |
| `TOOLS.md` | Integration configuration |
| `AGENTS.md` | Agent ecosystem routing map |
| `[AGENT-NAME]_PRD.md` | Full product requirements document |

---

## 8. Agent Registry — Full Roster (44 Agents / 10 Companies)

### Holigenix (HGL) — Healthcare — 5 Agents

| Agent | Role | Type | Reports To | Status |
|-------|------|------|-----------|--------|
| **Ava** | Operations Lead (CEO) | Webhook | Rodney | Live |
| CareOps | Clinical Operations | Webhook | Ava | Live |
| OnboardBot | Caregiver Onboarding | Webhook | Ava | Live |
| Growth Engine | Patient Acquisition & Referrals | Webhook | Ava | Live |
| CarePortal-Dev | Engineering (CarePortal App) | Local | Ava | Live |

### STR PM (STR) — Workforce Housing — 9 Agents

| Agent | Role | Type | Reports To | Status |
|-------|------|------|-----------|--------|
| **STR-Ops** | Operations Lead (CEO) | Webhook | Rodney | Live |
| Rex | Telegram Bot / Direct Line | Webhook | STR-Ops | Live |
| CrewIQ | Voice AI / Inbound Calls | Webhook | STR-Ops | Live |
| RateBrain | Pricing Intelligence | Webhook | STR-Ops | Live |
| Pen | Content & Marketing | Webhook | STR-Ops | Live |
| Scout | Property Scouting | Webhook | STR-Ops | Live |
| GuestSync | Guest Communications & Sync | Webhook | STR-Ops | Live |
| Watchtower | Monitoring & Alerts | Webhook | STR-Ops | Live |
| STR-Dev | Engineering | Local (Engineer) | STR-Ops | Live |

### DVTOL Systems (DVT) — SaaS Platform — 5 Agents

| Agent | Role | Type | Reports To | Status |
|-------|------|------|-----------|--------|
| **Vance** | Platform Orchestrator (CEO) | Webhook | Rodney | Live |
| Bridge | Operations / Service Health | Webhook | Vance | Live |
| Echo | Communications / Notifications | Webhook | Vance | Live |
| Nova | Pipeline Monitor / CI-CD | Webhook (Engineer) | Vance | Live |
| DVTOL-Dev | Engineering (Local) | Local | Vance | Live |

### Ad Whisperer (AD) — Digital Advertising — 8 Agents

| Agent | Role | Type | Reports To | Status |
|-------|------|------|-----------|--------|
| **Maestro** | Creative Director (CEO) | Webhook | Rodney | Live |
| Scout | Research & Targeting | Webhook | Maestro | Live |
| Quill | Copywriting | Webhook | Maestro | Live |
| Canvas | Visual Creative | Webhook | Maestro | Live |
| Trader | Media Buying & Performance | Webhook | Maestro | Live |
| Sentinel | Compliance & QA | Webhook | Maestro | Live |
| Beacon | Analytics & Reporting | Webhook | Maestro | Live |
| Creative-Agent | Production Engine (Engineer) | Webhook | Maestro | Live |

### Ops Hub (OPS) — Infrastructure — 3 Agents

| Agent | Role | Type | Reports To | Status |
|-------|------|------|-----------|--------|
| **Sage** | Chief of Staff / Orchestrator (CEO) | Webhook | Rodney | Live |
| Arlo | ClientTrack / Project Status | Webhook | Sage | Live |
| Ledger | Fleet Optimizer / Spend Monitor | Webhook | Sage | Live |

### GeniusPrompts (GEN) — Products — 1 Agent

| Agent | Role | Type | Reports To | Status |
|-------|------|------|-----------|--------|
| **Content-Agent** | Product Lead (CEO) | Webhook | Rodney | Live |

### Personal Ops (PER) — 1 Agent

| Agent | Role | Type | Reports To | Status |
|-------|------|------|-----------|--------|
| **Aria** | Personal Chief of Staff (CEO) | Webhook | Rodney | Live |

### Agent Builder (AGE) — Meta — 1 Agent

| Agent | Role | Type | Reports To | Status |
|-------|------|------|-----------|--------|
| **Builder-Agent** | Agent Architect (CEO) | Webhook | Rodney | Live |

### GrantIQ (GRA) — Grant Research & Applications — 10 Agents

| Agent | Role | Type | Reports To | Status |
|-------|------|------|-----------|--------|
| **Director** | Grant Operations Lead (CEO) | Webhook | Rodney | Live |
| Finder | Grant Discovery & Search | Webhook | Director | Live |
| Writer | Grant Proposal Writing | Webhook | Director | Live |
| Analyst | Grant Data Analysis | Webhook | Director | Live |
| Tracker | Application Status Tracking | Webhook | Director | Live |
| Monitor | Compliance & Deadline Monitoring | Webhook | Director | Live |
| Reporter | Reporting & Dashboards | Webhook | Director | Live |
| Vault | Document Storage & Retrieval | Webhook | Director | Live |
| BudgetGen | Budget Generation & Modeling | Webhook | Director | Live |
| Applicator | Application Submission Engine | Webhook | Director | Live |

### K1 Contracting (K1) — Government Contracting — 1 Agent

| Agent | Role | Type | Reports To | Status |
|-------|------|------|-----------|--------|
| **K1 Portal** | Contracting Operations (CEO) | Webhook | Rodney | Live |

### Fleet Summary

| Metric | Count |
|--------|-------|
| Total companies | 10 |
| Total agents | 44 |
| Live webhook agents | 40 |
| Local agents | 4 (CarePortal-Dev, STR-Dev, DVTOL-Dev, Content-Agent) |
| CEO-tier agents | 10 (Ava, STR-Ops, Vance, Maestro, Sage, Content-Agent, Aria, Builder-Agent, Director, K1 Portal) |
| Monthly fleet cost | $285 |

---

## 9. Naming Convention

**Naming rule:** Agent names are short, memorable, and distinct. CEO agents get human names (Ava, Vance, Sage, Aria). Functional agents get descriptive names (CareOps, OnboardBot, Growth Engine).

---

## 10. Communication Rules

- **Primary channel:** Telegram (all agents currently deliver via Telegram)
- **Future command center:** Discord (migration planned)
- **Never hardcode team member names in agent files** — use role-based references only
- Names belong in the **Team Roster table in MEMORY.md** as the single source of truth
- **Never expose raw tool names, API errors, or system internals to Rodney**
- **Never start messages with "I have retrieved the following information"**

---

## 11. Key Principles

- **Every Railway redeploy resets Telegram pairing** — re-approval at `/setup` is required each time
- **OpenClaw files are ephemeral** — always upload workspace files after deployment, never assume they persist
- **Composio env var is `COMPOSIO_API_KEY`** — exact name required
- **Test each agent individually before connecting them** — stage-gate protocol
- **If it's not written down, it didn't happen** — mental notes do not survive session resets

---

## 12. OpenRouter Key Assignments

| Key Label | Assigned To |
|-----------|-------------|
| Holigenix_Clawbot | Holigenix agents |
| Care Ops | Holigenix CareOps |
| STR PM Openclaw | STR PM agents |
| DVTOL | DVTOL Systems agents |
| OpenClaw_bot | Ops Hub agents |
| Agent Builder | Builder-Agent |
| Summit Build | Builder-Agent (secondary) |

---

*GLOBAL-DEFAULTS.md v1.0 | Levelup Ecosystem | Read this first before building anything.*
*Update this file when projects, agents, or ecosystem constants change.*
