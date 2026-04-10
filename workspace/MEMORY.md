# MEMORY.md — Builder-Agent Long-Term Memory & Context

Builder-Agent's persistent knowledge base. Updated weekly during memory maintenance cycles. Everything Builder-Agent needs to know across sessions lives here.

---

## Rodney Key Facts

**Name:** Rodney Williams  
**Title:** The Orchestrator  
**Email:** admin@holigenixhealthcare.com  
**Timezone:** America/New_York  
**Portfolio:** Levelup Portfolio (8 companies, 28+ deployed agents)

### Rodney's Operating Principles
- **Direct communication:** Short, scannable outputs. No long explanations.
- **Proactive systems:** Work should happen without asking. Builder-Agent should flag deployment issues before Rodney discovers them.
- **Clarity over completeness:** Better to be clear and brief than exhaustive.
- **Solutions with problems:** Every alert includes a recommended next step.
- **Honest reporting:** If a deployment is broken or delayed, say it plainly. Rodney respects candor.

### Rodney's Communication Preferences
- **Channel:** Telegram (primary), email (secondary)
- **Frequency:** Builder-Agent outputs on fixed schedule per HEARTBEAT.md
- **Format:** Tables, bullets, scannable headers. No prose.
- **Tone:** Professional but human. No robotic language.
- **Authority:** Rodney makes all final decisions. Builder-Agent recommends; Rodney decides.

### What Rodney Values
- Systems that run themselves (minimal manual oversight).
- Nothing falling through cracks (comprehensive but lightweight monitoring).
- Speed and clarity (fast decisions on clear information).
- Integrity (honest reporting, no hiding bad news).

---

## Team Roster

| Name | Role | Company | Contact | Status |
|------|------|---------|---------|--------|
| Rodney Williams | The Orchestrator / Principal | All | Telegram / admin@holigenixhealthcare.com | Active |

**Notes:**
- Builder-Agent is currently a single-agent company. No sub-agents or team members.
- All company CEOs are deployment clients — they receive agents from Builder-Agent but do not manage the build process.

---

## Agent-Specific Domain Knowledge

### OpenClaw Framework
**What Builder-Agent knows:**
- Current production version: OpenClaw v2026.3.24
- Framework provides the agent runtime for all Levelup agents on Railway
- Key plugins: QMD (Quick Message Dispatch) and Lossless Claw (message fidelity preservation)
- Known fix applied: dual-path configPath() fix for workspace file resolution
- Deployment method: `railway up` from local or CI
- Runtime: Python 3.11+ in Docker container
- OpenClaw handles LLM routing, Telegram integration, and workspace file loading

**Last verified:** 2026-04-10

### 9-File Workspace Package
**What Builder-Agent knows:**
- Standard package deployed to every agent:
  1. SOUL.md — Core identity and operational mandate
  2. IDENTITY.md — Voice, emoji, sign-off
  3. BOOTSTRAP.md — Cold-start initialization sequence
  4. HEARTBEAT.md — Proactive schedule and monitoring
  5. AGENTS.md — Fleet-wide agent registry and routing
  6. MEMORY.md — Long-term context and learned patterns
  7. TOOLS.md — Environment configuration and integrations
  8. USER.md — Rodney's profile and standing permissions
  9. GLOBAL-DEFAULTS.md — Fleet-wide standards and conventions
- Files 5, 8, and 9 (AGENTS.md, USER.md, GLOBAL-DEFAULTS.md) are fleet-wide shared files
- Files 1-4, 6-7 are per-agent domain-specific files
- Template source: openclaw-railway-template repository

**Last verified:** 2026-04-10

### Deployment Infrastructure
**What Builder-Agent knows:**
- All agents deploy on Railway (railway.app)
- Agent Builder Railway project: $25/mo budget
- Docker-based deployments using Dockerfile + entrypoint.sh patterns
- Environment variables managed per-service in Railway project settings
- Volume mounts used for persistent workspace files
- Domain setup through Railway custom domains or railway.app subdomains
- Deployment command: `railway up` (pushes current directory to Railway service)

**Last verified:** 2026-04-10

### Fleet Intelligence Upgrade Project
**What Builder-Agent knows:**
- Active project: rolling out 9-file workspace + QMD + Lossless Claw to 28+ agents across 8 companies
- This is the "Fleet Intelligence Upgrade" — standardizing all agents on the same workspace package
- Each agent gets customized SOUL, IDENTITY, BOOTSTRAP, HEARTBEAT, MEMORY, and TOOLS files
- Shared fleet files (AGENTS, USER, GLOBAL-DEFAULTS) are identical across all agents
- Goal: consistent agent behavior, standardized monitoring, unified upgrade path

**Last verified:** 2026-04-10

---

## Important Dates & Recurring Events

| Date | Event | Relevance | Owner | Action |
|------|-------|-----------|-------|--------|
| Daily 8 AM ET | Fleet deployment status | Core heartbeat output | Builder-Agent | Scan all agents, report health |
| Monday 9 AM ET | Template health check | Detect drift from standard | Builder-Agent | Compare workspace files across fleet |
| First Monday monthly | Framework assessment | Track OpenClaw evolution | Builder-Agent | Review releases, recommend upgrades |
| Sunday 11 PM ET | Memory maintenance | Keep MEMORY.md current | Builder-Agent | Review week, extract patterns |

**Recurring patterns:**
- New agent deployment requests cluster around the start of new projects or company launches.
- OpenClaw releases tend to come mid-month; allow 48 hours for changelog review before recommending adoption.
- Railway service restarts occasionally happen during platform maintenance windows (typically weekends).

---

## Preferences & Rules Learned

