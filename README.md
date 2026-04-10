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

---

## Categories (rotating — 33 total)

Each tip belongs to one of 30 categories, cycling in order by tip number. Every category has a defined **purpose** — the problem it addresses — and a **definition** — the precise scope of what belongs in it.

---

### 0 · Context Management
**Purpose:** Agents are only as good as what you hand them. Most agent failures are context failures — too much, too little, or the wrong slice entirely. This category teaches you to treat context as a first-class architectural concern, not an afterthought.
**Definition:** Structuring codebases so that any feature's complete picture fits a single coherent context window. Covers AGENTS.md living contracts, feature-co-located folder structures, barrel exports as agent manifests, and context budgeting discipline.

---

### 1 · API Design
**Purpose:** A well-typed API surface is a machine-readable spec. When your routes, schemas, and service functions are self-documenting, agents can extend, debug, and test them without asking you to explain the business logic.
**Definition:** Designing SvelteKit APIs for agent legibility — Zod schemas as the single source of truth, derived TypeScript types, 1:1 REST-to-service naming, typed `ApiSuccess<T>` / `ApiError` envelopes, and auto-generated OpenAPI from schemas.

---

### 2 · Prompt Engineering
**Purpose:** Prompts are code. Vague prompts produce vague results. This category treats prompt design with the same rigor as software design — composable, testable, version-controlled.
**Definition:** Building prompt chains, few-shot templates, system prompt conventions, and design-system priming patterns. Covers prompt versioning, chain-of-thought structuring, and the difference between a prompt that works once and one that works reliably.

---

### 3 · Agent Tooling
**Purpose:** An agent is only as powerful as the tools it can call. Most devs underinvest in their tool layer, leaving agents to work with blunt instruments when precision tools exist.
**Definition:** Building and configuring agent tools — MCP servers, custom function schemas, tool-use patterns, and multi-agent orchestration. Covers when to build a tool vs. when to refine a prompt, and how to design tool interfaces that agents use correctly on the first call.

---

### 4 · Data Architecture
**Purpose:** Agents that touch data without a principled data layer produce inconsistent, hard-to-debug results. A clean data architecture makes your entire system — agent and human alike — more predictable.
**Definition:** Designing data layers for LLM-assisted applications — PostgreSQL schema design, DuckDB for analytics, Drizzle ORM patterns, migration strategies, and analytics pipelines. Covers data modeling decisions that affect how easily agents can reason about and manipulate your data.

---

### 5 · Design Systems
**Purpose:** Without a design system, every agent-generated UI component is a snowflake. With one, every component is a coherent, predictable piece of the same system.
**Definition:** Building and maintaining design systems that agents can consume and produce — Tailwind token architecture, component library conventions, design-to-code workflows, and the file formats and prompt patterns that let an agent generate on-brand components reliably.

---

### 6 · DevOps & Infra
**Purpose:** Agents can write code that deploys itself — but only if your infra is clean enough for them to reason about. This category closes the loop between code generation and production.
**Definition:** CI/CD pipelines that incorporate agents, deployment patterns for Railway/Docker/monorepos, environment management, and infra-as-code practices that make your stack agent-navigable. Covers when to let agents trigger deployments and how to gate them safely.

---

### 7 · Testing & Quality
**Purpose:** Agent-written code without tests is liability, not an asset. This category turns testing from an afterthought into a first-class agent output.
**Definition:** Using agents to write, run, and maintain tests — snapshot testing, type coverage enforcement, Playwright E2E, and agent-assisted regression detection. Covers how to prompt for testable code, not just code that works.

---

### 8 · Knowledge Bases
**Purpose:** Agents with no persistent memory repeat themselves, forget decisions, and lose context between sessions. A well-built knowledge base turns a stateless agent into a system that learns and accumulates.
**Definition:** Designing RAG pipelines, vector stores, embedding strategies, and agent memory architectures for SvelteKit applications. Covers chunking strategies, retrieval quality, and how to make a knowledge base that agents actually query correctly.

