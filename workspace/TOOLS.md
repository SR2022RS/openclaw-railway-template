# TOOLS.md — Builder-Agent Environment Configuration

Complete system configuration. Everything Builder-Agent needs to know about its runtime environment, integrations, and deployment.

---

## Telegram Configuration

### Bot Setup
**Bot Name:** Builder-Agent  
**Telegram Handle:** @BuilderAgentBot (placeholder — currently uses Agent Builder Telegram bot)  
**Bot Token:** [Stored in Railway env var: `TELEGRAM_BOT_TOKEN`]  
**Chat ID (Rodney):** [Stored in Railway env var: `RODNEY_CHAT_ID`]

### Message Routing
- **Primary recipient:** Rodney (chat ID from env var)
- **Fallback:** If primary message fails after 3 retries, log to error queue and alert via email to admin@holigenixhealthcare.com
- **Quiet hours:** Do not send routine messages 11 PM – 6 AM ET (store in buffer, send at 6 AM)
- **Critical alerts:** Override quiet hours for CRITICAL and SECURITY severity levels

### Telegram Rate Limits
- **Burst limit:** 30 messages per second  
- **Sustained limit:** Builder-Agent sends < 100 messages/hour during business hours
- **Handling overage:** Batch deployment status messages, queue non-urgent items, escalate if urgent queue fills

### Telegram Message Format
```
[Content in Markdown]

— Builder-Agent :building_construction:
[Timestamp in ET]
```

**Supported Markdown:**
- Bold: `**text**`
- Italic: `_text_`
- Code: `` `code` `` (inline) or ` ``` ` (block)
- Lists: `-` for bullets, `1.` for numbered
- Links: `[text](url)`
- Tables: Pipe-delimited with header separator

**Not supported:** HTML, custom formatting. Use plain Markdown.

---

## Composio MCP Configuration

### Access Credentials
**Composio API Key:** [Stored in Railway env var: `COMPOSIO_API_KEY`]  
**Workspace ID:** [Stored in Railway env var: `COMPOSIO_WORKSPACE_ID`]  
**Integration Status:** ACTIVE

### Enabled Integrations
Builder-Agent has access to these Composio-managed integrations:

| Integration | Provider | Credentials | Status | Last Tested |
|-------------|----------|-------------|--------|-------------|
| GitHub | GitHub API | Token via Railway env var | Active | 2026-04-10 |
| Railway | Railway API | Token via Railway env var | Active | 2026-04-10 |

### Authentication & Secrets
- All credentials stored in Railway environment variables (prefixed `COMPOSIO_*`)
- **Never expose API keys in logs, messages, or user-facing output**
- **Rotation schedule:** Every 90 days or on Rodney's request
- **Breach protocol:** If compromised, alert Rodney immediately and rotate

### Composio Error Handling
| Error Code | Meaning | Action |
|------------|---------|--------|
| 401 | Authentication failed | Check env var, retry once, escalate |
| 403 | Permission denied | Verify account permissions, escalate |
| 429 | Rate limit | Back off exponentially, queue and retry |
| 5xx | Service error | Retry with jitter, escalate if > 5 min |

---

## LLM Configuration

### Model Specification
**Provider:** OpenRouter  
**Model:** MiniMax M2.5  
**API Key:** [Stored in Railway env var: `OPENROUTER_API_KEY`]  
**Endpoint:** `https://openrouter.ai/api/v1/chat/completions`

### Model Parameters
```json
{
  "model": "minimax/minimax-text-01",
  "temperature": 0.5,
  "max_tokens": 2048,
  "top_p": 0.95,
  "frequency_penalty": 0.5,
  "presence_penalty": 0.0
}
```

**Rationale:**
- **Temperature 0.5:** Builder-Agent favors consistency and precision over creativity. Infrastructure operations demand deterministic outputs.
- **Max tokens 2048:** Keeps deployment reports focused and scannable. Increase to 4096 only for multi-agent rollout reports.
- **Top P 0.95:** Nucleus sampling prevents rare, irrelevant tokens.
- **Frequency penalty 0.5:** Reduces repetition in deployment status reports.

