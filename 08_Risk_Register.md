# Risk Register

**Project Name:** ServiceDesk Copilot — AI-Assisted Tier-1 IT Support
**Document Owner:** Prachi Sharma, AI/ML Project Manager
**Status:** Living document
**Version:** 1.0
**Date:** [Insert Last Updated Date]

---

## 1. Purpose

This register provides a scored, prioritized view of project risk, complementing the RAID Log. Each risk is rated on likelihood and impact (1–5 scale) to produce a risk score used to prioritize mitigation effort and sponsor attention.

## 2. Scoring Methodology

| Likelihood | Score | Impact | Score |
|---|---|---|---|
| Very Low | 1 | Negligible | 1 |
| Low | 2 | Minor | 2 |
| Medium | 3 | Moderate | 3 |
| High | 4 | Major | 4 |
| Very High | 5 | Severe | 5 |

**Risk Score = Likelihood × Impact** (1–25). Scores ≥ 15 require sponsor visibility and an active mitigation owner; scores ≥ 20 are launch-blocking until resolved.

## 3. Risk Register

| ID | Risk Description | Category | Likelihood | Impact | Score | Risk Response | Owner | Status |
|---|---|---|---|---|---|---|---|---|
| RR1 | Hallucination rate exceeds the 3% threshold, eroding user trust and the case for AI adoption | Quality / Reputational | 3 | 5 | **15** | **Mitigate** — root-cause analysis on any threshold breach; treat as launch-blocking, not negotiable against the calendar | Data Science Lead | Closed — realized at 8%, fixed to 2.1% |
| RR2 | Knowledge base fragmentation/outdated content degrades retrieval quality | Data / Technical | 4 | 4 | **16** | **Mitigate** — formal data readiness audit before pipeline work; SME review and deduplication | PM / Data Science Lead | Closed — audit completed, content remediated |
| RR3 | Security rejects fine-tuning on raw ticket data due to PII exposure | Compliance / Architecture | 4 | 4 | **16** | **Avoid** — pivot architecture to pure RAG over a redacted, curated KB rather than fine-tuning | PM / Security | Closed — RAG architecture adopted |
| RR4 | Confidently wrong answers presented without escalation erode trust or cause harm | Quality / Trust | 3 | 5 | **15** | **Mitigate** — hard requirement that any below-threshold answer triggers explicit human handoff with context, never presented as final | PM / UX | Closed — requirement implemented and verified pre-launch |
| RR5 | Prompt injection allows unauthorized data access or behavior manipulation | Security | 2 | 5 | **10** | **Mitigate** — PII redaction layer; adversarial prompt-set testing before UAT | Security / ML Engineer | Closed — no successful injections in final test pass |
| RR6 | One employee retrieves another employee's ticket or account data through the bot | Security / Privacy | 2 | 5 | **10** | **Mitigate** — strict access scoping to general knowledge content only | Security | Closed — verified in Responsible AI review |
| RR7 | Vendor lock-in on a single model/platform provider | Commercial | 3 | 3 | **9** | **Accept (mitigated)** — build behind an internal API abstraction layer so the provider can be swapped with contained effort | Procurement / Solution Architect | Closed — accepted with documented mitigation |
| RR8 | LLM provider outage with no fallback | Technical / Availability | 2 | 4 | **8** | **Mitigate** — graceful degradation to a static FAQ accepted as sufficient for v1; multi-vendor strategy deferred | Solution Architect | Accepted for v1 — revisit if outage frequency increases |
| RR9 | Pure vector search underperforms on short, informal queries | Technical | 3 | 4 | **12** | **Mitigate** — add hybrid keyword + vector search | ML Engineer | Closed — realized and resolved, one sprint added |
| RR10 | Key ML engineer becomes unavailable mid-build | Resourcing | 3 | 4 | **12** | **Mitigate** — cross-train a second engineer in advance as a standing contingency | PM | Closed — contingency activated successfully when realized |
| RR11 | Scope creep from an open-ended "AI helpdesk" ambition stalls the fundable MVP | Scope | 4 | 3 | **12** | **Mitigate** — effort-vs-impact exercise with ticket data; phase HR/Finance into a later release | PM / Sponsor | Closed — scope narrowed and approved |
| RR12 | Mid-build scope requests (e.g., multilingual support) bypass formal change control | Scope / Governance | 3 | 3 | **9** | **Mitigate** — route all such requests through a formal change-request process with cost/timeline impact assessment | PM | Closed — process used successfully; multilingual deferred to Phase 2 |
| RR13 | Sponsor pressure to compress or skip the Responsible AI / bias review to hit a launch date | Governance / Ethical | 3 | 5 | **15** | **Mitigate** — hold the RAI gate as non-negotiable; quantify reputational/compliance exposure for the sponsor | PM / Compliance | Closed — short scoped delay accepted instead of skipping the review |
| RR14 | Low pilot adoption is misdiagnosed as a product failure, triggering an unnecessary rollback | Adoption / Change Management | 3 | 4 | **12** | **Mitigate** — quick diagnostic survey before concluding root cause; correct via change management (guided walkthrough) before considering rollback | PM | Closed — correctly diagnosed as an awareness gap |
| RR15 | Workforce perceives the bot as a threat to service desk jobs, creating resistance | Change Management / Workforce | 3 | 4 | **12** | **Mitigate** — direct communications plan framing the tool as augmentation; address union/staff representative concerns head-on | PM / Internal Comms | Closed — addressed in communications plan; no escalation reported |
| RR16 | A bot-suggested workaround bypasses required change-control steps (near-miss) | Operational / Safety | 2 | 4 | **8** | **Mitigate** — add explicit guardrail rule blocking that suggestion category | PM / Security | Closed — guardrail added pre-expansion |
| RR17 | Cost per query drifts materially above forecast post-launch | Financial | 3 | 3 | **9** | **Mitigate** — monthly cost-per-query monitoring with a 10%+ deviation trigger; prompt/context optimization | PM / Finance | Closed — corrected within first month |
| RR18 | Answer quality drifts as source content ages without a formal freshness owner | Operational / Data | 3 | 3 | **9** | **Mitigate** — tie KB updates to the IT change management process with a defined SLA | Service Desk Manager | Closed — 5-business-day SLA established |
| RR19 | Three stakeholders hold different private definitions of "success," risking disputed evaluation at launch | Governance / Alignment | 3 | 3 | **9** | **Mitigate** — facilitated weighting exercise to produce one signed-off success formula before build | PM | Closed — resolved in Stage 2 PRD |
| RR20 | HR/Finance expansion or other Phase 2 features are pursued without their own data-readiness validation | Strategic / Future Scope | 2 | 3 | **6** | **Avoid (for now)** — explicitly gate Phase 2 domain expansion on those teams' own KB readiness | PM | Open — tracked in Phase 2 roadmap |

