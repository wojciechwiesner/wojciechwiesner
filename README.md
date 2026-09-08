# Wojciech Wiesner

## Founding & Principal AI Systems Architect · Hands-On Systems Builder

I turn ambiguous business problems into systems that can actually operate.

I architect systems, but I write code hands-on every single day. I genuinely love the craft of coding—the immediate, deterministic feedback loop of the terminal, the compiler, and green test suites is what keeps me grounded, focused, and operating at peak velocity.

Whether I am designing a novel agent runtime or taking on async engineering delivery:
- **Zero ego, zero drama:** I don't lecture your team or push unsolicited rewrites. I respect your existing patterns, conventions, and codebase reality.
- **Surgical async delivery:** I pick up tasks from Linear/Jira, implement clean solutions with regression tests, and submit reviewable PRs without calendar pollution or unnecessary calls.
- **Craft over slides:** I believe real product leadership is impossible without touching the code and understanding runtime failure modes firsthand.

My background spans enterprise data, high-scale operations, company building, product leadership and hands-on AI delivery. I work best close to the business problem: understand it with decision-makers, prototype the shortest useful path, then turn what works into a production system.

Today, at **Application Partner**, I work closely with CFO / executive leadership on business problems that benefit from AI and automation — from rapid prototypes to full end-to-end product delivery.

### Scale I have operated at

**~PLN 3M raised** · **CCC Group strategic investor** · **~14k-driver network** · **61 cities + Prague** · **~20 people hired** · **~10k invoices/month** · **~1.5k automated onboardings** · **4 manufacturing sites under SAP Master Data responsibility**

---

## SOTA products (live)

Operating systems I ship — not slide decks. Screenshots from production, 2026.

### [jit-context](https://github.com/wojciechwiesner/jit-context) · [CERN Zenodo DOI: 10.5281/zenodo.22649542](https://doi.org/10.5281/zenodo.22649542)

**Flagship Architectural Moat:** An Epistemic Context Runtime & JIT OS for AI Agents.

Eliminates context needle-in-a-haystack bloat, prompt drift, and agent hallucinations through a 3-tier cascade: L0 Hot-Path SQLite WAL (<3ms Read-Your-Own-Writes), L1 Scope Hysteresis Guard (<10ms), and L2 Bounded Associative Broker. Governed by 10 strict Epistemic Invariants (I1–I10).

