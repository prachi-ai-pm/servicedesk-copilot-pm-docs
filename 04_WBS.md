# Work Breakdown Structure (WBS)

**Project Name:** ServiceDesk Copilot — AI-Assisted Tier-1 IT Support
**Document Owner:** Prachi Sharma, AI/ML Project Manager
**Status:** Approved
**Version:** 1.0
**Date:** [Insert Approval Date]

---

## 1. WBS Overview

The project is decomposed into **7 stages** (1.0–7.0), aligned to the stage-gate structure used to govern security, compliance, and Responsible AI sign-off. Stages 1–3 are largely sequential (gating decisions); Stage 4 runs as 8 two-week Agile sprints; Stages 5–7 are sequential gates followed by ongoing operations.

**Total duration:** 16 weeks discovery-to-launch, plus ongoing post-launch governance.

## 2. WBS Hierarchy

```
0.0 ServiceDesk Copilot — AI-Assisted Tier-1 IT Support
├── 1.0 Discovery & Business Case
│   ├── 1.1 Structured discovery interviews (IT Ops Director, Service Desk Manager, InfoSec, Finance)
│   ├── 1.2 Ticket data analysis (12 months ServiceNow data — volume, cost, resolution time by category)
│   ├── 1.3 Scope-setting workshop (bound the MVP)
│   ├── 1.4 Draft Project Charter & Business Case
│   └── 1.5 Sponsor approval gate
│
├── 2.0 Requirements & Data Readiness Assessment
│   ├── 2.1 Requirements workshops with Data Science & Engineering leads
│   ├── 2.2 Functional & non-functional requirements definition (PRD)
│   ├── 2.3 Data readiness audit (ServiceNow KB, SharePoint Wiki, Confluence)
│   ├── 2.4 Labeled test-set construction (150 SME-validated Q&A pairs)
│   ├── 2.5 Success-metric alignment workshop (single weighted formula)
│   └── 2.6 PRD & Data Readiness Assessment sign-off
│
├── 3.0 Solution Design & Architecture
│   ├── 3.1 Build-vs-host-vs-buy evaluation (3-option comparison)
│   ├── 3.2 Architecture decision & vendor selection (Azure OpenAI + Azure AI Search)
│   ├── 3.3 Conversation design sessions (tone, persona, escalation UX)
│   ├── 3.4 PII redaction & prompt-injection mitigation design
│   ├── 3.5 Confidence-threshold escalation design
│   └── 3.6 Architecture Decision Record (ADR) finalized & logged
│
├── 4.0 Build & Delivery Coordination (8 two-week sprints)
│   ├── 4.1 Sprint 1–2: Foundational pipeline (KB ingestion, chunking, vector index build)
│   ├── 4.2 Sprint 3–4: Retrieval quality (hybrid keyword + vector search)
│   ├── 4.3 Sprint 5–6: Guardrails & UX (confidence escalation, PII redaction, conversation design)
│   ├── 4.4 Sprint 7: Pilot readiness (UAT fixes, agent handoff testing, go-live runbook draft)
│   ├── 4.5 Sprint 8: Pilot launch build readiness (Phase 1 — Finance dept., 450 users)
│   ├── 4.6 Sprint planning, daily standups, backlog grooming (ongoing across all sprints)
│   ├── 4.7 RAID log maintenance & weekly sponsor review (ongoing across all sprints)
│   └── 4.8 Change-request management (e.g., mid-build multilingual request)
│
├── 5.0 Evaluation, Testing & Responsible AI Review
│   ├── 5.1 Test-set evaluation run (150-question set — accuracy, relevance, hallucination rate)
│   ├── 5.2 Root-cause analysis & remediation (chunking fix for hallucination rate)
│   ├── 5.3 UAT coordination (8 service desk agents, 25 end-user volunteers, 3 departments)
│   ├── 5.4 Conversation tone revision pass (post-UAT feedback)
│   ├── 5.5 Responsible AI review (bias, fairness, documented model limitations)
│   ├── 5.6 Accessibility check (screen-reader compatibility, Teams interface)
│   └── 5.7 Evaluation Report, RAI Checklist & UAT Sign-Off
│
├── 6.0 Deployment & Change Management
│   ├── 6.1 Phased rollout plan design (pilot → expanded pilot → full company)
│   ├── 6.2 Go-live runbook (rollback triggers, named decision owner)
│   ├── 6.3 Communications plan & materials (email, manager toolkit, Teams walkthrough, survey)
│   ├── 6.4 Phase 1 — Pilot rollout (Finance dept., ~450 employees, 2 weeks)
│   ├── 6.5 Pilot adoption monitoring & mid-pilot correction (guided walkthrough)
│   ├── 6.6 Guardrail patch (block unsafe workaround suggestion — near-miss fix)
│   ├── 6.7 Phase 2 — Expanded pilot rollout (IT & Engineering, ~1,800 employees, 2 weeks)
│   └── 6.8 Phase 3 — Full rollout (remaining ~9,750 employees, phased over 2 weeks)
│
└── 7.0 Post-Launch Governance & Continuous Improvement
    ├── 7.1 KPI review cadence stood up (named owners per metric)
    ├── 7.2 Knowledge base freshness SLA (tied to IT change management; 5-business-day update trigger)
    ├── 7.3 Cost-per-query monitoring & optimization (context-window tuning)
    ├── 7.4 Answer-drift monitoring & re-index triggers
    ├── 7.5 Lessons-learned review
    └── 7.6 Phase 2 roadmap (multilingual, HR/Finance expansion, voice channel, proactive suggestions)
```

