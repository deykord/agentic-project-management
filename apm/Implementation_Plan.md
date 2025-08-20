# Implementation Plan (Simple)

Project: Digital Services and AI Business Platform
Owner: Setup Agent
Date: 2025-08-20

## Summary
Build a self-hosted web platform and operating stack for a digital services + AI solutions provider focused on Iranian businesses. Deliver a credible online presence, compliant payments, and production-ready service delivery processes.

## Decisions & Assumptions (Accepted "recommended options")
- Asset_format: md
- Memory_strategy: dynamic-md (Memory Root will be created in a later phase)
- Frontend: React (RTL-ready for fa-IR) + TailwindCSS (or equivalent) for rapid styling
- Backend: Node.js + Express
- Database: PostgreSQL
- Primary Payment Gateway: Zarinpal (Iran-compliant); evaluate IDPay as fallback
- AI Strategy: Local model fallback (Ollama + Llama/Mistral) with optional OpenAI where reachable
- Hosting: Linux VM(s) with stable connectivity to Iran; reverse proxy via Nginx; SSL via Let’s Encrypt
- Language: Persian-first (fa-IR, RTL) with optional English (en) secondary

Open Decisions (to be resolved in Phase 1–2 tasks):
- Hosting provider/region (shortlist + decision)
- Domain name selection and registration
- Internal tools stack (PM, docs, chat)
- International payment workaround (if required) and invoicing flow

---

## Phase 1: Foundation (Weeks 1–4)
Objectives: Establish business/legal baseline, offerings, compliance posture, and payment approach.

Deliverables:
- Business Plan v1 (services, pricing, ICPs, GTM)
- Compliance & Regulatory Checklist (Iranian e‑commerce/data privacy)
- Payment Gateway Selection Report (Zarinpal primary; fallback options)
- Preliminary Success Metrics (KPIs) and Launch Criteria

Key Tasks:
1. Legal & Registration
   - Verify business registration requirements; create action list and timeline
   - Draft required company policies (privacy, ToS, refund)
2. Offerings & Pricing
   - Define services catalogue outline (tiers, SLAs, pricing bands)
   - Draft proposal/contract templates
3. Compliance Discovery
   - Identify applicable Iranian regulations and data residency needs
   - Define data handling/PII policy and retention schedule
4. Payments Strategy
   - Evaluate Zarinpal onboarding; create checklist (merchant account, docs)
   - Decide on international payment handling (invoice, partner, etc.)
5. KPIs & Success Metrics
   - Define launch KPIs (e.g., MVP live, first IRR payment, pilot clients)

---

## Phase 2: Platform Development (Weeks 5–12)
Objectives: Deliver a secure, self-hosted MVP website with payments and basic CMS for services.

Deliverables:
- Architecture Diagram & ADRs
- Production Linux VM(s) with hardened baseline (firewall, updates)
- PostgreSQL instance and backups
- Backend API scaffold (Node/Express) and auth layer
- Frontend scaffold (React) with RTL support; initial marketing pages
- Payment integration (Zarinpal sandbox → production)
- CI/CD (GitHub Actions) and Infrastructure-as-Code (basic)
- SSL/TLS (Let’s Encrypt) via Nginx reverse proxy

Key Tasks:
1. Infrastructure & Security
   - Select provider; provision VM; set up SSH, ufw, auto-updates
   - Install Docker + Compose; set up Nginx reverse proxy + Fail2ban
   - Configure Let’s Encrypt certificates (auto-renew)
2. Data Layer
   - Deploy PostgreSQL; implement backups (daily) and restores (test)
   - Define initial schema (users, services, orders, payments, logs)
3. Backend
   - Scaffold Express app; add auth/session/JWT (to decide)
   - Services/catalog endpoints; payment webhook handlers
   - Configuration abstraction for payment gateways
