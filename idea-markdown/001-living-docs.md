# Idea #001 — LivingDocs

> Auto-generated, always-fresh agent-readable knowledge layers for any website or product

| Field | Value |
|---|---|
| **Date** | April 10, 2026 |
| **Market** | Developer Tools / AI Infra |
| **Model** | B2B SaaS |
| **Effort** | Medium |

---

## The Problem

AI agents are blind to most of the web. They either hallucinate outdated API details, fail to find the right page, or burn thousands of tokens parsing HTML noise just to answer one question. The `llms.txt` standard exists — but only 5–15% of websites have implemented it, and most implementations are static, manually maintained files that go stale within weeks.

> "Without a dedicated machine-readable entry point, coding assistants fall back on generic web scraping, which frequently produces hallucinations or outdated patterns." — Fern, 2026

Meanwhile, **Google, AWS, and Microsoft have all shipped MCP servers** for their own docs in early 2026. Every mid-size SaaS, open-source project, or internal tool has the same problem — and zero budget to build this themselves.

---

## The Idea

**LivingDocs** is a webapp that takes any URL, sitemap, or GitHub repo and automatically generates a continuously-synced, agent-readable knowledge layer: a structured `llms.txt`, a full-context `llms-full.txt`, and an optional hosted MCP server endpoint — all kept fresh via webhooks or scheduled re-indexing.

Users paste their domain. LivingDocs crawls their content, uses an LLM to extract structure (endpoints, concepts, relationships, changelog entries), and serves the result at a permanent, versioned URL that AI agents can query directly. Humans get a clean dashboard. Agents get clean JSON or Markdown. Both win.

---

## Why It's Valuable

- **For humans:** Your product shows up accurately in AI-assisted search, Cursor, Claude, and Copilot — instead of being hallucinated or ignored. Higher AI-referred conversion traffic (ChatGPT converts at 15.9%).
- **For agents:** A clean, structured, token-efficient entry point. No HTML parsing, no stale snapshots. Semantic search over your content via a standard MCP endpoint.
- **For builders:** Gartner says 30%+ of new API demand in 2026 comes from LLM tools. This is infrastructure for that wave.
- **Moat:** The value compounds — the longer a site is indexed, the richer the version history. Agents can ask "what changed in v2.3?" and get a real answer.

---

## How to Build It (4-week MVP)

**Week 1 — Crawler + Extractor**
SvelteKit frontend, URL input → sitemap parser → Firecrawl or Playwright for content fetch → chunk + embed with OpenAI `text-embedding-3-small`, store in Postgres with pgvector.

**Week 2 — Generator**
LLM pass (GPT-4o-mini) to produce structured `llms.txt` and `llms-full.txt`. Version each generation. Expose at `yourdomain.livingdocs.io/llms.txt`.

**Week 3 — MCP Server**
Expose a minimal MCP-compatible endpoint: `search_document` + `get_document` tools over the embedded knowledge base. One-click deploy via Railway.

**Week 4 — Sync + Dashboard**
Webhook support for GitHub, Notion, Gitbook. Dashboard showing agent traffic (bot vs. human), most-queried pages, staleness indicators. Auto re-index on schedule.

**Stack:** `SvelteKit` · `TypeScript` · `Postgres + pgvector` · `OpenAI Embeddings` · `MCP SDK` · `Railway` · `Firecrawl API` · `GPT-4o-mini`

---

## How to Pitch It

**One-liner:** "robots.txt was for Google. LivingDocs is for AI agents. One line of code and your product is readable by every AI in the world."

| | |
|---|---|
| **Target ICP** | Developer tools, SaaS products with public docs, open-source maintainers, internal tooling teams at 50–500 person companies. |
| **Go-to-market** | Launch on Product Hunt + Hacker News "Show HN". Open-source the llms.txt generator. Monetize the MCP hosting, sync automation, and analytics dashboard. |
| **Pricing** | Free: 1 site, manual refresh · Pro $19/mo: 5 sites, auto-sync, analytics · Team $79/mo: unlimited sites, MCP endpoint, webhooks, version history |
| **Investor angle** | API infra for the agent economy. Comparable to how Algolia became essential for search — LivingDocs becomes essential for agent discoverability. |

---

## Comparable Signals

- Fern, Mintlify, and Scalar are already competing on llms.txt generation — but only for API docs platforms, not the general web.
- Google launched its Developer Knowledge API (MCP) in Feb 2026. AWS and Microsoft followed. The race for agent-readable content is on.
- Only 5–15% of websites have llms.txt today. Massive greenfield opportunity.

---

*Researched & written by Perplexity Computer · creatuluw@gmail.com*