### Token Budget
- **Monthly quota:** Check OpenRouter dashboard for current allocation
- **Builder-Agent's allocation:** Shared portfolio quota
- **Monthly burn rate:** Moderate (daily fleet scans + deployment operations)
- **Alert threshold:** Escalate to Rodney if burn rate > 110% of baseline

### Fallback Strategy
If OpenRouter is unavailable:
1. Retry after 10 seconds (backoff to 60s max).
2. After 3 retries, degrade gracefully:
   - Simple outputs (deployment status checks): proceed with cached data
   - Complex outputs (fleet analysis, upgrade assessments): queue and retry hourly
3. After 24 hours of outage, alert Rodney and await direction.

---

## OpenClaw Configuration

### Framework Details
**Version:** v2026.3.24  
**GitHub:** https://github.com/openclaw (reference)  
**Documentation:** OpenClaw project docs

### Agent Runtime Environment
**Runtime:** Python 3.11+  
**Framework:** OpenClaw agent executor  
**Deployment:** Railway container  
**Startup command:** Defined in Dockerfile entrypoint (entrypoint.sh)

### OpenClaw Features Used by Builder-Agent
- **Task execution:** Builder-Agent uses OpenClaw's task runner for scheduled fleet scans and deployment operations
- **Memory integration:** Builder-Agent persists state to workspace/MEMORY.md between executions
- **Logging:** OpenClaw logs to Railway dashboard (Logs tab)
- **Error handling:** Unhandled errors are caught and logged; Builder-Agent retries per policy
- **Plugins:** QMD (Quick Message Dispatch) for efficient Telegram messaging; Lossless Claw for message fidelity preservation
- **configPath() fix:** Dual-path resolution applied — ensures workspace files load correctly from both local and containerized paths

### OpenClaw Debugging
- **Logs location:** Railway dashboard > Builder-Agent > Logs
- **Enable verbose logging:** Set `LOG_LEVEL=DEBUG` in Railway env vars (temporary only; revert after debugging)
- **Local testing:** Clone openclaw-railway-template repo, set local .env, run with Docker Compose

---

## Railway Deployment

### Container Configuration
**Image:** Built from openclaw-railway-template Dockerfile  
**Replicas:** 1 (single-agent company)  
**Memory:** 512MB  
**CPU:** 0.5 vCPU  
**Uptime SLA:** 99.5%

### Railway Dashboard Access
- **Project name:** Agent Builder
- **Service name:** Builder-Agent
- **Monthly budget:** $25/mo
- **Owner:** Rodney Williams (admin credentials managed separately)

### Deployment Process
1. **Code update:** Commit to `main` branch of openclaw-railway-template.
2. **Build:** Railway builds automatically from Dockerfile; check logs for errors.
3. **Deploy:** `railway up` pushes to Railway service; monitor uptime during rollout.
4. **Verification:** Builder-Agent sends "online" message to Rodney on successful boot.

### Rollback Procedure
If deployment fails:
1. Railway shows deployment status; use "Rollback" button if available.
2. If unavailable, reset env vars to previous state and re-deploy.
3. Alert Rodney immediately with error details.

### Resource Monitoring
- **CPU usage:** Monitor in Railway > Metrics. Alert if > 80% sustained.
- **Memory usage:** Alert if > 75% sustained.
- **Disk usage:** Monitor workspace file volume; alert if approaching limits.
- **Network:** Monitor for unusual bandwidth spikes during fleet scans.

---

## Environment Variables Summary

**Secure storage:** All env vars stored in Railway project settings (encrypted at rest).

| Variable | Purpose | Example Value | Secret? |
|----------|---------|----------------|---------|
| `TELEGRAM_BOT_TOKEN` | Telegram bot authentication | `123456:ABC-DEF` | Yes |
| `RODNEY_CHAT_ID` | Rodney's Telegram chat ID | `987654321` | Yes |
| `OPENROUTER_API_KEY` | OpenRouter LLM access | `sk-or-xxx` | Yes |
| `COMPOSIO_API_KEY` | Composio MCP access | `comp_xxx` | Yes |
| `COMPOSIO_WORKSPACE_ID` | Composio workspace | `ws_xxx` | Yes |
| `RAILWAY_API_TOKEN` | Railway deployment API access | `railway_xxx` | Yes |
| `GITHUB_TOKEN` | GitHub API access for template repos and OpenClaw monitoring | `ghp_xxx` | Yes |
| `LOG_LEVEL` | Logging verbosity | `INFO` | No |
| `TIMEZONE` | Agent timezone (for scheduling) | `America/New_York` | No |
| `OPENCLAW_VERSION` | Current OpenClaw version tracking | `v2026.3.24` | No |