---

### 9 · Documentation
**Purpose:** Documentation written after the fact is often wrong. Documentation written by the agent that wrote the code is accurate by construction. This category makes docs a first-class output.
**Definition:** Auto-generating and maintaining documentation with agents — JSDoc, OpenAPI specs, README generation, architecture decision records (ADRs), and living docs that stay in sync with the codebase. Covers how to structure code so documentation writes itself.

---

### 10 · Webdesign & Styling
**Purpose:** Agent-generated UI tends toward functional but ugly. This category teaches agents to produce components that are both correct and visually intentional.
**Definition:** Guiding agents through visual design decisions — Tailwind best practices, responsive design patterns, component aesthetics, spacing systems, and the prompt techniques that produce design-system-compliant output instead of arbitrary utility class soup.

---

### 11 · Best Dev Tools
**Purpose:** The tooling landscape for LLM-assisted development moves faster than any one developer can track. This category is a curated monthly signal cut through the noise.
**Definition:** Monthly spotlight on the highest-value tools for agentic development — editors, IDE extensions, CLIs, SaaS services, and open-source utilities. Each tip evaluates a tool on: what problem it solves, how it fits into an agent workflow, and whether it's worth the switching cost.

---

### 12 · Agent Workflow & Context
**Purpose:** Most agent interactions are one-shot. Production-grade agentic work is a pipeline — with stages, handoffs, state, and recovery paths. This category designs those pipelines.
**Definition:** Architecting multi-step agent workflows — task decomposition, state handoff between agent calls, human-in-the-loop checkpoints, error recovery strategies, and context preservation across a session or across days.

---

### 13 · Innovation
**Purpose:** The frontier of agentic development moves fast. This category gives you the signal before it becomes mainstream — the patterns that senior engineers are quietly shipping before anyone writes a blog post about them.
**Definition:** Cutting-edge techniques, emerging paradigms, and early-adopter patterns in LLM-assisted development. Covers novel use cases, experimental toolchains, and the ideas that feel like they shouldn't work yet — but do.

---

### 14 · Pure Creativity
**Purpose:** Agents are not just code generators — they are creative collaborators. This category explores what happens when you stop using agents to execute plans and start using them to help invent them.
**Definition:** Unconventional, generative, and experimental uses of LLM agents in development — generative UI, procedural content, creative coding, unexpected combinations of agent capabilities, and the projects that exist at the edge of what's currently possible.

---

### 15 · Agent Self-Learning
**Purpose:** The best agent setup today should not be the same as tomorrow. This category teaches you to build systems where agents get better over time — without manual intervention.
**Definition:** Architectures and patterns for agent improvement — self-reflection loops, output evaluation pipelines, meta-prompting, fine-tuning feedback collection, and how to build a dev workflow where each agent interaction makes the next one smarter.

---

### 16 · Agent-to-Agent Interactions
**Purpose:** Single agents hit capability ceilings. Multi-agent systems break through them — but only when the inter-agent communication is designed, not improvised.
**Definition:** Designing systems where multiple agents collaborate — orchestrator/sub-agent patterns, inter-agent message schemas, capability delegation, conflict resolution, and the failure modes unique to multi-agent pipelines (cascading errors, context pollution, circular delegation).

---

### 17 · Optimizing DX
**Purpose:** The best agent output in the world doesn't matter if the developer experience around it is slow, confusing, or error-prone. DX is a force multiplier on everything else.
**Definition:** Reducing friction in agent-assisted development workflows — faster feedback loops, better editor integration, smarter defaults, CLI ergonomics, and the small tooling decisions that compound into large productivity differences over time.

---

