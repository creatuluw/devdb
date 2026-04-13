# Idea #004 — ComplyCraft

> An agent-ready compliance evidence workspace that collects, attests, and serves audit evidence for SMBs — consumable by both humans and AI agents

| Field | Value |
|---|---|
| **Date** | April 13, 2026 |
| **Market** | GRC / Compliance for SMB |
| **Model** | B2B SaaS |
| **Effort** | Medium |

---

## The Problem

Every growing startup hits the same wall: a customer sends a security questionnaire, an auditor requests evidence for SOC 2, or a finance review demands proof of controls. Teams scramble through Notion pages, Google Drive folders, and Slack messages to collect screenshots, export CSVs, and assemble evidence packages manually.

> "Compliance evidence collection involves gathering screenshots, configs, and policy docs from dozens of systems — then manually mapping them to controls. It's repetitive, error-prone, and expensive." — [Secureframe, 2026](https://secureframe.com/blog/automated-evidence-collection)

Enterprise GRC tools (Secureframe, Vanta, Drata) cost $15K+/yr and require deep integrations. They're overkill for a 20-person startup that just needs to answer 10 common audit asks. Meanwhile, AI agents are starting to handle security reviews — but they have no structured evidence to reference.

---

## The Idea

**ComplyCraft** is a lightweight compliance evidence workspace designed for SMBs. It auto-collects evidence from your existing tools (GitHub, AWS, Google Workspace, Slack), attests it with cryptographic hashes for chain-of-custody, and serves it through both a human dashboard and a machine-readable MCP API.

### How it works:

1. **Evidence Recipes** — Pre-built workflow templates for the 10 most common audit asks (SOC 2 access reviews, MFA enforcement proof, encryption configs, backup verification). Each recipe defines what to collect, from where, and what format.

2. **Auto-Collection** — Connect tools via OAuth. ComplyCraft pulls screenshots, configs, and exports on a schedule. Human-in-the-loop checkpoints for sensitive items. Timestamped and hashed (SHA-256) for chain-of-custody.

3. **Agent-Facing API** — A structured JSON/MCP endpoint that AI agents can query: "Do we have current MFA evidence?" "When was the last backup verification?" Other agents can reference and cite your evidence inventory directly.

4. **Evidence Packages** — One-click export of a complete evidence package for an auditor or customer questionnaire. PDF with attestation hashes, or a shared link with role-based access. Auto-refreshes when underlying evidence updates.

---

## Why It's Valuable

- **For SMBs:** Answer security questionnaires and audit requests in hours instead of weeks. No $15K/yr GRC platform needed. Focus on the 10 things auditors actually ask for.
- **For agents:** Machine-readable evidence inventory. An agent handling a security review can query ComplyCraft to check what evidence exists, its freshness, and its attestation status — then cite it directly.
- **Trust layer:** Cryptographic hashes on every evidence artifact create chain-of-custody without blockchain overhead. Auditors trust it. Agents can verify it programmatically.

---

## How to Build It (4-week MVP)

**Week 1 — Evidence Model + Recipes**
Postgres schema for evidence artifacts (type, source, collected_at, hash, status, control_mapping). Pre-seed 10 recipe templates in JSON. SvelteKit dashboard to browse and trigger recipes.

**Week 2 — Connectors + Collection**
OAuth integrations for GitHub (repo settings, branch protection), AWS (IAM policies, S3 configs), Google Workspace (MFA status, sharing settings). Each connector pulls evidence, stores to S3, hashes with SHA-256, records metadata in Postgres.

**Week 3 — Agent API + MCP Server**
REST + MCP endpoint: `list_evidence`, `get_evidence`, `check_control_status`. Returns structured JSON with freshness, hash, and attestation status. Agents can programmatically verify and cite evidence.

**Week 4 — Export + Sharing**
One-click evidence package export: PDF with attestation summary, or a shareable link with role-based access. Auto-refresh when underlying evidence updates. Scheduled re-collection with staleness alerts.

**Stack:** `SvelteKit` · `TypeScript` · `Postgres` · `S3` · `SHA-256` · `OAuth` · `MCP SDK` · `Railway`

---

## How to Pitch It

**One-liner:** "Compliance evidence on autopilot. Collect once, serve to auditors and AI agents forever."

| | |
|---|---|
| **Target ICP** | Seed to Series B startups (10–200 people) facing first SOC 2 audit, enterprise customer security questionnaires, or finance PBC requests. Engineering leads and ops managers who own compliance without a dedicated team. |
| **Go-to-market** | Open-source the evidence recipe format + CLI collector. "Show HN" launch. Template library as content marketing. Monetize the hosted dashboard, MCP endpoint, scheduled collection, and shareable evidence packages. |
| **Pricing** | Free: 3 recipes, manual collection · Pro $39/mo: all recipes, auto-collect, MCP API · Team $99/mo: unlimited, shareable packages, SSO |
| **Investor angle** | Compliance infrastructure for the SMB tier. Vanta and Secureframe own enterprise — nobody owns the lightweight, agent-native layer for smaller teams. Every startup that sells to enterprise customers needs this. |

---

## Sources

- [AWS — Building an AI-powered system for compliance evidence collection](https://aws.amazon.com/blogs/machine-learning/building-an-ai-powered-system-for-compliance-evidence-collection/)
- [FloQast — 10 Must-Have Features in Audit Evidence Management Tools](https://www.floqast.com/blog/10-must-have-features-in-audit-evidence-management-tools)
- [Secureframe — A Guide to Automated Evidence Collection for Compliance](https://secureframe.com/blog/automated-evidence-collection)

---

*Researched & written by Perplexity Computer · creatuluw@gmail.com*
