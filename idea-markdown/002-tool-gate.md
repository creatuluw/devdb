# Idea #002 — ToolGate

> Approval gates, schema contracts, and audit logs for AI agents using tools

| Field | Value |
|---|---|
| **Date** | April 11, 2026 |
| **Market** | Developer Tools / AI Governance |
| **Model** | B2B SaaS |
| **Effort** | Medium |

---

## The Problem

AI agents can now call tools — send emails, create PRs, query databases, make purchases. But there is no standard way to enforce who approved what, what schemas are allowed, or to produce an audit trail that satisfies compliance teams.

Observability tools like LangSmith and Phoenix can trace what agents did after the fact. AWS Bedrock Guardrails filter inputs/outputs. But neither provides an app-agnostic policy gateway that sits between the agent and the tool — enforcing allow/deny/approval-required at runtime with typed schema contracts.

> "Browser agents are less safe than chat models — they need runtime guardrails that go beyond input/output filtering to cover actual tool execution." — [Invariant Labs, 2026](https://invariantlabs.ai/blog/enhancing-browser-agent-safety)

MCP and structured tool schemas are making tool contracts a first-class product surface. Enterprises adopting agents need exactly one thing before they go to production: a policy layer with human-in-the-loop approval and audit-grade logs. Nobody owns this layer yet.

---

## The Idea

**ToolGate** is a webapp that acts as a policy gateway for AI agent tool calls. It sits between agents and their tools, enforcing typed schema contracts, routing high-risk actions through human approval gates, and producing audit-grade logs — all queryable by both humans and other agents.

### How it works:

1. **Policy Engine** — Define allow/deny/approval-required rules per tool, per agent, per team. Write policies in YAML or via a visual editor. Supports wildcard matching, parameter constraints, and time windows.

2. **Schema Contracts** — Every tool call passes through a typed JSON Schema validator. Agents can only invoke tools with the exact parameters allowed. Malformed or unauthorized payloads are rejected before execution.

3. **Human Approval Gates** — High-risk actions pause and route to a human via Slack, email, or dashboard. The agent waits for approval before proceeding — with configurable timeout and escalation.

4. **Audit Trail** — Every tool call (approved, denied, timed out) is logged with agent ID, parameters, policy matched, approver, and timestamp. Exportable as JSON for compliance, queryable via API for other agents.

---

## Why It's Valuable

- **For enterprises:** Ship agents to production with confidence. Every tool call has a policy, an approval flow, and a log. SOC 2 and ISO 27001 auditors get the paper trail they need.
- **For agents:** Machine-readable policy responses. Agents know exactly which tools they can use, what parameters are allowed, and whether to wait for approval — no guessing.
- **For developers:** Drop-in middleware. Works with any MCP server, OpenAI function calling, or custom tool framework. One config file, zero code changes to your agent.

---

## How to Build It (4-week MVP)

**Week 1 — Policy Engine + Proxy**
Build a lightweight HTTP proxy that intercepts tool calls. Policy rules in YAML define allow/deny/approval_required per tool name, agent ID, and parameter patterns. JSON Schema validation on every payload. Store policies in Postgres.

**Week 2 — Approval Flow**
When a call hits `approval_required`, ToolGate holds the request in Redis, sends a notification (Slack webhook or email), and exposes a `/approve/:id` endpoint. Configurable timeout + auto-deny/escalation.

**Week 3 — Audit Log + Dashboard**
Every decision (allow, deny, approve, timeout) is logged to Postgres with full context. SvelteKit dashboard shows real-time feed, filterable by agent, tool, and decision. Export as JSON or CSV for compliance.

**Week 4 — SDK + MCP Integration**
TypeScript SDK wraps any MCP client. Also ships as Express/Hono middleware. Agents query `/capabilities` to get their allowed tool list — machine-readable policy discovery. One-click deploy on Railway.

**Stack:** `SvelteKit` · `TypeScript` · `Postgres` · `Redis` · `JSON Schema` · `MCP SDK` · `Railway` · `Slack API`

---

## How to Pitch It

**One-liner:** "IAM for AI agents. Every tool call gets a policy, an approval gate, and a log."

| | |
|---|---|
| **Target ICP** | Engineering teams shipping agents to production, platform teams managing multi-agent systems, compliance officers at regulated enterprises, MCP server authors who need a governance layer. |
| **Go-to-market** | Open-source the proxy + policy engine. "Show HN" launch. Free for single-agent use. Monetize team dashboards, SSO, advanced approval workflows, and compliance exports. |
| **Pricing** | Free: 1 agent, 1K calls/mo, basic logs · Pro $29/mo: 10 agents, approval flows, Slack · Enterprise $149/mo: unlimited, SSO, compliance exports |
| **Investor angle** | IAM for the agent economy. Every enterprise deploying agents will need a policy layer — ToolGate is the natural chokepoint. Comparable to how Okta became essential for human identity. |

---

## Sources

- [Invariant Labs — Enhancing Browser Agent Safety with Guardrails](https://invariantlabs.ai/blog/enhancing-browser-agent-safety)
- [Agent Patterns — Human Approval For AI Agents](https://www.agentpatterns.tech/en/governance/human-approval)
- [Stacklok ToolHive — Create a Custom MCP Registry](https://docs.stacklok.com/toolhive/tutorials/custom-registry)
- [Moveworks — How Policy Validators Help AI Compliance](https://www.moveworks.com/us/en/resources/blog/how-policy-validators-help-ai-compliance)
- [AWS — Amazon Bedrock Guardrails](https://aws.amazon.com/bedrock/guardrails/)
- [TrueFoundry — What is MCP Registry?](https://www.truefoundry.com/blog/what-is-mcp-registry)

---

*Researched & written by Perplexity Computer · creatuluw@gmail.com*
