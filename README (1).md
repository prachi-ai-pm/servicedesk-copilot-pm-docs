# ServiceDesk Copilot — PM Artifacts

Formal project management documentation for **ServiceDesk Copilot**, an AI/ML PM case study built by Prachi Sharma. This is a self-directed simulation modeled on realistic enterprise IT service management environments — not a claimed client engagement.

> Source case study: *ServiceDesk Copilot — AI/ML PM Case Study* (Prachi Sharma)

## Contents

| Document | Description |
|---|---|
| [01 — Project Charter](01_Project_Charter.md) | Formal authorization, sponsor, objectives, high-level scope, budget, and approval conditions |
| [02 — Business Case](02_Business_Case.md) | Problem statement, options considered, recommended solution, costs, benefits, ROI, and actual 90-day outcomes |
| [03 — Scope Statement](03_Scope_Statement.md) | Detailed in-scope/out-of-scope boundaries, deliverables, acceptance criteria, and change control approach |
| [04 — Work Breakdown Structure (WBS)](04_WBS.md) | Full decomposition across all 7 project stages and 8 build sprints, with WBS dictionary and milestones |
| [05 — Stakeholder Register](05_Stakeholder_Register.md) | Power/interest mapping, detailed stakeholder profiles, and engagement cadence |
| [06 — Communication Plan](06_Communication_Plan.md) | Internal governance communications, workforce/rollout messaging, and key messaging principles |
| [07 — RAID Log](07_RAID_Log.md) | Risks, Assumptions, Issues, and Dependencies tracked weekly across the project lifecycle |
| [08 — Risk Register](08_Risk_Register.md) | Scored, prioritized risk view (likelihood × impact) with heat map and top-5 ranking |
| [09 — Sprint Plan](09_Sprint_Plan.md) | Sprint-by-sprint goals, stories, team capacity, and backlog re-prioritization events |
| [10 — Product Backlog](10_Product_Backlog.md) | Epics and MoSCoW-prioritized stories, including deferred Phase 2 scope |
| [11 — User Stories](11_User_Stories.md) | Full Given/When/Then user stories with personas and story-point estimates, organized by epic |
| [12 — Budget](12_Budget.md) | Detailed cost breakdown, run-cost forecast vs. actuals, variance log, and ROI summary |
| [13 — Project Closure Report](13_Project_Closure_Report.md) | Objectives-vs-outcomes reconciliation, financial closure, deliverable acceptance, and final sign-off |
| [14 — Lessons Learned](14_Lessons_Learned.md) | What went well, what didn't, and recommendations carried into the Phase 2 roadmap |

## Architecture Diagram

![ServiceDesk Copilot architecture](assets/architecture_diagram.svg)

Channels (Teams, self-service portal) → guardrail layer (PII redaction, prompt-injection defense, access scoping) → retrieval layer (Azure AI Search hybrid index over the curated knowledge base) → Azure OpenAI generation → confident answer delivered in-channel, or human agent handoff with full context if confidence falls below threshold.

## Project Snapshot

| | |
|---|---|
| **Sponsor** | VP, IT Operations |
| **Project Manager** | Prachi Sharma |
| **Duration** | 16 weeks discovery-to-launch, plus ongoing governance |
| **Methodology** | Hybrid Agile (2-week sprints inside a Waterfall stage-gate structure) |
| **Core stack** | Azure OpenAI (GPT-4o-class) + Azure AI Search, ServiceNow KB + SharePoint as source content, delivered via Microsoft Teams + self-service portal |
| **Outcome (90 days post-launch)** | 28% reduction in human-handled L1 ticket volume against a 25% target; ~$300K projected annualized savings run-rate |

## How These Documents Relate to the Case Study

The original case study narrates seven delivery stages, each producing a working artifact. This folder formalizes those artifacts into standard PM templates so they can be reviewed independently of the narrative:

| Case Study Stage | Originating Artifact | Formalized Here In |
|---|---|---|
| Stage 1 — Discovery & Business Case | Project Charter & Business Case | `01_Project_Charter.md`, `02_Business_Case.md`, `12_Budget.md` |
| Stage 2 — Requirements & Data Readiness | PRD & Data Readiness Assessment | `03_Scope_Statement.md` (acceptance criteria), `10_Product_Backlog.md` (E1–E2), `11_User_Stories.md` (E1–E2) |
| Stage 3 — Solution Design & Architecture | Architecture Decision Record | Referenced in `03_Scope_Statement.md` and `04_WBS.md`; visualized in `assets/architecture_diagram.svg` |
| Stage 4 — Build & Delivery Coordination | Sprint Summary & RAID Log | `04_WBS.md` (Section 4.0), `07_RAID_Log.md`, `08_Risk_Register.md`, `09_Sprint_Plan.md`, `10_Product_Backlog.md`, `11_User_Stories.md` |
| Stage 5 — Evaluation, Testing & Responsible AI Review | Evaluation Report & RAI Checklist | `09_Sprint_Plan.md` (Sprint 7), `10_Product_Backlog.md` (E6), `11_User_Stories.md` (E6) |
| Stage 6 — Deployment & Change Management | Go-Live Runbook & Communications Plan | `06_Communication_Plan.md`, `09_Sprint_Plan.md` (Sprint 8), `11_User_Stories.md` (E7) |
| Stage 7 — Post-Launch Governance | Governance & Monitoring Plan | `06_Communication_Plan.md` (Section 6), `07_RAID_Log.md`, `08_Risk_Register.md`, `12_Budget.md` (Sections 5, 7–9) |
| Closure (90 days post-launch) | Outcomes Summary | `13_Project_Closure_Report.md`, `14_Lessons_Learned.md` |
| Stages 1–7 (all) | — | `05_Stakeholder_Register.md` |
