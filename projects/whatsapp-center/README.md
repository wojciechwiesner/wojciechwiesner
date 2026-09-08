# WhatsApp Command Center — Autonomous Communication & Multi-Agent Dispatch

> Production messaging infrastructure connecting high-volume WhatsApp channels to autonomous AI triage, customer workflows, and operational alerting.

**Role:** Infrastructure Architect & Lead Systems Builder  
**Stack:** Node.js (Baileys Engine) · Python 3.11 (FastAPI Hub) · PostgreSQL · WebSocket · PM2 · Docker · Tailscale  
**Status:** Production communication gateway deployed on borg.tools (:3060 / :3050); proprietary source code  

---

## 1. The Operational Problem

For modern service businesses and logistics operators, WhatsApp is the dominant communication channel for clients, drivers, and partners:
- **Unstructured Message Deluge:** Inbound messages arrive as raw voice notes, location pins, photos of documents, and unstructured text at all hours.
- **Fragile Cloud API Limitations:** Official WhatsApp Business Cloud APIs are restrictive, costly per conversation, and difficult to customize for deep developer tooling or real-time agent interception.
- **Sync & State Fragility:** Unreliable WebSocket connections frequently cause dropped messages, duplicate replies, or session de-authentication.

The business needed a self-hosted, resilient gateway capable of real-time multi-agent triage, audio transcription, and deterministic routing.

---

## 2. Architecture & Processing Flow

```text
Inbound WhatsApp Message (Text, Voice Note, Image, Location Pin)
                               ↓
       WhatsApp Connector (Node.js + Baileys Engine :3050)
        (Persistent multi-device session, WebSocket keeper)
                               ↓
         FastAPI Command Center & Dispatch Hub (:3060)
         (Idempotency check, media extraction & storage)
                               ↓
         ┌──────────────────────────────────────────────┐
         │ 1. Voice Note Pipeline: Fast Whisper STT     │
         │ 2. Semantic Triage: Classifies intent        │
         │    (Support / Booking / Hiring / Escalation) │
         │ 3. Policy & Guardrail Engine:                │
         │    Ensures response safety and compliance   │
         │ 4. Operator Bridge: Instant alert to         │
         │    Telegram Topic / Web Dashboard            │
         └──────────────────────┬───────────────────────┘
                                ↓
                 Deterministic Action & Outbound Reply
```

### Key Technical Achievements:
1. **Decoupled Two-Tier Architecture:**
   - *Connector Layer (`wa-connector` on :3050):* Low-level Node.js service managing the live Baileys WhatsApp protocol state, QR-code authentication, message deduplication, and raw socket reconnection.
   - *Command Center Layer (`wa-center` on :3060):* High-level Python service orchestrating business rules, LLM triage, webhook dispatch, and database persistence.
2. **Audio Voice-Note Transcription:** Automatically downloads incoming `.ogg`/Opus audio notes, transcodes them via FFmpeg, and transcribes them via local Whisper/Groq APIs in under 2 seconds, passing structured text to the triage agent.
3. **Strict Idempotency & Delivery Safety:** Every inbound message hash is checked in SQLite/PostgreSQL before processing to ensure zero duplicate responses, even during rapid network reconnections.

---

## 3. What I Owned & Delivered

- **Architecture & Service Implementation:** Built both microservices from scratch, integrating the Node.js Baileys socket engine with the Python FastAPI dispatch plane.
- **Media Pipeline & Transcoding:** Engineered the automatic media downloader and streaming audio transcription pipeline.
- **Production DevOps:** Deployed on production host (`borg.tools`), monitored via PM2 with automatic health check recovery and secure Tailscale private routing.

---

*Public architecture dossier. Phone numbers, session tokens, and client conversation records remain strictly confidential.*
