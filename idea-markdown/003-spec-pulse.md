# Idea #003 — SpecPulse

*Daily Idea · April 12, 2026*

**Tagline:** Continuous agent-contract tests for APIs — publish what agents can safely do, and prove it stays true.

## The Problem

Teams are shipping agents that call real APIs (payments, support, CRM, infra). But the ‘interface’ agents rely on is a mix of human docs, stale examples, and tribal knowledge. When an endpoint changes, a scope requirement shifts, or rate limits tighten, agents fail in production — or worse, do the wrong thing. There’s no standard place to publish a machine-checkable contract for agents, and no continuous test that says: ‘an agent can still complete task X safely with tool Y’. 

## The Idea

SpecPulse is a webapp that turns your API + workflows into **agent contracts**: machine-readable capability specs (JSON Schema for parameters/outputs, auth scopes, rate limits, safety constraints, example calls) paired with **continuous contract tests** that run on a schedule and on every deploy. It publishes an agent-facing ‘capabilities feed’ and optional MCP/OpenAPI adapters, so humans can review changes and AI agents can automatically discover what’s safe and supported today.

## Why it’s valuable (for humans + agents)

- **For humans:** Fewer broken automations and fewer incident tickets. Product and platform teams get a clear, versioned ‘what agents can do’ surface, plus change alerts when a deploy breaks a contract test. Compliance teams get evidence that risky workflows are gated and validated.
- **For agents:** A stable, queryable capabilities feed with typed schemas and freshness signals. Agents can select tools by guaranteed-supported tasks, request just-in-time scopes, and adapt when a contract version changes.
- **Compounding moat:** As more workflows are tested, SpecPulse becomes the source of truth for ‘agent-safe’ operations and their historical reliability. The contract test corpus becomes a defensible dataset that improves recommendations and auto-generated adapters.

## How to build it (4-week MVP — SvelteKit/TypeScript)

**Stack:** SvelteKit, TypeScript, Postgres, Prisma, BullMQ/Redis, OpenAPI parser, JSON Schema, Playwright (optional), Railway, Slack API

- Week 1: Data model + UI skeleton (SvelteKit) — APIs, Workflows, Contracts. Ingest OpenAPI + auth metadata. Store in Postgres.
- Week 2: Contract runner — define workflow tests (YAML/JSON), run via worker (Node + Playwright/HTTP). Record results, latency, error traces.
- Week 3: Publish capabilities — /capabilities.json with JSON Schema, versioning, and freshness. Generate MCP tool definitions + SDK snippet.
- Week 4: Alerts + diffs — GitHub webhook, deployment hooks, Slack/email alerts, ‘what changed’ contract diff view. Ship hosted demo + docs.

## How to pitch it

- **One-liner:** "CI for agent tools: publish an agent contract, then continuously prove it still works."
- **ICP:** API-first SaaS (B2B), platform teams shipping internal agents, and developer experience teams that maintain OpenAPI specs and SDKs.
- **GTM:** Start with an OpenAPI ‘agent contract’ linter + GitHub Action (free). Use it to upsell the hosted dashboard, continuous runners, capabilities feed hosting, and MCP adapter generation. Launch via ‘Show HN’, DX communities, and partner with API doc tools.
- **Pricing:**
  - Free: 1 API, 10 workflow tests, daily runs, public capabilities feed
  - Pro: $39/mo — 5 APIs, hourly runs, Slack alerts, private feed
  - Enterprise: $149/mo — unlimited APIs, SSO, audit exports, role-based approvals
- **Investor angle:** As agents become a primary customer of APIs, ‘agent readiness’ becomes a new reliability layer. SpecPulse is the monitoring + contract system for that layer — a chokepoint between API changes and autonomous execution.

## Sources

- Boomi — AI Agent Governance Framework: https://boomi.com/blog/ai-agent-governance-framework/
- Cerbos — Permission Management for AI Agents: https://www.cerbos.dev/blog/permission-management-for-ai-agents
- MintMCP — AI agent security audit: https://www.mintmcp.com/blog/ai-agent-security-audit