## 3. WBS Dictionary (Summary)

| WBS ID | Work Package | Primary Owner | Key Output |
|---|---|---|---|
| 1.4 | Draft Project Charter & Business Case | PM | Approved charter with sponsor sign-off |
| 2.3 | Data readiness audit | PM / Data Science Lead | Audit findings — 18%/35% outdated content identified |
| 2.4 | Labeled test-set construction | PM / Service Desk SMEs | 150-question ground-truth test set |
| 3.2 | Architecture decision & vendor selection | PM / Solution Architect / Security | ADR — Option B (Azure OpenAI + Azure AI Search) selected |
| 4.2 | Hybrid retrieval sprint (added) | ML Engineer | Hybrid keyword + vector search live |
| 5.1 | Test-set evaluation run | Data Science Lead | Hallucination rate reduced from 8% to 2.1% |
| 5.5 | Responsible AI review | PM / Compliance | RAI Checklist, sign-off held firm against date pressure |
| 6.4 | Phase 1 pilot rollout | PM / Service Desk Manager | Pilot live, ~450 users, adoption gap diagnosed and corrected |
| 7.2 | KB freshness SLA | Service Desk Manager | Standing 5-day update SLA tied to change management |

## 4. Milestones

| Milestone | WBS Reference | Gate Type |
|---|---|---|
| Charter & Business Case approved | 1.5 | Sponsor approval gate |
| PRD & Data Readiness Assessment signed off | 2.6 | Stakeholder alignment gate |
| Architecture & Security approved | 3.6 | Security/Compliance gate |
| Pilot-readiness build complete | 4.5 | Engineering readiness gate |
| UAT & Responsible AI sign-off | 5.7 | Compliance / RAI gate (non-negotiable) |
| Full rollout complete | 6.8 | Sponsor sign-off on Phase 2 results |
| 90-day outcomes review | — | Post-launch governance checkpoint |

## 5. Notes on Decomposition Choices

- **Stage 4 is sprint-based, not task-based**, reflecting the project's actual Hybrid Agile execution model — the backlog within each sprint was re-sequenced in response to technical findings (e.g., the hybrid-search addition), so sprint-level WBS items are intentionally the lowest level of formal decomposition; finer-grained stories/tasks live in the sprint backlog, not this WBS.
- **Stages 1–3 and 5–7 are gate-based**, reflecting their Waterfall-style governance structure.
- Work packages that produced a recurring or standing artifact (e.g., 7.1 KPI cadence, 7.2 KB freshness SLA) are intentionally framed as the work to *establish* the mechanism, not the ongoing operation of it — ongoing operation is tracked in the Governance & Monitoring Plan, not repeated here.

---
*Prepared by Prachi Sharma — AI Project Manager · Technical PM · Gen AI Delivery Lead*