### 18 · Build Internal Tools for LLM
**Purpose:** LLM workflows need infrastructure — dashboards to monitor costs, admin UIs to manage prompts, portals to inspect outputs. Most teams build these ad-hoc or not at all.
**Definition:** Designing and building internal tooling specifically for LLM-powered systems — prompt management UIs, cost dashboards, output inspection portals, evaluation harnesses, and the SvelteKit + TypeScript patterns that make these tools fast to build and easy to maintain.

---

### 19 · Failure Archaeology
**Purpose:** Every agent failure contains a lesson. Most developers delete the bad output and try again. This category teaches you to mine failures instead — turning errors into prompts, prompts into tests, and tests into guardrails.
**Definition:** Systematic analysis of past agent failures — building typed error taxonomies, creating regression suites from real failure cases, extracting implicit prompt requirements from outputs that went wrong, and maintaining a "failure library" that makes your system incrementally harder to break.

---

### 20 · Cognitive Load Engineering
**Purpose:** A correct agent output that takes 20 minutes to verify costs more than it saves. This category optimizes the human side of the human-agent loop — making outputs faster to review, easier to trust, and cheaper to reason about.
**Definition:** Designing agent interactions for minimal human cognitive overhead — structured diff outputs instead of full rewrites, typed return shapes that parse at a glance, self-documenting code that doesn't require reading, and the prompt patterns that produce outputs a developer can approve in seconds, not minutes.

---

### 21 · Temporal Reasoning & State Drift
**Purpose:** Agents have no sense of time. They don't know your codebase changed yesterday, that the API they're targeting was deprecated last week, or that the pattern they're suggesting was removed from your AGENTS.md two sprints ago. This category solves that.
**Definition:** Anchoring agents to the current state of a system — versioned context injection, freshness signals, stale assumption detection, and time-aware prompts. Covers how to build agent workflows that degrade gracefully when context is stale rather than confidently producing wrong answers.

---

### 22 · The Economics of Agent Time
**Purpose:** Agents are not free. Token costs, latency, and human review time are real expenses. Most teams have no model for when agentic approaches produce positive ROI and when they don't — so they apply agents everywhere or nowhere.
**Definition:** Building an economic model for agentic development — token budgeting, cost-per-feature measurement, latency profiling, human review time accounting, and the decision framework for when to reach for an agent vs. write it yourself. Covers how to present ROI arguments to non-technical stakeholders.

---

### 23 · Adversarial Prompting as a Design Tool
**Purpose:** Every prompt has failure modes. Most developers discover them in production. This category teaches you to find them first — by deliberately trying to break your own system before users do.
**Definition:** Applying adversarial and red-teaming techniques to prompt design — systematic edge case generation, input fuzzing for prompts, assumption surfacing, and building a pre-production adversarial test suite for every critical agent interaction. Covers the failure modes unique to LLMs: confident wrongness, instruction hijacking, and context poisoning.

---

### 24 · Comprehension Debt
**Purpose:** Technical debt is tracked. Comprehension debt — the code that passes review because it looks right, but that nobody actually understands — is invisible until it fails catastrophically. Agent-written code accelerates its accumulation.
**Definition:** Detecting, measuring, and paying down comprehension debt in agent-assisted codebases — identifying code with high complexity but zero tests, orphaned types, undocumented side effects, and the patterns that signal "an agent wrote this and nobody checked." Covers strategies for systematic comprehension paydown without stopping feature work.

---

### 25 · Updating Devs in a Smart Way
**Purpose:** Most team updates are noise — notifications that something changed, not communication about what it means. Agents can generate updates that actually inform, not just notify.
**Definition:** Using agents to produce genuinely useful developer communications — intent-first PR summaries, semantic changelogs that explain *why* not just *what*, architecture decision digests, and the diff formats that let a developer understand a change in 60 seconds instead of 20 minutes. Covers the prompt patterns that produce signal, not boilerplate.

---

