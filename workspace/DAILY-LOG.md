# DAILY-LOG.md —  Daily Journal

Raw, real-time record of everything that happens during 's operational day. This is the unfiltered journal — messy, detailed, and complete. Important insights get promoted to MEMORY.md during weekly maintenance. Mistakes get promoted to LESSONS.md immediately.

---

## How This File Works

**New entry every day.** Each day gets its own section at the top of this file (newest first). Entries older than 14 days get archived to `/workspace/memory/daily-logs/` as individual files (e.g., `2026-04-11.md`).

**Write in real time.** Don't wait until end of day. Log events as they happen — decisions, tasks, errors, conversations, escalations, everything.

**Read on boot.** Every session,  reads today's log and the previous two days' logs. This gives continuity across sessions and context compaction.

**Promote, don't duplicate.** When weekly memory maintenance runs (Sunday 11 PM ET per HEARTBEAT.md), review the past 7 days of daily logs:
- **Insights worth keeping 3+ weeks** → promote to MEMORY.md
- **Mistakes with permanent fixes** → promote to LESSONS.md immediately (don't wait for weekly cycle)
- **One-time events** → leave in daily log, let them age out to archive

---

## Log Format

Each entry follows this structure:

```
## [YYYY-MM-DD] — [Day of Week]

### Session [N] — [Start Time ET]

**Tasks Completed:**
- [What was done, for whom, outcome]

**Decisions Made:**
- [Decision] — [Why this option was chosen over alternatives]

**Rodney Interactions:**
- [What Rodney asked / instructed / corrected]
- [Key takeaway from the interaction]

**Escalations & Delegations:**
- [What was escalated, to whom, why, current status]

**Errors & Issues:**
- [What broke, root cause, how it was fixed]
- [If this should be a lesson → flag for LESSONS.md]

**Observations:**
- [Patterns noticed, anomalies detected, things that seem off]

**Context Compaction Notes:**
- [If compaction happened this session, what was the pre-compaction context about?]
- [Key items that might have been lost — re-anchor them here]

---
```

---

## Active Log

## [DATE] — [Day]

### Session 1 — [Time ET]

**Tasks Completed:**
- [Awaiting first entry]

**Decisions Made:**
- [None yet]

**Rodney Interactions:**
- [None yet]

**Escalations & Delegations:**
- [None yet]

**Errors & Issues:**
- [None yet]

**Observations:**
- Agent deployed with 9-file workspace package + DAILY-LOG.md + LESSONS.md
- Fleet Intelligence Upgrade v2 (Ledger-First architecture)
- First operational day — baseline entry

**Context Compaction Notes:**
- No compaction yet this session

---

## Archival Rules

1. **Daily logs older than 14 days** get moved to `/workspace/memory/daily-logs/YYYY-MM-DD.md`
2. **Never delete a daily log** — archive it. QMD can search archived logs.
3. **Monthly cleanup** (first Monday): verify archive integrity, confirm QMD indexes archived files.
4. **If DAILY-LOG.md exceeds 15,000 words**: immediately archive the oldest entries, don't wait for the 14-day window.

---

## Why This File Exists

Without daily logs,  has no raw material to learn from. MEMORY.md is curated wisdom. LESSONS.md is mistake prevention. But daily logs are the source of truth — the unfiltered record that feeds both.

**The rule:** If you don't write it down, it didn't happen. Mental notes do not survive context compaction. Every session, every decision, every error — log it here in real time.

---

**Last Updated:** [Date]  
**Owner:** Rodney Williams, The Orchestrator  
**Deployed via:** OpenClaw on Railway
