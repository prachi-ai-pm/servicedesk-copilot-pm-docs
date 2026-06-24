# Project Charter

**Project Name:** ServiceDesk Copilot — AI-Assisted Tier-1 IT Support
**Document Owner:** Prachi Sharma, AI/ML Project Manager
**Status:** Approved
**Version:** 1.0
**Date:** [Insert Approval Date]

> **Note on this document:** This case study is a self-directed simulation built to demonstrate AI/ML project management methodology end to end. The company (Atlas Industrial Group), stakeholders, and figures are illustrative, modeled on realistic enterprise IT service management environments. It is not a claimed client engagement.

---

## 1. Purpose

This charter formally authorizes the ServiceDesk Copilot project and grants the Project Manager the authority to apply organizational resources to project activities. It converts an open-ended vendor pitch — a generic "AI helpdesk" platform promising to "automate IT support" — into a bounded, fundable, and governed initiative with a named sponsor, validated numbers, and a defined MVP scope.

## 2. Project Sponsor & Authority

| Role | Name / Title |
|---|---|
| **Executive Sponsor** | VP, IT Operations |
| **Project Manager** | Prachi Sharma — AI/ML Project Manager (sole PM, cross-functional lead) |
| **Approval Authority** | VP, IT Operations, with conditions (see Section 9) |

## 3. Business Need / Problem Statement

Atlas Industrial Group is a 12,000-employee global manufacturing and logistics company. Its IT service desk handles roughly **9,000 Tier-1 tickets per month** at an estimated fully loaded cost of **$12 per ticket** — approximately **$1.3M annually**. About **65% of that volume** falls into five repetitive, low-complexity categories that are well suited to automation but currently require round-the-clock human handling:

- Password resets
- Software access requests
- VPN and connectivity issues
- Printer and hardware queries
- General how-to questions

## 4. Project Description

ServiceDesk Copilot is a Retrieval-Augmented Generation (RAG) chatbot built to:

- Deflect a meaningful share of eligible Tier-1 ticket volume to a 24/7 self-service channel
- Escalate gracefully to a human agent whenever the system is not confident in an answer
- Operate within enterprise security, compliance, and cost constraints

The project follows a **Hybrid Agile** methodology — two-week sprints nested inside a Waterfall-style stage-gate structure for security, compliance, and Responsible AI sign-off.

## 5. Project Objectives

| # | Objective |
|---|---|
| 1 | Deflect 25% of eligible Tier-1 ticket volume to self-service within 90 days of launch |
| 2 | Maintain or improve end-user satisfaction versus the current human-handled baseline |
| 3 | Operate within an agreed hallucination-rate and cost-per-query ceiling |
| 4 | Preserve a frictionless escalation path to a human agent at all times |

## 6. Success Metrics

| Metric | Target |
|---|---|
| Ticket deflection rate | 25% within 90 days |
| Hallucination rate | ≤ 3% on the validated test set |
| User CSAT | ≥ 4.0 / 5 |
| Average response latency | ≤ 3 seconds |
| Cost per query | Within 10% of forecast |

## 7. High-Level Scope

**In Scope (MVP):** Password reset guidance, software access requests, VPN/connectivity troubleshooting, printer/hardware FAQs, and general how-to questions — delivered via Microsoft Teams and the self-service portal.

**Out of Scope (Phase 1):** HR and Finance query domains; voice channel; multilingual support; any ticket category requiring account-level changes without human approval.

*(See the Scope Statement for full detail.)*

## 8. Project Team & Resources

| Role | Allocation |
|---|---|
| Project Manager | 1, full-time (sole PM, cross-functional lead) |
| ML / Data Engineers | 2 |
| Backend / Integration Engineer | 1 |
| Conversation / UX Designer | 1 |
| QA Analyst | 1 |
| Security, Compliance, Finance | Part-time partners |

**Duration:** 16 weeks discovery-to-launch, plus ongoing governance.

## 9. Budget & Funding

| Item | Amount |
|---|---|
| One-time build cost | $145,000 |
| Projected run cost | ~$3,800/month (model inference, search indexing, hosting) |

## 10. Key Assumptions

- Existing knowledge base content is substantially reusable after a cleanup pass
- Security will approve an in-tenant model hosting option
- Service Desk leadership will support a phased pilot rollout rather than a single big-bang launch

## 11. Key Constraints

- No fine-tuning on raw ticket data containing PII
- All production traffic must stay within approved data residency boundaries
- Escalation to a human must always be available — never dead-ended

## 12. High-Level Risks

| Risk | Notes |
|---|---|
| Knowledge base fragmentation | Support content lives across three disconnected systems with overlap and outdated articles — flagged in this charter rather than surfacing later as a build-phase surprise |
| Architecture disagreement | Security favors in-tenant hosting; the original vendor pitch assumed public SaaS. Deferred to a Stage 3 architecture decision with a documented placeholder assumption so it does not block charter approval |
| Scope creep | Original ambition included HR and Finance on day one; narrowed to IT Tier-1 only for Phase 1 based on an effort-versus-impact analysis |

## 13. Approval

| Decision | Detail |
|---|---|
| **Outcome** | Approved by VP, IT Operations |
| **Conditions** | Security and Compliance sign-off required before any production data exposure (tracked as a Stage 3 gate) |

| Approver | Title | Signature | Date |
|---|---|---|---|
| | VP, IT Operations (Sponsor) | | |
| | AI Project Manager | | |
| | Information Security Officer | | |
| | Compliance Officer | | |

---
*Prepared by Prachi Sharma — AI Project Manager · Technical PM · Gen AI Delivery Lead*
