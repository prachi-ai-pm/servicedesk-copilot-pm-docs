# Project Scope Statement

**Project Name:** ServiceDesk Copilot — AI-Assisted Tier-1 IT Support
**Document Owner:** Prachi Sharma, AI/ML Project Manager
**Status:** Approved
**Version:** 1.0
**Date:** [Insert Approval Date]

---

## 1. Project Scope Description

ServiceDesk Copilot is a Retrieval-Augmented Generation (RAG) chatbot deployed to deflect repetitive Tier-1 IT service desk tickets to a 24/7 self-service channel, while escalating gracefully to a human agent whenever the system's confidence in an answer falls below an agreed threshold. The solution is built on Azure OpenAI and Azure AI Search, retrieving from a curated, deduplicated knowledge base sourced from the ServiceNow KB and SharePoint IT Wiki, and delivered through Microsoft Teams and a self-service portal widget.

## 2. Project Deliverables

| Stage | Deliverable |
|---|---|
| 1 — Discovery & Business Case | Project Charter & Business Case |
| 2 — Requirements & Data Readiness | Product Requirements Document (PRD) & Data Readiness Assessment |
| 3 — Solution Design & Architecture | Architecture Decision Record (ADR) |
| 4 — Build & Delivery Coordination | Sprint Summaries & RAID Log |
| 5 — Evaluation, Testing & Responsible AI Review | Evaluation Report, Responsible AI Checklist & UAT Sign-Off |
| 6 — Deployment & Change Management | Go-Live Runbook & Communications Plan |
| 7 — Post-Launch Governance | Governance & Monitoring Plan |

## 3. In Scope (MVP / Phase 1)

- **Query categories:** Password reset guidance, software access requests, VPN/connectivity troubleshooting, printer/hardware FAQs, general how-to questions
- **Channels:** Microsoft Teams, self-service web portal widget
- **Retrieval sources:** ServiceNow Knowledge Base (reviewed/refreshed), SharePoint IT Wiki (deduplicated)
- **Core capabilities:**
  - Hybrid (keyword + vector) retrieval-augmented generation
  - Confidence-threshold routing with full-context handoff to a human agent
  - PII redaction layer applied to retrieved content and logged queries
  - Prompt-injection defenses
  - Strict access scoping (general knowledge content only — never another employee's ticket or account data)
- **Rollout:** Phased deployment — pilot department → expanded pilot → full company
- **Governance:** Ongoing KPI monitoring, knowledge base freshness SLA tied to IT change management

## 4. Out of Scope (Phase 1)

- HR and Finance query domains
- Voice channel
- Multilingual support
- Any ticket category requiring account-level changes without human approval
- Fine-tuning on raw ticket data (rejected by Security due to PII exposure risk; pure RAG architecture used instead)
- Confluence Engineering Notes as a content source (wrong audience for Tier-1 end-user queries)
- Proactive/predictive suggestions (e.g., flagging a likely upcoming issue) — explicitly parked pending a dedicated Responsible AI review

## 5. Acceptance Criteria

| Requirement | Acceptance Criteria |
|---|---|
| Answer eligible Tier-1 queries | ≥ 90% of in-scope test-set questions receive a relevant, non-hallucinated answer |
| Confidence-based escalation | 100% of below-threshold queries are escalated with no dead-ends |
| Response latency | ≤ 3 seconds average under expected load |
| Data handling | No PII used for model fine-tuning; query logs retained per Legal's retention policy; verified by Security and Compliance sign-off prior to launch |
| Channel availability | Both Microsoft Teams and the self-service portal functional in UAT |
| Hallucination rate | ≤ 3% on the 150-question validated test set |
| User satisfaction | CSAT ≥ 4.0/5 |

## 6. Project Constraints

- No fine-tuning on raw ticket data containing PII
- All production traffic must remain within approved data residency boundaries
- Escalation to a human must always be available — never dead-ended
- Security and Compliance sign-off required before any production data exposure

## 7. Project Assumptions

- Existing KB content is substantially reusable after a cleanup pass
- Security will approve an in-tenant model hosting option
- Service Desk leadership will support a phased pilot rollout rather than a single big-bang launch

## 8. Scope Exclusions Rationale

| Excluded Item | Rationale | Disposition |
|---|---|---|
| HR & Finance domains | Original "AI helpdesk" ambition outpaced a fundable, deliverable MVP; IT Tier-1 represented the largest, cleanest, fastest win per effort-vs-impact analysis | Phased into a later release |
| Multilingual support | Requested mid-build by a stakeholder; assessed via formal change request for cost/timeline impact | Deferred to Phase 2 |
| Voice channel | Not required for MVP value case | Deferred to Phase 2 |
| Fine-tuning on ticket data | Security rejected due to PII exposure risk | Replaced with pure RAG over a redacted, curated knowledge base |

## 9. Scope Change Control

All scope changes are managed through a formal change-request process: the requester's ask is logged, a cost and timeline impact assessment is performed, and the decision is brought to the sponsor for disposition (approve into current scope, defer to a later phase, or reject) — rather than handled as an informal yes/no. Example: a mid-build request for multilingual support was logged, assessed, and deferred to Phase 2 with the requester's agreement.

## 10. Sign-Off

| Approver | Title | Signature | Date |
|---|---|---|---|
| | VP, IT Operations (Sponsor) | | |
| | AI Project Manager | | |
| | Service Desk Manager | | |
| | Information Security Officer | | |
| | Compliance Officer | | |

---
*Prepared by Prachi Sharma — AI Project Manager · Technical PM · Gen AI Delivery Lead*