4. Frontend
   - Scaffold React app; enable i18n (fa-IR default, en optional) and RTL
   - Pages: Home, Services, Pricing, About, Contact, Legal (Privacy/ToS)
   - Admin/CMS-lite for editing services content (MVP)
5. Payments
   - Integrate Zarinpal sandbox; handle success/cancel/webhook
   - E2E payment test plan and logs; switch to production creds
6. DevEx & CI/CD
   - GitHub Actions: build/test/lint, Docker image build/push, deploy job
   - .env handling, secrets storage (host-level or vault)

---

## Phase 3: Team Building (Weeks 8–14)
Objectives: Define roles, recruit core team, and stand up internal collaboration tools.

Deliverables:
- Org & Roles Matrix; Hiring Plan
- Internal Tools: PM, Docs, Chat (self-hosted or SaaS as decided)
- Onboarding Guide for new hires

Key Tasks:
1. Roles & Hiring
   - Prioritize: Full-stack engineer, DevOps, AI engineer, Designer, PM
   - Create job descriptions and interview rubrics
2. Tools Setup
   - Evaluate and choose: Plane/Redmine (PM), Mattermost (chat), Wiki.js/HedgeDoc (docs)
   - Provision and secure instances; backup configs
3. Processes
   - Define working agreements, sprint cadence, code review standards

---

## Phase 4: Service Development (Weeks 10–18)
Objectives: Finalize service catalogue, delivery playbooks, and AI capability stack.

Deliverables:
- Service Catalogue v1 with delivery steps and SLAs
- Delivery Playbooks (checklists, templates)
- AI Stack Plan: connectivity checks, local model setup, abstraction layer
- Client Onboarding Process & artifacts

Key Tasks:
1. Catalogue & Playbooks
   - Detail 3–5 priority services with inputs/outputs/SLAs
   - Create delivery runbooks and quality gates
2. AI Enablement
   - Test OpenAI access from infra; capture reliability metrics
   - Stand up Ollama with Llama/Mistral; evaluate accuracy/cost/latency
   - Implement adapter pattern to switch providers seamlessly
3. Client Onboarding
   - Define lead → contract → kickoff → delivery → support flow
   - Create intake forms, NDAs, SOW templates

---

## Phase 5: Launch (Weeks 19–20)
Objectives: Pilot with early clients and go live.

Deliverables:
- Pilot Feedback Report and fixes
- Go-live Runbook & Incident Playbook
- Marketing Site v1 and assets (brochure, pitch deck)

Key Tasks:
1. Pilot & QA
   - Run pilot transactions; validate payment reconciliation
   - Fix critical issues; performance pass
2. Go-live
   - Final legal pages; monitoring & alerts enabled
   - Launch announcement and outreach

---

## Phase 6: Growth (Week 21+)
Objectives: Scale operations, improve reliability, and expand offerings.

Deliverables:
- Analytics dashboard, SEO baseline
- SLOs and capacity plan; backlog for v2 features
- Partnership plan and pipeline

Key Tasks:
1. Reliability & Scale
   - Add caching/queueing; refine backup/restore RPO/RTO
   - Consider WAF and CDN if beneficial
2. Marketing & Sales
   - Lead gen funnel; monthly reporting; case studies
3. Partnerships
   - Identify partners; co-marketing opportunities

---

## Risks & Mitigations
- Sanctions/API access: prefer local/regional services; local AI fallback
- Internet instability: retries, offline-tolerant ops, monitoring, staged rollouts
- Compliance uncertainty: early legal consult; bake compliance checks into CI/CD
- Talent availability: remote/contract options; training plans

## Success Metrics (initial draft)
- MVP site live; first successful IRR payment
- 3 pilot clients onboarded within 1 month of launch
- 10 qualified leads/month by Month 3
- 99.5% uptime; backup restore tested quarterly

---

Notes:
- Memory Root and enhanced artifacts will be produced in later phases per APM.
- This is a simple plan; it will be refined or enhanced after review.