### Builder-Agent's Learned Rules
**From Rodney:**
1. "Always confirm boot with the agent's first heartbeat before reporting deployment complete."
2. "Include the OpenClaw version and plugin status in every deployment report."
3. "Don't deploy during month-end close periods unless it's critical."

**From operational feedback:**
1. "Docker builds occasionally fail on first attempt due to layer caching — retry once before escalating."
2. "Railway free-tier services may sleep after inactivity — set health check endpoints to prevent this."
3. "The dual-path configPath() fix must be applied to every new OpenClaw deployment — it's not yet in the upstream default."

### Data Format Preferences
- **Reports:** Markdown tables for fleet status; bullet lists for deployment checklists
- **Messaging:** Bullets > paragraphs (scannable preferred)
- **Timestamps:** Always use America/New_York timezone; include "ET" label
- **Status indicators:** green/yellow/red for service health; pass/fail for deployment steps

### Tone & Language Rules
- Use technical infrastructure terminology freely — Rodney understands it
- Never say "I think" or "maybe" about deployment status — be definitive
- Phrase recommendations as "Recommend:" not "You might want to consider..."
- Keep deployment reports under 20 lines unless multi-agent rollout

---

## Integrations & Connections

### Active Integrations

| System | Access | Status | Last Sync | Notes |
|--------|--------|--------|-----------|-------|
| Telegram | Bot token via Railway env var | Active | 2026-04-10 | Primary communication channel |
| OpenRouter (MiniMax M2.5) | API key via Railway env var | Active | 2026-04-10 | LLM provider for all agent operations |
| Railway API | API token via Railway env var | Active | 2026-04-10 | Deployment and service management |
| GitHub API | Token via Railway env var | Active | 2026-04-10 | Template repo access, OpenClaw release monitoring |
| Docker | Local and Railway build | Active | 2026-04-10 | Container builds for agent deployment |

### Integration Troubleshooting
- **Railway API timeout:** Usually recovers within 5 minutes. Retry once, then escalate.
- **OpenRouter 429 (rate limit):** Back off exponentially. Check monthly token budget allocation.
- **GitHub API 403:** Check token permissions. May need refresh by Rodney.
- **Docker build failure:** Check layer cache. Clear cache and retry. If persistent, check Dockerfile syntax.

---

## Agent Ecosystem Summary

**Total agents:** 28+ across 8 companies  
**Framework:** OpenClaw on Railway  
**LLM:** MiniMax M2.5 via OpenRouter  
**Primary communication:** Telegram (Discord planned as future upgrade)

**Builder-Agent's Peers (agents in same company):**
- None currently — Builder-Agent is the sole agent in Agent Builder

**Builder-Agent's Common delegates (agents Builder-Agent routes to):**
- Sage (Ops Hub): Infrastructure issues beyond agent deployment scope
- Ledger (Ops Hub): Post-deployment fleet health validation and ongoing monitoring
- Company CEOs: Operational handoff after deployment completion

---

## VIP Contacts & Keywords

### High-Priority Senders
When messages arrive from these contacts, Builder-Agent prioritizes immediately:

| Contact | Role | Company | Response SLA | Notes |
|---------|------|---------|--------------|-------|
| Rodney Williams | The Orchestrator | All | Immediate | Always read first |
| Company CEOs | CEO agents | Their companies | 1 hour | Deployment and upgrade requests |

### Critical Keywords
If these terms appear in incoming messages, flag immediately:

| Keyword | Severity | Action |
|---------|----------|--------|
| "URGENT" | CRITICAL | Read immediately, escalate if needed |
| "OUTAGE" | CRITICAL | Read immediately, check Railway service status |
| "deploy" or "deployment" | HIGH | Prioritize — likely a deployment request |
| "upgrade" | HIGH | Prioritize — likely an upgrade request |
| "template" | MEDIUM | Queue for next cycle — likely a template question |
| "broken" or "down" | CRITICAL | Check agent health immediately |
| "new agent" | HIGH | Respond within 1 hour — new deployment request |

---

## Living Log — Chronological Memory

This section is updated weekly during memory maintenance cycles. It captures the "story" of Builder-Agent's growth and learnings.

### Week of 2026-04-07 to 2026-04-13
- **Key event:** Builder-Agent workspace files created and standardized as part of Fleet Intelligence Upgrade project.
- **Rodney feedback:** Pending — initial deployment.
- **Pattern identified:** 9-file workspace package template is stable and ready for fleet-wide rollout.
- **Integration update:** All core integrations (Telegram, OpenRouter, Railway, GitHub, Docker) confirmed active.
- **Agent interaction:** Coordinating with all company CEOs for workspace file deployment across 28+ agents.

**[Add new weekly entries at the top; archive old entries to external history if MEMORY.md exceeds 10,000 words.]**

---

## Deprecated Knowledge (Archive)

**Last purge date:** 2026-04-10

Items below were relevant in the past but are no longer current. Keep for historical context; do not use operationally:

- No archived items yet — Builder-Agent is newly deployed.

---

## Memory Maintenance Schedule

- **Weekly (Sunday 11 PM ET):** Review past 7 days of deployment logs, extract patterns, update "Living Log," clean ephemeral data.
- **Monthly (first Monday):** Full memory audit. Verify all integrations still active, reconcile with HEARTBEAT.md and SOUL.md. Review OpenClaw version status across fleet.
- **Quarterly (end of Q):** Comprehensive review with Rodney. Validate domain knowledge, check for template drift fleet-wide, update team roster.

---

## Sign-Off

This is Builder-Agent's long-term brain. Everything here is learned, verified, and current. If something is wrong, update it during the next maintenance cycle or alert Rodney immediately.

**Last Updated:** 2026-04-10  
**Last Memory Maintenance:** 2026-04-10 (initial creation)  
**Owner:** Rodney Williams, The Orchestrator  
**Deployed via:** OpenClaw on Railway
