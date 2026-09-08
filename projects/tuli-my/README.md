# Tuli.my — Privacy-First Relational Intelligence PWA

> Event-sourced Progressive Web App with tiered model routing, cryptographic consent boundaries, and local-first context isolation.

**Role:** Creator & Lead Systems Architect  
**Stack:** TypeScript · Next.js PWA · Python (FastAPI Gateway) · PostgreSQL (Event Sourcing) · Web Push API · Stripe  
**Status:** Private MVP; proprietary architecture and source code  

---

## 1. The Architectural Challenge

Consumer AI products dealing with relationships, therapy prep, or intimate personal reflection face severe engineering paradoxes:
- **The Context Leakage Nightmare:** In multi-user or partner workflows, personal reflections must NEVER bleed into a shared summary without explicit, affirmative consent.
- **Runaway Token Economics:** Monolithic RAG pipelines feeding entire relationship histories into frontier models (Claude Opus / GPT-4o) on every turn make consumer subscription pricing unsustainable.
- **Data Sovereignty:** Users will not trust cloud AI with sensitive personal thoughts unless privacy is guaranteed by system architecture rather than legal disclaimers.

---

## 2. Architecture: Event Sourcing + Tiered Model Gateway

Tuli.my solves these challenges through an **event-sourced core with strict cryptographic consent gates and cost-tiered model routing**:

```text
User Interaction (Journaling, Reflection, Partner Communication)
                               ↓
                   Cryptographic Consent Gate
         (Verifies scope: Strictly Solo vs Partner-Consented)
                               ↓
                     Event-Sourced Journal
               (Append-only immutable audit trail)
                               ↓
                     Tiered AI Gateway Hub
         ┌──────────────────────────────────────────────┐
         │ Tier 1: Fast Categorizer (Groq Llama 70B)    │
         │ - Instant sentiment & topic tagging (<150ms) │
         ├──────────────────────────────────────────────┤
         │ Tier 2: Deep Reflection (Gemini 3.7 Flash)    │
         │ - Bounded situational synthesis              │
         ├──────────────────────────────────────────────┤
         │ Tier 3: Complex Mediation (Frontier Tier)    │
         │ - High-EQ conflict reframing & boundary work │
         └──────────────────────┬───────────────────────┘
                                ↓
             PWA Client Delivery & Web Push Alert
```

### Key Technical Innovations:
1. **Event-Sourced Data Model:** State is never overwritten. Every reflection, mood shift, and consent grant is recorded as an immutable event in PostgreSQL, enabling complete point-in-time auditing and zero state resurrection.
2. **Tiered Model Routing Engine:** By breaking agent queries into distinct cognitive layers, 80% of routine interactions are handled by ultra-fast, cost-effective inference endpoints, slashing per-user token expenditure by over 70%.
3. **Hermetic Consent Boundaries:** The context compiler enforces a hard rule: if `consent_status != "CONSENT_SHARED"`, personal journals are physically excluded from partner prompts at the database query layer, making accidental data leakage structurally impossible.

---

## 3. What I Owned & Delivered

- **End-to-End System Design:** Conceived the event-sourced data model, consent state machine, and tiered AI Gateway architecture.
- **Progressive Web App:** Built a high-contrast, distraction-free mobile PWA with offline journaling, local caching, and Web Push notifications.
- **Agent-Ready MCP Integration:** Designed Model Context Protocol (MCP) server endpoints allowing external trusted agents to interact with permitted life context safely.

---

*Public architecture dossier. Proprietary source code and personal user records remain strictly confidential.*