## 4. Risk Heat Map (Summary by Score Band)

| Score Band | Risk Level | Count | Risk IDs |
|---|---|---|---|
| 20–25 | Critical (launch-blocking) | 0 | — |
| 15–19 | High (sponsor visibility required) | 4 | RR1, RR2, RR3, RR4, RR13 |
| 10–14 | Medium | 9 | RR5, RR6, RR9, RR10, RR11, RR14, RR15 |
| 1–9 | Low / Accepted | 7 | RR7, RR8, RR12, RR16, RR17, RR18, RR19, RR20 |

*(Note: RR1, RR2, RR3, RR4, and RR13 scored 15+ at identification and were treated as requiring direct sponsor visibility; all were closed prior to or during launch except where noted otherwise above.)*

## 5. Top 5 Risks by Initial Score

1. **RR2 / RR3 (tied, score 16)** — Knowledge base fragmentation; PII-driven fine-tuning rejection
2. **RR1 / RR4 / RR13 (tied, score 15)** — Hallucination threshold breach; unescalated low-confidence answers; RAI review compression pressure
3. **RR9 / RR10 / RR11 / RR14 / RR15 (tied, score 12)** — Vector search underperformance; key-person dependency; scope ambition; adoption misdiagnosis; workforce resistance

## 6. Review Cadence

This register is reviewed weekly alongside the RAID Log during build (Stages 1–6) and monthly during post-launch governance (Stage 7), with score re-assessment whenever a risk is realized or a mitigation is completed.

---
*Prepared by Prachi Sharma — AI Project Manager · Technical PM · Gen AI Delivery Lead*