### 26 · Semantic Tooling
**Purpose:** Syntax-aware tools (TypeScript, ESLint, Prettier) are table stakes. The next generation of dev tooling operates on *meaning* — understanding what code does, not just how it's structured. This category gets you there first.
**Definition:** Tools and techniques that operate on semantic content rather than syntax — embedding-based codebase search, meaning-preserving refactoring agents, concept graphs that map relationships between features, and the infrastructure for making your entire codebase queryable by meaning. Covers how to build semantic tooling into a SvelteKit workflow.

---

### 27 · How to Ideate with LLMs
**Purpose:** Developers use agents to execute. Almost none use them to *think*. The highest-leverage use of an agent is often not writing code — it's pressure-testing an idea before a line of code is written.
**Definition:** Structured ideation techniques using LLMs — divergent/convergent prompt patterns, spec generation from rough intent, assumption stress-testing, competing-spec generation from the same brief, and the facilitation techniques that turn a solo brainstorm into a genuinely creative dialogue. Covers how to use an agent to escape your own blind spots.

---

### 28 · Deterministic Design
**Purpose:** Agents are stochastic by default. Production systems cannot be. The gap between "it works when I try it" and "it works every time" is closed by deterministic design — and most teams never close it.
**Definition:** Making agent outputs reproducible, testable, and production-safe — temperature and sampling discipline, strict Zod output schemas for agent responses, idempotency patterns for agent-triggered side effects, seed management, and the pipeline architecture that guarantees the same input always produces the same output. Covers how to build generation systems you can regression-test.

---

### 29 · In 5 Years From Now
**Purpose:** The decisions you make today compound. A developer who understands where agentic tooling is heading in 5 years makes better architectural choices right now — not because they're building for the future, but because they understand the direction of travel.
**Definition:** Forward-looking analysis of where LLM-assisted development is heading — emerging agent capabilities, the skills that will compound in value, the patterns being built today that will be standard practice in 2030, and the things that feel experimental now but will be table stakes soon. Each tip is grounded in current trajectory, not speculation.

---

### 30 · LLM Data & Logs
**Purpose:** LLMs produce a stream of observable signal — token counts, latencies, input/output pairs, confidence patterns, failure signatures — that almost no team captures systematically. The teams that do build compounding advantages: they know what's expensive, what's failing, and what's improving over time. Without logs, you are flying blind in production.
**Definition:** Capturing, storing, and making sense of LLM runtime data — structured logging of prompts and completions, token usage tracking, latency profiling, cost attribution per feature or user, error rate monitoring, and building dashboards that make this data actionable. Covers the schema design for LLM log tables, retention strategies, and how to use historical data to improve prompts and reduce cost.

---

### 31 · LLM Hooks
**Purpose:** Most LLM integrations are fire-and-forget. Hooks let you intercept the LLM lifecycle — before a prompt is sent, after a response arrives, when an error occurs — and attach logic at each stage. This is how you build observability, guardrails, caching, rate limiting, and fallback strategies without tangling that logic into your application code.
**Definition:** Designing and implementing lifecycle hooks around LLM calls — pre-request hooks (prompt mutation, context injection, PII scrubbing), post-response hooks (output validation, logging, caching, formatting), and error hooks (fallback model routing, retry logic, alerting). Covers the middleware patterns, TypeScript interfaces, and SvelteKit integration points that make hooks composable and testable.

---

### 32 · LLM Integrations
**Purpose:** An LLM sitting in isolation is a demo. An LLM wired into your database, your auth layer, your external APIs, and your UI state is a product. Most integration complexity is not in the LLM call itself — it's in the plumbing around it. This category teaches you to build that plumbing cleanly.
**Definition:** Connecting LLMs to the rest of your stack — integrating with third-party APIs (Stripe, Resend, GitHub, Notion), database-backed context injection, auth-aware prompt construction, streaming responses into SvelteKit UI, webhook-triggered agent workflows, and the patterns that keep integrations loosely coupled and easy to swap. Covers the adapter pattern for LLM providers, so switching models doesn't break your app.
