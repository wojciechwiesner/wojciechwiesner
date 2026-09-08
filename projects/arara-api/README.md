# Arara API — Resilient Recruitment Ops & Legacy System Adapter

> Production FastAPI service modernizing a legacy, closed-source recruitment backoffice into an automated REST gateway with self-healing authentication.

**Role:** Systems Architect & Backend Engineer  
**Stack:** Python 3.11 · FastAPI · Playwright (Headless Automation) · Chrome Extension (Manifest V3) · Docker Compose · Nginx · Telegram Bot API  
**Status:** Production microservice handling daily hiring cascades; proprietary implementation  

---

## 1. The Operational Problem

A nationwide logistics operator’s candidate pipeline was bottlenecked inside a third-party legacy backoffice web portal:
- **No Public API:** All candidate data, status updates, and hiring triggers were locked behind complex web forms requiring constant manual clicking.
- **Aggressive Session Expiration:** Operator auth tokens expired multiple times per day without warning, breaking bulk hiring actions mid-stream.
- **Manual Cascade Bottlenecks:** Advancing hundreds of drivers through background checks, vehicle assignments, and onboarding handoffs created hours of administrative toil every week.

Rewriting the legacy platform was economically unfeasible; the solution was to build an indestructible API adapter around it.

---

## 2. Architecture: Self-Healing Dual-Path Gateway

Arara API exposes clean, modern REST endpoints to internal tools while managing legacy session state and browser automation behind the scenes:

```text
Internal Webhook / Pipeline Trigger ("Advance Candidate #4920 to HIRED")
                           ↓
                   FastAPI Microservice
         (Request validation, role enforcement, audit log)
                           ↓
             Token Lifecycle & Session Manager
         ┌───────────────────────────────────────┐
         │ Primary Path: Live Session Mirroring  │
         │ (Manifest V3 Chrome Extension syncs   │
         │  authenticated operator cookies)      │
         ├───────────────────────────────────────┤
         │ Fallback Path: Headless Daemon        │
         │ (Playwright automation with mutex     │
         │  lock and exponential backoff)        │
         └───────────────────┬───────────────────┘
                             ↓
              Legacy Backoffice HTTP Layer
         (Direct REST/XHR emulation with retries)
                             ↓
               Candidate Hired + Telegram Alert
```

### Key Technical Achievements:
1. **Dual-Path Authentication Engine:**
   - *Active Session Mirroring:* A lightweight Manifest V3 Chrome extension securely mirrors active operator session cookies to the gateway when a human is logged in.
   - *Autonomous Headless Fallback:* If no human is online, a headless Playwright daemon automatically navigates the login flow, solves authentication challenges, and updates the shared token store.
2. **Mutex-Locked Token Refresh:** When token expiry (HTTP 401/403) is detected, all concurrent incoming requests are queued behind an asyncio Mutex. A single worker executes token renewal, after which queued requests replay automatically without throwing errors downstream.
3. **Automated Status Cascades:** A single API call (`POST /candidates/{id}/hire`) atomically verifies document checklists, assigns driver ID tags, pushes status updates, and triggers downstream onboarding notifications.

---

## 3. What I Owned & Delivered

- **Full Reverse Engineering & API Design:** Mapped internal XHR payloads, CSRF token exchanges, and undocumented backend constraints.
- **Resilient Microservice Implementation:** Built the FastAPI service, asyncio queue workers, and self-healing token lifecycle manager.
- **Chrome Extension & Playwright Scraper:** Authored both the Manifest V3 synchronization extension and the headless fallback worker.
- **Production DevOps & Monitoring:** Containerized the service with Docker Compose, configured Nginx reverse proxying with SSL, and wired instant Telegram alerts for operational anomalies.

---

*Public architecture dossier. Legacy system credentials and proprietary endpoints remain strictly confidential.*