[![CERN Zenodo DOI](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.22649542-107c41?style=flat-square&logo=zenodo&logoColor=white)](https://doi.org/10.5281/zenodo.22649542)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](https://opensource.org/licenses/MIT)
[![Tests: 28/28 PASS](https://img.shields.io/badge/Invariants-10%2F10%20PASS-success?style=flat-square)](https://github.com/wojciechwiesner/jit-context)
[![Speedup: 2.44x](https://img.shields.io/badge/Task_Delivery-2.44x_Faster-orange?style=flat-square)](https://github.com/wojciechwiesner/jit-context#executive-scorecard-verified-empirical-proofs)

#### Verified Empirical Proofs (Paired Production Codebase Run — Synthapse E2E):

| Operational Metric | Standard Long-Context (Control) | JIT-Context OS (Production) | Real Impact / Delta |
| :--- | :--- | :--- | :--- |
| **Wall-Clock Task Delivery** | 9m 27s (567s) | **3m 52s (232s)** | **-59.0% (2.44x faster delivery)** |
| **LLM Inference Turns** | 171 API calls | **66 API calls** | **-61.4% (-105 rounds avoided)** |
| **Total Tool Operations** | 169 actions | **64 actions** | **-62.1% agent churn reduction** |
| **File Read Churn** | 73 reads | **24 reads** | **-67.1% less context thrashing** |
| **Runtime & Test Errors** | 8 error loops | **0 errors (clean)** | **100% first-shot error elimination** |
| **Scope Drift (Collateral Edits)**| 14 files mutated | **4 files (surgical SRP)**| **Zero scope drift** |
| **Prompt Context Size** | >50,000 tokens (Haystack) | **482 tokens (Capsule)** | **>99% token budget preserved** |
| **Read-Your-Own-Writes Latency**| 200–800ms (Vector API) | **<3ms (SQLite WAL)** | **Sub-millisecond local truth** |
| **Epistemic Self-Poisoning** | High (repeats hallucinations)| **Zero (Authority = 0.0)** | **100% grounded in runtime proofs** |

### [TheOnes.io](https://theones.io) · [AI Product Leader](https://theones.io/ai-product-leader)

Portfolio and evidence site: governed AI workflows, case studies, developer passport.

[![TheOnes.io](assets/theones-home.png)](https://theones.io)

[![AI Product Leader](assets/theones-ai.png)](https://theones.io/ai-product-leader)

### [sota-agent-kit](https://github.com/wojciechwiesner/sota-agent-kit)

Public operating kit for coding agents (Hermes / Claude Code / OpenCode): one living `STATE.md`, verified `DONE.md` (SHA + command), VibingDiary, autocheck spots, no secrets in git.

### [Feedby](https://github.com/wojciechwiesner/feedby-public) · [widget](https://github.com/wojciechwiesner/feedby-widget)

Feedback → triage → isolated agent → **reviewable PR** (never auto-merge).

### [InvoiceFlow](https://invoiceflow.apppartner.pl) · [case](projects/invoiceflow/README.md)

**~10,000 invoices/month in production.** Business problem → prototype with finance leadership → full operating workflow.

The model extracts and classifies; deterministic rules decide what is allowed next. No model writes to the ledger unsupervised.

What it does (product, not internals): ingest documents · classify type/vendor/cost · validate against accounting rules · human approval at money boundaries · route to finance systems · keep an audit trail.

[![InvoiceFlow](assets/invoiceflow.png)](https://invoiceflow.apppartner.pl)

### b**c*o — AI-first salon OS (invitation-only MVP)

No public URL. Brand redacted. Private source.

The operator talks to the product in language. The assistant asks only what is missing (who / what / when), then turns intent into a booking — not a 12-field form. Suggestion chips, staff calendar, waitlist, and a feedback loop back into the product. Built as **invitation-only** while the operating loop is proven with real salons.

What is new (product, not stack): language-first operations instead of admin CRUD; the model may propose, the operator confirms; empty fields become questions, not validation errors.

<img src="assets/mvp-ai-mobile.png" width="280" alt="b**c*o AI assistant, mobile, light theme, brand redacted">
<img src="assets/mvp-cal-mobile.png" width="280" alt="b**c*o calendar, mobile, light theme">

### [cmux-remote-tui](https://github.com/wojciechwiesner/cmux-remote-tui) · [agentzero-cli](https://github.com/wojciechwiesner/agentzero-cli)

Operator tools I actually run: remote control of coding-agent terminals over SSH, and a local-first agent TUI with **command interception and approvals** (the model does not get a raw shell).

<img src="assets/cmux-remote-tui.png" width="720" alt="cmux-remote-tui public repo">
<img src="assets/agentzero-cli.png" width="720" alt="agentzero-cli public repo">

---

## Selected systems & production architecture dossiers

In-depth technical architecture dossiers for non-public, enterprise, and internal production systems:

### [jit-context](https://github.com/wojciechwiesner/jit-context) · [CERN Zenodo DOI](https://doi.org/10.5281/zenodo.22649542)
**Architectural Moat: Epistemic Context Runtime & JIT OS for AI Agents.**  
Sub-3ms L0 SQLite WAL (Read-Your-Own-Writes), L1 Scope Hysteresis, L2 Bounded Associative Broker, 10 Epistemic Invariants (I1–I10), and dynamic prompt caching prefix alignment. Delivered 2.44x faster autonomous delivery on production benchmarks.

### [InvoiceFlow](projects/invoiceflow/README.md)
**~10,000 invoices/month in production.**  
Production financial automation pipeline: Vision OCR extraction proposals governed by deterministic gross/net VAT validation, KSeF FA(2) compliance, High-Water Mark deduplication, and enterprise ERP routing.  
*Pattern:* Probabilistic models propose; deterministic engines decide.

### [Onboarding Flow](projects/onboarding-flow/README.md)
**~1,500 people processed with minimal manual intervention.**  
Schema-driven legalisation and onboarding engine handling 108 dynamic datapoints. Decouples complex business and regulatory rules into swappable JSON schemas, eliminating code releases on workflow changes. Built with FastAPI, asyncpg, and iDenfy biometric KYC.

### [Boocco](projects/boocco/README.md)
**AI-first salon operations platform & multi-tenant RAG.**  
Vertical SaaS replacing administrative CRUD with a natural language booking resolver. Features hermetic tenant isolation (PostgreSQL RLS), pgvector HNSW indexing for client context, and deterministic double-booking prevention with 2-way SMS confirmation.

### [Synthapse & KKiK](projects/synthapse/README.md) · [Live Demo](https://synthapse.theones.io)
**Real-time generative AI techno studio with deterministic DSP watchdogs.**  
High-performance browser instrument combining Google Lyria RealTime audio streaming with WebGL shaders and physical Web MIDI hardware control (Akai MPD218 / MIDImix). Enforces sub-bass mono discipline (<120Hz) and transient alignment via real-time DSP analysis.

### [Feedby](projects/feedby/README.md) · [Widget Repo](https://github.com/wojciechwiesner/feedby-widget)
**Closed-loop feedback-to-pull-request multi-agent system.**  
Captures user runtime context in web applications, triages bug reports via vector clustering, and dispatches isolated coding agents to author surgical fixes. Enforces human review at the merge boundary (zero direct commits to main).

### [Arara API](projects/arara-api/README.md)
**Resilient recruitment ops adapter & self-healing REST gateway.**  
Wraps a closed-source legacy recruitment portal in clean FastAPI REST endpoints. Features dual-path authentication (Manifest V3 extension sync + headless Playwright daemon fallback), asyncio mutex locking on token refresh, and automated push-to-HIRED cascades.

### [WhatsApp Command Center](projects/whatsapp-center/README.md)
**Autonomous messaging infrastructure & multi-agent dispatch hub.**  
Production gateway deployed on borg.tools (:3060 / :3050) bridging WhatsApp channels with autonomous agent triage. Features persistent Baileys WebSocket connection, automatic Opus audio note transcription via Whisper, and idempotent event routing to Telegram topics.

### [Tuli.my](projects/tuli-my/README.md)
**Privacy-first relational intelligence PWA & tiered model gateway.**  
Event-sourced progressive web app with cryptographic consent boundaries. Employs a multi-tier model gateway (Groq Llama 70B / Gemini Flash / Frontier) that slashes token inference costs by >70% while guaranteeing that private reflections never leak across scopes.

### [UniPro OS & Insight](projects/unipro/README.md)
**Policy-bounded desktop telemetry & Plan JSON execution compiler.**  
Enterprise automation architecture: screen observation extracts activity primitives, while a deterministic OS compiles intent into validated Plan JSON before invoking system automation APIs.

### [Xpress Delivery](projects/xpress-delivery/README.md)
**Technology-enabled same-day delivery platform across 61 cities + Prague.**  
Logistics network and internal dispatch platform: co-founded, raised ~PLN 3M, secured CCC Group as strategic investor, hired ~20 people, and led product/software delivery.

---

## Public tools I actually use / built for real workflows

### [jit-context](https://github.com/wojciechwiesner/jit-context)
Epistemic Context Runtime & JIT OS for AI Agents. Sub-3ms SQLite WAL, 10 epistemic invariants, CERN Zenodo DOI.

### [cmux-remote-tui](https://github.com/wojciechwiesner/cmux-remote-tui)
Remote control plane for agent-heavy terminal workflows. Lets me monitor and interact with multiple coding-agent terminals running on an always-on machine over SSH.

### [Agent Zero CLI](https://github.com/wojciechwiesner/agentzero-cli)
Local-first coding-agent CLI with command interception, approval boundaries and multiple model backends. Packaged for PyPI.

### [Feedby Widget](https://github.com/wojciechwiesner/feedby-widget)
Embeddable feedback widget used as the client-side part of a feedback → context → AI triage → reviewable change workflow.

### [MCP Agent Bridge](https://github.com/wojciechwiesner/mcp-agent-bridge)
Bidirectional MCP bridge connecting coding-agent ecosystems and tool interfaces across different execution environments.

---

## How I build

```text
listen → decompose → model → prototype → constrain → build → automate → observe → improve
```

I use AI aggressively to compress research, prototyping and implementation time. I do **not** use it as an excuse to remove deterministic controls from consequential workflows.

I deliberately separate:

- ambiguity that benefits from probabilistic models,
- state and rules that should remain deterministic,
- actions that require validation or policy boundaries,
- decisions that should remain human.

I also run rapid 0→1 product experiments to shorten the distance between an idea and market feedback. My personal speed record is roughly **2 hours from idea → working WordPress plugin → product page → live checkout**.

---

## Background

Before AI-native product work, I spent years operating real systems at scale:

- **Application Partner** — AI Developer / product & technology operator; direct work with CFO and executive leadership; business problem discovery, rapid prototypes and end-to-end AI/automation delivery.
- **Xpress Delivery (2018–2025)** — co-founder / CEO-CVO; product and technology direction, development-team delivery, enterprise customers, fundraising and multi-city operations.
- **2016–2022** — founder/operator of a ~14k-driver logistics network and internal settlement/accounting system.
- **2 Sisters Food Group, UK (2010–2012)** — SAP Master Data Specialist with independent responsibility across four manufacturing sites.

In 2022 I was recognised by **BRIEF among the 50 Most Creative People in Business**.

---

## Links

- **Portfolio / case studies:** https://theones.io/case-studies
- **Direct inquiries:** wojciech@theones.io

> Production/customer repositories remain private where they contain proprietary code or operational details. This profile intentionally highlights systems and tools that best represent how I build.
