# devdb — LLM Agent Dev Tips Archive

Daily tips for SvelteKit + TypeScript developers on using LLM coding agents effectively.

## Structure

```
devdb/
├── tips-html/        # Gmail-compatible HTML email bodies per tip
│   ├── tip-001.html
│   └── ...
├── tips-markdown/    # Full tip content as Markdown
│   ├── tip-001.md
│   └── ...
├── tips-data/
│   └── dev-tips.json   # All tips as structured JSON (appended with each new tip)
└── tips-digests/     # Weekly digest HTML emails (every Monday)
    ├── digest-2026-04-14.html
    └── ...
```

## Tips Index

| # | Title | Category | Date |
|---|-------|----------|------|
| 001 | Context Windows as Architecture | Context Management | 2026-04-10 |
| 002 | Agent-First API Design | API Design | 2026-04-10 |
| 003 | Prompt Chaining for UI Generation | Prompt Engineering | 2026-04-10 |

## Categories (rotating — 29 total)

| # | Category | Focus |
|---|----------|-------|
| 0 | Context Management | Structuring codebases, AGENTS.md, file organization for agents |
| 1 | API Design | Zod schemas, typed routes, error envelopes, self-documenting APIs |
| 2 | Prompt Engineering | Prompt chains, few-shot patterns, system prompts, design priming |
| 3 | Agent Tooling | MCP servers, tool-use patterns, multi-agent orchestration |
| 4 | Data Architecture | PostgreSQL, DuckDB, Drizzle ORM, migrations, analytics pipelines |
| 5 | Design Systems | Tailwind tokens, component libraries, design-to-code workflows |
| 6 | DevOps & Infra | CI/CD with agents, Railway, Docker, monorepo management |
| 7 | Testing & Quality | Agent-assisted testing, snapshot testing, type coverage, Playwright |
| 8 | Knowledge Bases | RAG systems, vector stores, embedding pipelines, agent memory |
| 9 | Documentation | Auto-generating docs, JSDoc, OpenAPI, living docs patterns |
| 10 | Webdesign & Styling | Agent-driven UI, Tailwind best practices, responsive design |
| 11 | Best Dev Tools | Monthly spotlight on tools for LLM-assisted development |
| 12 | Agent Workflow & Context | Multi-step workflows, handoffs, state management, human-in-the-loop |
| 13 | Innovation | Cutting-edge patterns, emerging paradigms, future of agentic dev |
| 14 | Pure Creativity | Unconventional agent use, generative UI, creative coding with LLMs |
| 15 | Agent Self-Learning | Self-reflection loops, meta-prompting, feedback pipelines |
| 16 | Agent-to-Agent Interactions | Multi-agent systems, orchestrators, inter-agent communication |
| 17 | Optimizing DX | Dev experience improvements, tooling ergonomics, reducing friction |
| 18 | Build Internal Tools for LLM | Admin UIs, dashboards, dev portals purpose-built for LLM workflows |
| 19 | Failure Archaeology | Mining past agent failures as training signal — error taxonomies, regression suites |
| 20 | Cognitive Load Engineering | Designing agent outputs to minimize human verification overhead |
| 21 | Temporal Reasoning & State Drift | Anchoring agents to reality — versioned context, freshness signals, stale state detection |
| 22 | The Economics of Agent Time | Token budgeting, cost-per-feature, ROI measurement, when NOT to use an agent |
| 23 | Adversarial Prompting as a Design Tool | Red-teaming your own prompts to find failure modes before production |
| 24 | Comprehension Debt | The accumulating cost of agent-written code you never fully understood — how to detect, measure, and pay it down before it owns your codebase |
| 25 | Updating Devs in a Smart Way | Agent-generated changelogs, semantic PR summaries, intent-first diffs — keeping humans genuinely informed, not just notified |
| 26 | Semantic Tooling | Tools that operate on meaning, not syntax — semantic search, embedding-aware linters, meaning-preserving refactors, codebase-wide concept graphs |
| 27 | How to Ideate with LLMs | Structured divergent/convergent prompting, using agents as a thinking partner, idea pressure-testing, spec generation from rough intent |
| 28 | Deterministic Design | Making agent outputs reproducible and production-safe — temperature discipline, output schemas, idempotency, regression-proof generation pipelines |
