# LESSONS.md —  Mistake Log & Permanent Fixes

Every mistake gets logged here once. What happened, why it happened, and the permanent fix so it never repeats. This file is read every session — it is how  compounds knowledge and stops making the same errors.

---

## How This File Works

**Log immediately.** When a mistake happens, don't wait for the weekly memory cycle. Add it to LESSONS.md right away while the context is fresh.

**Read every session.**  reads this file on boot, after SOUL.md and before starting any work. These are permanent operating rules.

**Never delete lessons.** Lessons compound. A file with 50+ lessons is a feature, not a problem. The more lessons, the smarter the agent.

**Promote from DAILY-LOG.md.** During daily operations, flag errors in the daily log. If the error has a clear root cause and permanent fix, promote it to LESSONS.md immediately. If the root cause is unclear, investigate first, then log the lesson once you understand it.

**Format matters.** Every lesson must have all three parts: what happened, why, and the fix. A lesson without a fix is just a complaint.

---

## Lesson Format

```
### Lesson [N]: [Short title]
**Date learned:** [YYYY-MM-DD]
**Severity:** [CRITICAL / HIGH / MEDIUM / LOW]
**Category:** [Operations / Communication / Technical / Decision-Making / Delegation / Data]

**What happened:**
[Factual description of the mistake or failure — what went wrong]

**Why it happened:**
[Root cause analysis — not symptoms, but the actual underlying reason]

**Permanent fix:**
[The rule or behavior change that prevents this from ever happening again]

**Verification:**
[How to confirm the fix is working — what to check]
```

---

## Active Lessons

### Lesson 1: [First lesson title]
**Date learned:** [Date]
**Severity:** [Level]
**Category:** [Category]

**What happened:**
[Awaiting first entry — this section will grow over time as  operates and encounters real situations]

**Why it happened:**
[Root cause]

**Permanent fix:**
[Rule to follow going forward]

**Verification:**
[How to confirm]

---

## Lesson Categories Reference

Use these categories to organize lessons for quick scanning:

| Category | What It Covers | Example |
|----------|---------------|---------|
| **Operations** | Task execution failures, missed deadlines, process gaps | "Always update docs and scripts at the same time, not sequentially" |
| **Communication** | Misunderstandings with Rodney, unclear outputs, bad formatting | "Never send raw data without a summary headline" |
| **Technical** | API failures, integration errors, deployment issues | "When action fails after consuming inputs, undo the consumption so system can retry" |
| **Decision-Making** | Wrong judgment calls, missed trade-offs, bad prioritization | "Before building anything, map the entire flow end-to-end and present gaps before writing code" |
| **Delegation** | Routing to wrong agent, unclear handoffs, dropped tasks | "Always include full context packet when delegating — never assume the receiving agent has background" |
| **Data** | Incorrect metrics, stale data, wrong sources, calculation errors | "Always verify data freshness before including in reports — check timestamp, not just availability" |

---

## Lesson Review Schedule

- **Every session (boot):** Read all lessons. These are permanent operating rules.
- **Weekly (Sunday 11 PM ET):** Review daily logs for new lessons. Promote any errors with clear root causes.
- **Monthly (first Monday):** Review all lessons for relevance. Mark any that are no longer applicable as `[SUPERSEDED]` with reason, but do not delete.
- **Quarterly:** Report to Rodney: total lessons, most common category, any patterns that suggest systemic issues.

---

## Metrics

Track these to measure learning velocity:

| Metric | Value |
|--------|-------|
| Total lessons logged | 0 |
| Lessons this week | 0 |
| Most common category | — |
| Last lesson added | — |
| Repeat violations (lesson existed but was ignored) | 0 |

**Target:** Zero repeat violations. If a lesson exists and the same mistake happens again, that's a CRITICAL issue — escalate to Rodney with root cause.

---

## Why This File Exists

The video creator who pioneered this approach logged 51 lessons in 3 weeks. Each one prevents a specific failure from ever repeating. Without this file, agents make the same mistakes over and over because context compaction wipes the memory of what went wrong.

With LESSONS.md, every mistake becomes a permanent upgrade. The agent that has 50 lessons is 50 mistakes smarter than the one with zero. This is how agents compound knowledge over time instead of resetting to baseline every session.

**The rule:** Every mistake is a lesson. Every lesson has a fix. Every fix is permanent. No exceptions.

---

**Last Updated:** [Date]  
**Owner:** Rodney Williams, The Orchestrator  
**Deployed via:** OpenClaw on Railway
