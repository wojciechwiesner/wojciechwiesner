# Feedby — Autonomous Feedback-to-Pull-Request Platform

> Closed-loop developer tooling that converts user bug reports and UI friction into reviewable, tested pull requests at the merge boundary.

**Role:** Product Architect & Systems Engineer  
**Stack:** TypeScript (Vite Widget) · Python (FastAPI Engine) · Claude Code SDK · Agent Zero · cmux Multiplexer · PostgreSQL + pgvector · GitHub API  
**Status:** Active pilot; open-source widget + proprietary agent orchestration engine  

---

## 1. The Business Problem

In high-velocity software products, the user feedback loop is broken:
- **The Backlog Graveyard:** User bug reports and friction points sit in Jira or Zendesk queues for weeks before an engineer ever reads them.
- **Context Loss:** By the time a developer picks up a ticket, the user's browser environment, reproduction steps, and exact DOM state are lost.
- **Agent Hallucination Risk:** Unleashing autonomous coding agents directly on production repositories frequently causes catastrophic regressions, prompt drift, or corrupted business logic.

Feedby solves this by turning user reports into surgical, review-gated Pull Requests in minutes instead of weeks.

---

## 2. Multi-Agent Architecture & The Merge Gate

```text
User Submits Feedback (Feedby Widget captures DOM + console + network logs)
                               ↓
                   FastAPI Triage & Vector Clustering
             (pgvector semantic deduplication & prioritization)
                               ↓
                       Multi-Agent Harness
         ┌──────────────────────────────────────────────┐
         │ 1. Triage Agent: Classifies bug vs feature   │
         │ 2. Localization Agent: Finds culprit files   │
         │    (Scoped via JIT Context OS to prevent     │
         │     prompt drift and broad codebase scans)   │
         │ 3. Execution Agent: Implements minimal fix   │
         │ 4. Verification Agent: Runs test suite       │
         └──────────────────────┬───────────────────────┘
                                ↓
                 Reviewable GitHub Pull Request
     (Detailed description + reproduction proof + green CI tests)
                                ↓
                     Human Engineer Merge Gate
             (Zero unsupervised writes to production main)
```

### Architectural Principles:
1. **The Merge Boundary Invariant:** Feedby agents never push directly to `main` or trigger automated deploys. Every agent output is isolated on a feature branch (`fix/feedby-*`) and submitted as a clean Pull Request with full test coverage for human sign-off.
2. **JIT Context Scoping:** Autonomous coding agents frequently fail because they read too much irrelevant code and hallucinate fixes in unrelated modules. Feedby uses JIT context capsules to restrict agent attention strictly to the affected component and its immediate interface boundaries.
3. **Telemetry & Autocheck Spots:** Every triage decision and code modification produces observable structured logs in the central dashboard, enabling immediate intervention if an agent proposes an invalid plan.

---

## 3. What I Owned & Delivered

- **Full Multi-Agent Pipeline:** Built the orchestration bridge coordinating Claude Code, Agent Zero, and cmux terminal runners across isolated worker processes.
- **Embeddable Client Widget:** Authored the zero-dependency, ultra-lightweight TypeScript widget with DOM capture, session replay, and user rating components.
- **Automated Regression Test Synthesis:** Engineered the prompt harness that forces execution agents to write a failing test before authoring the code fix, proving the remediation in CI.

---

*Public architecture dossier. Widget components available in open-source; multi-agent dispatch harness and backend API proprietary.*
