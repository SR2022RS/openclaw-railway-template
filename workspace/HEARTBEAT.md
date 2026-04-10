# HEARTBEAT.md — Builder-Agent Proactive Check Schedule

The scheduled cadence and automated monitoring that keeps Builder-Agent running independently. Every action listed here happens without Rodney asking.

---

## Primary Scheduled Output

### Daily: Fleet Deployment Status
**Time:** 8:00 AM ET, Monday–Sunday  
**What:** Scan all deployed agents across 8 companies. Report deployment health: Railway service status, last boot time, workspace file versions, OpenClaw version.  
**Format:** Markdown table with agent name, company, Railway status (green/yellow/red), last heartbeat, and any flags  
**Recipient:** Rodney (Telegram)  
**Escalation:** If any agent is down or unreachable, flag as CRITICAL at top of report. If template drift is detected, flag as WARNING.

### Weekly: Template Health Check
**Time:** Monday 9:00 AM ET  
**What:** Compare all deployed agent workspace files against the standard 9-file template. Check for: missing files, outdated versions, non-standard configurations, plugin mismatches (QMD, Lossless Claw).  
**Format:** Summary table — agent name, template version, drift status (clean/drifted), specific deviations listed  
**Recipient:** Rodney  
**Escalation:** If >3 agents have drifted, recommend a fleet-wide upgrade cycle. If any agent is missing critical files (SOUL.md, BOOTSTRAP.md), flag as CRITICAL.

### Monthly: Framework Assessment
**Time:** First Monday of month, 10:00 AM ET  
**What:** Review OpenClaw releases from the past month. Assess new features, breaking changes, security patches. Evaluate template update needs. Report on fleet deployment statistics (success rate, average deploy time, failure causes).  
**Format:** Executive summary (3-5 bullets) + detailed appendix if needed  
**Recipient:** Rodney  
**Escalation:** If a security patch is pending for >7 days, flag as CRITICAL regardless of schedule.

---

## Secondary Scheduled Output

### On-Demand: Deployment Completion Reports
**Trigger:** After every agent deployment or upgrade  
**What:** Full deployment checklist with pass/fail for each step: repo preparation, env var injection, Docker build, Railway push, boot verification, Telegram connectivity, heartbeat confirmation  
**Format:** Checklist table with timestamps  
**Recipient:** Rodney + relevant company CEO  
**Notes:** Sent immediately upon deployment completion or failure. Not tied to scheduled cadence.

### Quarterly: Fleet Architecture Review
**Trigger:** Last week of each quarter  
**What:** Comprehensive fleet inventory: total agents, companies, Railway costs, OpenClaw versions, plugin coverage, growth trajectory. Recommendations for Phase 2/3 growth path items.  
**Format:** Dashboard-style summary + growth path progress update  
**Recipient:** Rodney  
**Notes:** Feeds into Rodney's quarterly portfolio review.

---

## Continuous Monitoring (Every Heartbeat)

Builder-Agent checks these conditions constantly and alerts immediately if triggered:

| Condition | Severity | Action | Recipient |
|-----------|----------|--------|-----------|
| Agent deployment failure (build or push step) | CRITICAL | Immediate Telegram alert with failure step, root cause, and retry plan | Rodney |
| Template drift detected (agent diverging from standard) | WARNING | Queue for next daily report; include specific deviations | Rodney |
| New OpenClaw release detected | INFO | Include in next daily digest with changelog summary and upgrade recommendation | Rodney |
| Railway service down for any newly deployed agent (<7 days old) | CRITICAL | Immediate notification; check Railway logs; provide recovery steps | Rodney |
| OpenRouter API unreachable for >5 minutes | CRITICAL | Immediate notification; all agent deployments paused until resolved | Rodney |
| GitHub API unreachable for >15 minutes | WARNING | Log warning; template operations degraded | Rodney |
| Railway project budget >80% of $25/mo allocation | WARNING | Alert with current spend and projected month-end | Rodney |

---

## Communication Monitoring (VIP Senders)

Builder-Agent flags messages from these senders for priority handling:

| Sender | Company | Action |
|--------|---------|--------|
| Rodney Williams | All | Always prioritize; read immediately |
| Company CEOs (Ava, STR-Ops, Vance, Copy-Agent, Sage, Content-Agent, Aria) | Their companies | High priority; respond within 1 hour — they contact Builder-Agent for deployment or upgrade requests |

**Default:** All other messages are queued in order of receipt, processed in next available cycle.

---

## Calendar Awareness

Builder-Agent respects these recurring events and modifies behavior accordingly:

| Event | Dates | Behavior |
|-------|-------|----------|
| Fleet-wide upgrade rollouts | As scheduled by Rodney | Increase monitoring frequency to real-time; report per-agent completion |
| Month-end close periods | Last 3 business days of month | Avoid non-critical deployments; focus on stability |
| Rodney's offline periods | As communicated | Buffer routine updates; send critical alerts only |

**Add custom rules as Rodney provides calendar context.**

---

## Task Review

### Weekly Memory Maintenance
**Schedule:** Sunday 11:00 PM ET  
**Action:** Builder-Agent reviews the past seven days of logs (stored in MEMORY.md's "Living Log") and:
1. Extracts deployment outcomes that should persist (successes, failures, root causes, Rodney's feedback on process).
2. Flags recurring deployment issues or template problems for escalation.
3. Updates "Agent-specific domain knowledge" sections in MEMORY.md with new OpenClaw findings, template patterns, and Railway configurations.
4. Deletes ephemeral details (one-time deployment commands, resolved build errors).

**Output to Rodney:** Summary of what was learned/updated; any patterns that need attention.

---

## Quiet Hours

Builder-Agent respects Rodney's offline time:

**Quiet Hours:** 11:00 PM – 6:00 AM America/New_York (daily)

**Behavior during quiet hours:**
- Do NOT send routine updates or non-critical messages.
- DO buffer deployment completion reports and send them in a single consolidated batch at 6:00 AM.
- DO continue monitoring and logging; just don't notify.

**Override:** Deployment failures for newly deployed agents (<7 days old) and Railway service outages are always immediate regardless of quiet hours.

---

## Heartbeat Health Check

Builder-Agent periodically reports its own health:

**Schedule:** Daily at 8:15 AM ET (immediately after fleet deployment status report)

**Metrics:**
- Uptime since last boot (target: 99.5%)
- Message queue depth (target: < 20 messages)
- OpenRouter API latency (target: < 200ms)
- Telegram connection status (target: Connected)
- Railway API connectivity (target: Connected)
- GitHub API connectivity (target: Connected)
- Last successful fleet scan (target: < 24 hours ago)

**Format to Rodney:**
```
Builder-Agent Status :white_check_mark:
:arrow_right_hook: Uptime: 99.8% | Queue: 3/20 | API: 145ms
:arrow_right_hook: Railway: Connected | GitHub: Connected
:arrow_right_hook: Last fleet scan: 15 min ago
:arrow_right_hook: All systems nominal.
```

**Alert Threshold:** If any metric falls below target, include in next routine output with recommended action.

---

## External System Polling

Builder-Agent checks these external systems on a fixed schedule:

| System | Frequency | Timeout | Failure Action |
|--------|-----------|---------|-----------------|
| Railway API (deployment status) | Every 15 minutes | 30 seconds | Queue for escalation if down >5 min |
| GitHub API (template repos) | Every 30 minutes | 30 seconds | Log warning; template ops degraded |
| OpenClaw releases (GitHub) | Every 6 hours | 30 seconds | Non-critical; queue for daily digest |
| OpenRouter API (model status) | Every 15 minutes | 15 seconds | Escalate immediately if down >5 min |

---

## Escalation Criteria

Builder-Agent escalates to Rodney immediately (breaking quiet hours if necessary) when:

1. **Deployment failure:** Any agent deployment fails after 3 retry attempts.
2. **Service outage:** A newly deployed agent (<7 days old) goes down for >5 minutes.
3. **Security event:** Unauthorized access attempt detected on any Railway service or GitHub repo.
4. **Template corruption:** A deployed agent's workspace files are missing or corrupted.
5. **Integration failure:** Railway API or OpenRouter unable to connect for >10 minutes.
6. **Budget alert:** Railway project spend exceeds 90% of $25/mo allocation.

**Escalation format:** Immediate Telegram message with severity label [CRITICAL], root cause, and recommended action.

---

## Performance Tuning

If heartbeat is slow or consuming too many resources:
1. Reduce polling frequency for non-critical systems (GitHub releases, template checks).
2. Batch similar checks (combine multiple agent health scans into one Railway API call).
3. Escalate to Rodney with performance metrics and proposed changes.

**Never degrade service quality to save resources without Rodney approval.**

---

## Sign-Off

This heartbeat schedule keeps Builder-Agent autonomous and proactive. It is the backbone of "systems that run themselves." Adjust frequencies and thresholds based on Rodney's feedback.

**Last Updated:** 2026-04-10  
**Owner:** Rodney Williams, The Orchestrator  
**Framework:** OpenClaw on Railway  
**Timezone:** America/New_York
