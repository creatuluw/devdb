# Idea #005 — IncidentPack

> Auto-assembles incident postmortem evidence packages when production incidents occur — signed, hash-anchored, and queryable by both humans and AI agents

| Field | Value |
|---|---|
| **Date** | April 14, 2026 |
| **Market** | DevOps / SRE / Incident Management |
| **Model** | B2B SaaS |
| **Effort** | Medium |

---

## The Problem

When a production incident fires, the clock starts ticking. Engineers scramble across five browser tabs — Datadog, Slack, GitHub, PagerDuty, the deployment dashboard — trying to assemble a picture of what broke, when, and why. By the time someone writes a postmortem, half the evidence has scrolled off Slack and the incident timeline is already fuzzy.

> "Human-in-the-loop runbook improvement requires structured, reproducible incident data — but most incident records are fragmented across tools, unstructured, and manually assembled after the fact." — [Amazon Science, 2025](https://www.amazon.science/publications/human-in-the-loop-runbook-improvement-with-agentic-support-automation)

PagerDuty and Opsgenie own alerting. Rootly and incident.io own incident coordination. But nobody owns the *evidence chain*. After an incident closes, assembling logs, metrics, Slack threads, git diffs, and deployment history into a coherent postmortem takes hours — and the result is often a Google Doc nobody reads.

**The signals are clear:**
- Regulated industries (SOC 2, HIPAA, PCI-DSS) require incident evidence preservation
- AI agents are starting to participate in incident response but lack structured evidence to reason over
- Postmortem fatigue is real — teams skip them because assembling the evidence is too painful

---

## The Idea

**IncidentPack** is a webapp that auto-assembles incident postmortem evidence packages the moment production incidents occur. It pulls logs, metrics, alerts, Slack threads, git diffs, and deployment history into a signed, hash-anchored package with both a human-readable postmortem report and an agent-readable manifest. Agents can query the package to answer "what caused the outage?" or "was the fix deployed?" Humans get a clean PDF/web report for stakeholders.

**Differentiation from ComplyCraft (#004):** ComplyCraft is proactive compliance evidence (SOC 2, security questionnaires). IncidentPack is reactive incident forensics — it kicks in when something breaks and assembles the evidence for root cause analysis, regulatory reporting, and continuous improvement.

### How it works:

1. **Auto Evidence Collection** — The moment an incident fires (PagerDuty, Opsgenie, or Grafana webhook), IncidentPack begins collecting: logs from Datadog or Loki, Slack thread messages, git diffs and recent commits, deployment events from Railway or Vercel. Every artifact is SHA-256 hashed for chain-of-custody.

2. **Signed Package + Manifest** — All evidence is assembled into a signed, hash-anchored package with two outputs: a structured `manifest.json` for agents (queryable, typed, versioned) and a clean PDF/web report for human stakeholders. The package is immutable after collection.

3. **Agent-Queryable MCP Endpoint** — An MCP server exposes three tools: `query_incident`, `get_evidence`, `get_timeline`. Agents can answer "what caused the outage?" or "was the fix deployed?" by querying the structured evidence package — no Slack archaeology required.

4. **LLM Postmortem Drafts** — Once evidence is collected, an LLM summarizes it into a structured postmortem draft: root cause analysis, impact timeline, contributing factors, and action items. Teams review and publish — instead of writing from scratch across disconnected tabs.

---

## Why It's Valuable

- **For SRE & DevOps:** Stop spending 3 hours assembling postmortem evidence after a 2-hour incident. IncidentPack collects while you're still firefighting — so the evidence is ready before the retro even starts.
- **For AI agents:** Structured, signed evidence packages give agents the context they need to participate meaningfully in incident response and RCA — instead of reasoning over raw Slack noise or reconstructed timelines.
- **For compliance:** SOC 2, HIPAA, and PCI-DSS all require incident evidence preservation. IncidentPack's signed, hash-anchored packages satisfy auditor requirements with no extra manual effort.

---

## How to Build It (4-week MVP)

**Week 1 — Dashboard + Incident Model**
SvelteKit dashboard + Postgres incident schema. Webhook receivers for PagerDuty, Opsgenie, and Grafana alerts. When an alert fires, create an incident record and begin the evidence collection pipeline.

**Week 2 — Evidence Collectors**
Pull logs from Datadog or Loki API, Slack threads via OAuth, git diffs and deployment events from GitHub API and Railway/Vercel webhooks. Each artifact is stored to S3 and hashed with `SHA-256` for chain-of-custody.

**Week 3 — Package Assembler + MCP**
Generate a signed `manifest.json` (agent-readable), an incident timeline view, and a PDF export (human-readable). MCP server exposes: `query_incident`, `get_evidence`, `get_timeline`.

**Week 4 — Postmortem Generator**
LLM summarizes collected evidence into a structured postmortem draft: RCA, impact, timeline, action items. Dashboard for browsing incidents, comparing patterns across time, and exporting stakeholder-ready reports.

**Stack:** `SvelteKit` · `TypeScript` · `Postgres` · `S3` · `Datadog API` · `Slack API` · `GitHub API` · `MCP SDK` · `Railway`

---

## How to Pitch It

**One-liner:** "Your production incident just happened. IncidentPack already has the evidence."

| | |
|---|---|
| **Target ICP** | SRE and DevOps teams at Series A–C startups (50–500 people), platform engineering teams, and incident commanders at companies with compliance requirements. Teams that run more than 2 incidents per month and still don't have a reliable postmortem process. |
| **Go-to-market** | Open-source the evidence collector CLI and manifest spec. Show HN launch. Free tier for up to 5 incidents/month. Content marketing around incident management best practices and postmortem culture. |
| **Pricing** | Free: 5 incidents/mo, manual collection · Pro $49/mo: unlimited, auto-collect, MCP API, postmortem drafts · Team $129/mo: SSO, custom integrations, SLA reporting |
| **Investor angle** | Evidence layer for the incident lifecycle. PagerDuty owns alerting, Rootly/incident.io own coordination — nobody owns the evidence chain. IncidentPack sits between them and becomes the system of record for incident forensics. |

---

## Market Signals

- Regulated industries require incident evidence preservation (SOC 2, HIPAA, PCI-DSS)
- AI agents are starting to participate in incident response but lack structured evidence to reason over
- Postmortem fatigue is real — teams skip them because assembling evidence is too painful
- AI-powered compliance and runbook automation are emerging as primary areas of infrastructure investment ([AWS](https://aws.amazon.com/blogs/machine-learning/building-an-ai-powered-system-for-compliance-evidence-collection/), [Amazon Science](https://www.amazon.science/publications/human-in-the-loop-runbook-improvement-with-agentic-support-automation))

---

## Sources

- [AWS — Building an AI-powered system for compliance evidence collection](https://aws.amazon.com/blogs/machine-learning/building-an-ai-powered-system-for-compliance-evidence-collection/)
- [Teleport — How AI Agents Impact SOC 2](https://goteleport.com/blog/ai-agents-soc-2/)
- [Amazon Science — Human-in-the-loop runbook improvement with agentic support automation](https://www.amazon.science/publications/human-in-the-loop-runbook-improvement-with-agentic-support-automation)
- [Koder.ai — Centralized Audit Evidence Collection](https://koder.ai/blog/build-web-app-centralized-audit-evidence-collection)

---

*Researched & written by Perplexity Computer · creatuluw@gmail.com*