### Adding New Environment Variables
1. **Create the variable in Railway project settings** (do not commit to git).
2. **Document it here in TOOLS.md** with purpose, example, and sensitivity.
3. **Restart Builder-Agent's service** for changes to take effect.
4. **Verify** by checking logs for startup confirmation.

---

## Health Check & Monitoring

### Builder-Agent Health Endpoints
- **Readiness:** Builder-Agent is ready when BOOTSTRAP.md loads successfully and all 7 workspace files are parsed.
- **Liveness:** Builder-Agent sends heartbeat check per HEARTBEAT.md schedule (daily at 8:15 AM ET).
- **Manual check:** Rodney can trigger via Telegram command: `@BuilderAgentBot status`

### Monitoring & Alerts
- **Uptime:** Railway dashboard shows green if service is running.
- **Error rate:** Escalate to Rodney if error count > 5 in past hour.
- **Response latency:** Alert if > 500ms average over 5-min window.
- **Integration health:** Check Railway API, GitHub API, and OpenRouter status every 15 minutes.

---

## Local Development & Testing

### Prerequisites
- Python 3.11+
- Docker for containerization
- Railway CLI (`railway` command)
- Git for template repo management

### Setup
```bash
# Clone the agent repo
git clone https://github.com/[org]/openclaw-railway-template.git
cd openclaw-railway-template

# Install dependencies
pip install -r requirements.txt

# Set local env vars (copy from Railway, modify as needed)
cp .env.example .env
# Edit .env with test credentials

# Run Builder-Agent locally
docker compose up --build
```

### Testing Against Staging
- **Telegram test bot:** Use a separate test bot token for non-production messaging
- **OpenRouter sandbox:** Use test API key with limited quota
- **Railway staging:** Deploy to a separate Railway service for testing before production push

### Debugging Tips
- **Enable verbose logging:** Set `LOG_LEVEL=DEBUG` in .env
- **Watch logs:** Check Railway dashboard > Builder-Agent > Logs (or `railway logs` CLI)
- **Test integrations:** Verify each API connection independently before full boot
- **Template validation:** Run workspace file parser against all 9 files to verify structure

---

## Disaster Recovery

### Backup & Restore
- **Config backup:** SOUL.md, IDENTITY.md, BOOTSTRAP.md, etc., are version-controlled in openclaw-railway-template repo.
- **Memory backup:** MEMORY.md is synced to GitHub weekly during memory maintenance.
- **Recovery steps:** If Builder-Agent crashes, restore from Railway backup or re-deploy from main branch with `railway up`.

### Communication Failover
If Telegram fails:
1. Alert Rodney via email at admin@holigenixhealthcare.com immediately.
2. Switch to email for critical deployment updates.
3. Queue all messages to retry on Telegram when connection restores.

---

## Support & Escalation

### Who to Contact
- **Builder-Agent errors or outages:** Alert Rodney at admin@holigenixhealthcare.com
- **Railway infrastructure:** Railway support portal
- **OpenRouter issues:** OpenRouter support dashboard
- **Composio issues:** Composio support dashboard

### Escalation Path
1. Builder-Agent detects critical issue (deployment failure, service outage, template corruption).
2. Log error with full context (timestamp, affected agent, error category, retry count).
3. Alert Rodney immediately via Telegram.
4. If Telegram unavailable, email Rodney.
5. Await Rodney's direction.

---

## Sign-Off

This configuration is complete and production-ready. Keep TOOLS.md synchronized with actual deployments. Any changes to Railway settings, API keys, or integrations must be reflected here within 24 hours.

**Last Updated:** 2026-04-10  
**Last Tested:** 2026-04-10  
**Owner:** Rodney Williams, The Orchestrator  
**Deployed via:** Railway, OpenClaw, MiniMax M2.5/OpenRouter
