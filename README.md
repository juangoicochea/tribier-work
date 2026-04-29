# Professional Work — Tribier Business Intelligence

> Private repositories — proprietary work.  
> This document describes the systems I have built and the technical
> decisions behind them.

## About

Tribier Business Intelligence is a B2B SaaS company focused on helping
enterprises improve their quality management processes.
I have been part of the development team since May 2023 as a Full Stack
Developer, contributing across the full cycle on multiple production
applications: DB design → API → UI → deploy.

The team has built and maintained three interconnected systems, working
across backend, frontend, infrastructure, and third-party integrations.

---

## Systems built

### SEI — Strategic Integrated System
The company's core platform. A multi-module web application that centralizes
enterprise quality workflows.

**Key modules:**
- Meeting minutes with participant tracking and digital sign-off
- Task management with assignment, deadlines, and status tracking
- Role-based access control (admin / processLeader / collaborator) via Auth0

**Stack:** NestJS · Next.js · TypeScript · PostgreSQL · TypeORM · MUI · GCP

![SEI Dashboard](assets/sei-dashboard.png)
![SEI Task Management](assets/sei-tasks.png)

---

### SIM — Integrated Measurement System
A companion platform focused on performance measurement and KPI tracking
for enterprise clients.

**Key modules:**
- Indicator definition and periodic measurement logging
- Data visualization dashboards
- Automated email notifications via scheduled cron jobs (Cloud Scheduler)

**Stack:** NestJS · Next.js · TypeScript · PostgreSQL · TypeORM · MUI · GCP

![SIM Dashboard](assets/sim-dashboard.png)
![SIM Indicators](assets/sim-indicators.png)

---

### Payment Service
A standalone microservice that handles all billing logic for both SEI and SIM,
decoupled from the main applications to allow independent scaling and
maintenance.

**Key features:**
- Recurring subscription flows with MercadoPago pre-approval
- Webhook processing for real-time payment event handling
- Subscription status sync across both platforms

**Stack:** NestJS · TypeScript · MercadoPago API · PostgreSQL · GCP Cloud Run

![Payment Service](assets/payment-service.png)

---

## Infrastructure

All systems are deployed on Google Cloud Platform:

| Service | Usage |
|---|---|
| Cloud Run | Containerized backend deployments |
| Cloud SQL | Managed PostgreSQL instances |
| Cloud Scheduler | Cron jobs for automated notifications |

---

## Technical highlights

- **Auth0 (OAuth 2.0 / OIDC):** Unified authentication across all platforms,
  eliminating custom password management
- **react-window virtualization:** Resolved critical frontend performance
  bottlenecks when rendering lists of 5,000+ rows
- **Webhook architecture:** Real-time payment event processing with
  idempotency handling
- **Ensuring production stability** Independently set up and deployed the full GCP infrastructure (Cloud Run, Cloud SQL,
Cloud Storage, Cloud Scheduler), ensuring production stability

---

## Stack overview

| Layer | Technologies |
|---|---|
| Backend | NestJS · Node.js · TypeScript · TypeORM · REST APIs |
| Frontend | Next.js · React · MUI · RTK Query |
| Database | PostgreSQL |
| Auth & Payments | Auth0 · MercadoPago · JWT · Webhooks |
| Cloud | GCP Cloud Run · Cloud SQL · Cloud Storage · Cloud Scheduler |
| Dev practices | Git · Scrum · CI/CD · Cron Jobs |
