# Sprint Plan

**Project Name:** ServiceDesk Copilot — AI-Assisted Tier-1 IT Support
**Document Owner:** Prachi Sharma, AI/ML Project Manager
**Status:** Complete (build phase concluded — see Outcomes Summary)
**Version:** 1.0
**Date:** [Insert Date]

---

## 1. Methodology

Build ran across **8 two-week sprints** (16 weeks total) using a Hybrid Agile approach — Agile sprint execution nested inside a Waterfall-style stage-gate structure for security, compliance, and Responsible AI sign-off. The PM ran sprint planning, daily standups, and backlog grooming; translated PRD requirements into epics and stories; and re-sequenced the backlog when technical findings changed what should be built next.

## 2. Team Composition & Capacity

| Role | Count | Sprint Involvement |
|---|---|---|
| Project Manager | 1 | All sprints — planning, standups, RAID log, stakeholder coordination |
| ML / Data Engineers | 2 | All sprints — pipeline, retrieval, model integration |
| Backend / Integration Engineer | 1 | All sprints — Teams integration, API abstraction layer, infrastructure |
| Conversation / UX Designer | 1 | Sprints 3–7 — conversation design, tone, escalation UX |
| QA Analyst | 1 | Sprints 5–8 — UAT coordination, adversarial testing, sign-off support |
| Security / Compliance / Finance (part-time) | — | Gate reviews at sprint boundaries, not embedded daily |

## 3. Sprint-by-Sprint Plan

### Sprint 1–2: Foundational Pipeline
**Sprint Goal:** Establish the data ingestion and retrieval foundation the rest of the build depends on.

| Story | Description | Owner |
|---|---|---|
| Ingest ServiceNow KB content | Pull and normalize ~420 reviewed articles | ML Engineer |
| Ingest SharePoint IT Wiki content | Pull and normalize deduplicated ~260 articles | ML Engineer |
| Build chunking pipeline | Chunk content for embedding, correcting the inconsistent chunking flagged in the data readiness audit | ML Engineer |
| Build vector index | Stand up Azure AI Search vector index over chunked content | ML Engineer |
| Establish API abstraction layer | Insulate the integration from direct vendor dependency, mitigating lock-in risk | Backend Engineer |

**Status:** Complete
**Deliverables:** KB ingestion pipeline, chunking pipeline, vector index build

---

### Sprint 3–4: Retrieval Quality
**Sprint Goal:** Validate retrieval accuracy and close the gap found in testing — **scope expanded mid-sprint based on a technical finding.**

| Story | Description | Owner |
|---|---|---|
| Run informal-query accuracy testing | Test retrieval against realistic short queries (e.g., "vpn not working") | ML Engineer |
| **[Added]** Implement hybrid (keyword + vector) search | Pure vector search underperformed on short, informal queries; added after mid-sprint finding | ML Engineer |
| Re-test retrieval accuracy against the 150-question test set | Confirm improvement after hybrid search implementation | ML Engineer / QA |
| Begin conversation design discovery | Tone, persona definition kickoff | UX Designer |

**Status:** Complete — **1 sprint added to scope** (originally planned as a single sprint; extended to two after the retrieval-quality finding, communicated to the sponsor as a trade-off rather than a quiet slip)
**Deliverables:** Hybrid keyword + vector search live

---

### Sprint 5–6: Guardrails & UX
**Sprint Goal:** Implement the trust and safety layer — confidence-based escalation, PII redaction, and conversation design.

| Story | Description | Owner |
|---|---|---|
| Build confidence-threshold scoring | Score retrieval confidence per query | ML Engineer |
| Implement escalation handoff | Route below-threshold queries to a human agent with full conversation context — non-negotiable requirement from the Stage 3 dry-run finding | Backend Engineer |
| Build PII redaction layer | Apply redaction to retrieved content and logged queries before reaching the model | ML Engineer / Security |
| Finalize conversation design | Define tone, persona, and escalation experience | UX Designer |
| Implement access scoping | Ensure users can only retrieve general knowledge content, never another employee's data | Backend Engineer / Security |

**Status:** Complete
**Deliverables:** Confidence-based escalation, PII redaction, conversation design

---

### Sprint 7: Pilot Readiness
**Sprint Goal:** Prepare for UAT and pilot launch.

| Story | Description | Owner |
|---|---|---|
| Fix issues surfaced in pre-UAT dry run | Address gaps such as the missing escalation path found in dry-run testing | Full team |
| Run UAT with service desk agents and end-user volunteers | 2-week UAT, 8 agents + 25 end-user volunteers across 3 departments | QA / PM |
| Test adversarial prompt set | Validate prompt-injection resistance before sign-off | Security / QA |
| Draft go-live runbook | Define rollback triggers and a named decision owner | PM |
| Conduct Responsible AI review | Bias, fairness, and documented limitations review | PM / Compliance |
| Tone revision pass | Address UAT feedback describing the bot as "robotic" and overly hedged | UX Designer |
| Chunking fix for hallucination rate | Root-cause and resolve the 8% hallucination rate finding (password-policy article chunking) | Data Science Lead |

**Status:** Complete
**Deliverables:** UAT fixes, agent handoff testing verified, go-live runbook drafted, RAI sign-off

---

### Sprint 8: Pilot Launch
**Sprint Goal:** Execute Phase 1 rollout to the Finance department.

| Story | Description | Owner |
|---|---|---|
| Execute Phase 1 pilot rollout | Launch to Finance department, ~450 employees | PM / Service Desk Manager |
| Monitor daily adoption data | Track usage in week one; act on early signals rather than waiting for a scheduled review | PM |
| Diagnose and correct adoption gap | Quick survey identified an awareness gap; added a guided Teams walkthrough mid-pilot | PM / Internal Comms |
| Add guardrail for unsafe workaround suggestions | Near-miss caught during pilot; blocked before expanding beyond the pilot department | Security / ML Engineer |

**Status:** Complete — see Outcomes Summary for results
**Deliverables:** Phase 1 rollout live; near-miss guardrail added; adoption gap corrected

## 4. Backlog Re-Prioritization Events

| Event | Sprint | PM Action |
|---|---|---|
| Vector-only search underperformed on short queries | 3–4 | Reprioritized backlog to add hybrid search; communicated one-sprint trade-off to sponsor rather than quietly slipping the date |
| Multilingual support requested mid-build | 5–6 | Logged as a formal change request, cost/timeline impact assessed, deferred to Phase 2 rather than informally accepted or rejected |
| Key ML engineer unavailable for 2 weeks | 5–6 | Activated the pre-planned cross-training contingency; absorbed a short ramp-up cost instead of a hard stop |
| Hallucination rate exceeded threshold (8% vs. 3%) | 7 | Inserted root-cause and remediation work ahead of sign-off rather than relaxing the threshold to protect the date |

## 5. Definition of Done (Sprint Level)

A story is considered done when:
- Functionality is implemented and passes engineering-level testing
- Any security- or PII-relevant change has been reviewed by Security
- Acceptance criteria from the PRD are demonstrably met
- The change is reflected in the RAID log if it affects a tracked risk, assumption, issue, or dependency

---
*Prepared by Prachi Sharma — AI Project Manager · Technical PM · Gen AI Delivery Lead*
