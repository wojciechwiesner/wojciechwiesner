# Boocco — AI-First Salon Operations Platform

> Multi-tenant SaaS platform integrating calendar engine, client CRM, and tenant-scoped pgvector RAG assistant for independent beauty businesses.

**Role:** Product Architect & Lead Systems Engineer  
**Stack:** Next.js 14 · TypeScript · PostgreSQL + pgvector (HNSW) · Self-Hosted Supabase · Tailwind CSS · PM2  
**Status:** Invitation-only MVP in production validation; proprietary source code  

---

## 1. The Business Problem

Independent salons and aesthetic clinics are caught in a painful structural trap:
1. **Predatory Marketplace Commissions:** Big booking marketplaces (Booksy, Treatwell) charge heavy recurring fees and siphon loyal salon clients into competitor recommendations.
2. **Convoluted Enterprise Software:** Legacy management tools are bloated with complex forms, rigid scheduling tables, and 12-field manual booking inputs that stall busy non-technical operators.

The salon operator needs an operating system where a booking can be made in natural language in under 5 seconds, client histories are instantly recalled, and scheduling conflicts are resolved deterministically.

---

## 2. Architecture & Operating Loop

Boocco replaces manual administrative CRUD forms with a **conversational booking resolver backed by deterministic relational integrity**:

```text
Client Message / Staff Request ("Book Gosia for balayage next Thursday at 3pm")
                           ↓
              Context-Aware AI Assistant
         (pgvector HNSW + Tenant Scope RLS)
                           ↓
            Deterministic Slot & Conflict Resolver
       (Staff working hours, buffer times, station locks)
                           ↓
                  Interactive Proposal
        (Presents resolved slot + price + client notes)
                           ↓
            Operator Confirmation & 2-Way SMS
          (Database write + SMS webhook dispatch)
```

### Architectural Highlights:
- **Language-First Operations:** The assistant asks only for strictly missing datapoints (who, what, when) rather than rejecting requests with validation errors.
- **Hermetic Multi-Tenant Scoping:** PostgreSQL Row-Level Security (RLS) ensures that embeddings and salon records never bleed across tenant boundaries.
- **Deterministic Booking Resolver:** LLMs propose appointments; deterministic PostgreSQL stored procedures and TypeScript state machines verify staff availability, station equipment, and double-booking invariants before any database commit.
- **Two-Way SMS Synchronization:** Automated appointment confirmations and reminders with incoming client response parsing.

---

## 3. What I Owned & Delivered

- **Full Product & System Architecture:** Designed the data model, multi-tenant schema, and appointment lifecycle state machine.
- **Self-Hosted Supabase & Infrastructure:** Deployed and optimized PostgreSQL with pgvector on production servers, implementing HNSW index tuning for sub-10ms similarity search.
- **Frontend & PWA Experience:** Built an ultra-fast, mobile-first Next.js interface tailored for fast one-thumb operation by hair stylists and salon managers between client appointments.
- **Pragmatic Build-vs-Buy Balance:** Integrated off-the-shelf foundation models via structured function calling while writing bespoke scheduling conflict algorithms where business differentiation lives.

---

## 4. Key Engineering Invariants

- **Zero Unsupervised State Changes:** AI suggestions are presented as one-tap confirmation chips; no booking is finalized without operator approval.
- **Idempotent Webhooks:** External communication and payment hooks are protected by unique event hashes to eliminate duplicate notifications.
- **Fast Local Execution:** RAG queries against client preferences, formula notes, and past visits execute in under 50ms.

---

*Public architecture dossier. Proprietary source code, integration keys, and salon client databases remain strictly confidential.*
