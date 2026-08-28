# InvoiceFlow

> Production AI-assisted document workflow for high-volume invoice processing.

**Scale:** ~10,000 invoices/month  
**Role:** product discovery, architecture, implementation and production delivery  
**Environment:** enterprise finance operations  
**Status:** production system; source code is private/proprietary

## Business problem

Invoice processing combined high document volume, inconsistent inputs, accounting rules, approvals and multiple downstream systems. A pure LLM pipeline would be too difficult to audit and too risky to let execute financial actions directly.

## Approach

InvoiceFlow separates probabilistic interpretation from deterministic execution:

```text
invoice / attachment
       ↓
AI extraction + classification
       ↓
normalization + deterministic validation
       ↓
business rules + history + approval boundaries
       ↓
routing / accounting integrations / audit trail
```

The model can propose what a document contains. The surrounding system decides what is valid and what is allowed to happen next.

## What the product does

- ingest invoices and attachments at volume (~10k/month);
- extract fields and **classify** document / vendor / cost nature;
- **validate** against accounting rules before any side effect;
- require **human approval** at money boundaries;
- **route** into finance operations (ERP / work management);
- keep an **audit trail** of propose → validate → decide.

The model can propose. It does not post unsupervised.

Source, parsers, prompts and integration maps stay private.

## What I owned

- translated finance and operational problems into the product/workflow design;
- prototyped solutions directly with business stakeholders and executive leadership;
- designed the AI + deterministic validation architecture;
- built and integrated the production workflow;
- introduced testable rules, routing, approvals and observable state;
- iterated from real production failures instead of treating the model as the source of truth.

## Engineering principles

- deterministic controls around probabilistic outputs;
- explicit state and auditability;
- schema validation before side effects;
- human approval at consequential boundaries;
- production feedback loops and regression tests;
- integrations treated as part of the product, not an afterthought.

## Stack

Python · FastAPI · PostgreSQL · vision/LLM models · APIs · Monday.com · accounting/finance integrations · automated tests

## Why this project matters

InvoiceFlow is representative of how I work on AI systems: start with an operational problem, prototype quickly, then turn the useful behavior into a constrained production system that the business can actually rely on.

---

Public case study only. Implementation details and source code remain private.