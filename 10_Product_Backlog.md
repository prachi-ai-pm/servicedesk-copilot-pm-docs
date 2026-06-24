# Product Backlog

**Project Name:** ServiceDesk Copilot — AI-Assisted Tier-1 IT Support
**Document Owner:** Prachi Sharma, AI/ML Project Manager
**Status:** Living document
**Version:** 1.0
**Date:** [Insert Last Updated Date]

---

## 1. Purpose

This backlog organizes all delivered, in-flight, and deferred work into epics and prioritized stories, translating the PRD's functional and non-functional requirements into units the engineering team could estimate and commit to.

## 2. Prioritization Method

Stories are prioritized using **MoSCoW** (Must / Should / Could / Won't — this release), informed by the PRD's acceptance criteria and the Stage 1 business case objectives. Priority reflects what's needed to meet the launch acceptance criteria, not story size.

## 3. Epics

| Epic ID | Epic | Description |
|---|---|---|
| E1 | Knowledge Ingestion & Retrieval | Ingest, clean, chunk, and index source content for retrieval |
| E2 | Hybrid Search & Accuracy | Retrieval quality, including the hybrid keyword + vector addition |
| E3 | Trust, Safety & Guardrails | Confidence-based escalation, PII redaction, access scoping, prompt-injection defense |
| E4 | Conversation Experience | Tone, persona, escalation UX |
| E5 | Channel Integration | Microsoft Teams and self-service portal delivery |
| E6 | Evaluation & Responsible AI | Test-set evaluation, bias/fairness review, accessibility |
| E7 | Rollout & Change Management | Phased launch, communications, adoption monitoring |
| E8 | Governance & Monitoring | Post-launch KPI tracking, KB freshness, cost monitoring |
| E9 (Phase 2 — deferred) | Multilingual & Channel Expansion | Multilingual support, voice channel |
| E10 (Phase 2 — deferred) | Domain Expansion | HR and Finance query domains |
| E11 (Phase 2 — deferred) | Proactive Assistance | Predictive/proactive suggestions, pending dedicated RAI review |

## 4. Product Backlog — Prioritized Stories

### Epic E1 — Knowledge Ingestion & Retrieval
| Priority | Story | Acceptance Criteria | Status |
|---|---|---|---|
| Must | As a system, I ingest ServiceNow KB content so retrieval has a primary source | ~420 reviewed/refreshed articles ingested | Done |
| Must | As a system, I ingest deduplicated SharePoint IT Wiki content | ~260 articles deduplicated against ServiceNow KB; outdated articles archived | Done |
| Must | As a system, I exclude out-of-audience content | Confluence Engineering Notes (90 articles) excluded from scope | Done |
| Must | As a system, I chunk content consistently to support accurate retrieval | Chunking strategy corrects inconsistencies flagged in the data readiness audit | Done |
| Must | As a system, I close identified content gaps | 70 new articles written to close gaps (e.g., recent VPN tool change) | Done |

### Epic E2 — Hybrid Search & Accuracy
| Priority | Story | Acceptance Criteria | Status |
|---|---|---|---|
| Must | As a user, I get relevant results for short/informal queries (e.g., "vpn not working") | Hybrid keyword + vector search live; retrieval accuracy improved versus vector-only baseline | Done |
| Must | As a system, I am evaluated against a ground-truth test set | 150-question labeled test set built with 4 Service Desk SMEs | Done |
| Must | As a system, I meet the accuracy acceptance threshold | ≥ 90% of in-scope test-set questions answered relevantly without hallucination | Done — 93% after fix |
| Must | As a system, I stay within the hallucination ceiling | ≤ 3% hallucination rate on the validated test set | Done — 2.1% after chunking fix (initial: 8%) |

### Epic E3 — Trust, Safety & Guardrails
| Priority | Story | Acceptance Criteria | Status |
|---|---|---|---|
| Must | As a user, I am handed off to a human when the bot isn't confident | 100% of below-threshold queries escalated with full context, no dead-ends | Done |
| Must | As a system, I redact PII from retrieved content and logged queries | PII redaction verified end-to-end on a sample of real (anonymized) query patterns | Done |
| Must | As a system, I resist prompt-injection attempts | No successful injections in final adversarial test pass | Done |
| Must | As a system, I never expose one user's data to another | Strict access scoping — general knowledge content only | Done |
| Must | As a system, I block unsafe workaround suggestions | Guardrail rule blocking change-control bypass suggestions (added after pilot near-miss) | Done |

### Epic E4 — Conversation Experience
| Priority | Story | Acceptance Criteria | Status |
|---|---|---|---|
| Must | As a user, I interact with a tone that feels natural, not robotic | UAT tone feedback addressed via a dedicated tone-revision pass | Done |
| Should | As a user, I experience a graceful, clearly human handoff when escalated | Escalation experience designed with UX, validated in UAT | Done |

### Epic E5 — Channel Integration
| Priority | Story | Acceptance Criteria | Status |
|---|---|---|---|
| Must | As a user, I can access the bot via Microsoft Teams | Functional in UAT | Done |
| Must | As a user, I can access the bot via the self-service portal | Functional in UAT | Done |
| Must | As a user, I get a response within latency targets | ≤ 3 seconds average response latency | Done — 2.4s after optimization |
| Should | As a user with accessibility needs, I can use the Teams interface with a screen reader | Accessibility check completed and passed | Done |

### Epic E6 — Evaluation & Responsible AI
| Priority | Story | Acceptance Criteria | Status |
|---|---|---|---|
| Must | As a compliance stakeholder, I need documented bias/fairness testing before sign-off | RAI review completed; no concerns of note identified in this domain | Done |
| Must | As a compliance stakeholder, I need documented model limitations | Known limitations documented (no account-level changes, no multilingual, no HR/Finance in v1) | Done |
| Must | As a sponsor, I need UAT validation beyond internal testing | 8 service desk agents + 25 end-user volunteers across 3 departments | Done |

### Epic E7 — Rollout & Change Management
| Priority | Story | Acceptance Criteria | Status |
|---|---|---|---|
| Must | As a sponsor, I need a phased rollout with a rollback option | Pilot → expanded pilot → full company, with named rollback owner and triggers | Done |
| Must | As an employee, I need clear communication that this tool supports, not threatens, my job | Communications plan addresses staff representative / union concerns directly | Done |
| Should | As a pilot user, I need a guided walkthrough if I don't know the tool exists | Added mid-pilot after adoption-gap diagnosis | Done |

### Epic E8 — Governance & Monitoring
| Priority | Story | Acceptance Criteria | Status |
|---|---|---|---|
| Must | As a sponsor, I need ongoing KPI ownership, not informal monitoring | Named owner per KPI, defined cadence and thresholds | Done |
| Must | As a service desk stakeholder, I need KB content to stay current automatically | 5-business-day update SLA tied to IT change management | Done |
| Must | As finance, I need cost-per-query drift caught early | Monthly monitoring with a 10%+ deviation trigger | Done — drift caught and corrected within month one |

### Epic E9 (Phase 2 — Deferred) — Multilingual & Channel Expansion
| Priority | Story | Status |
|---|---|---|
| Won't (this release) | As a non-English-speaking user, I can interact with the bot in my language | Deferred to Phase 2 via formal change request |
| Won't (this release) | As a user, I can interact with the bot via voice channel | Deferred to Phase 2 |

### Epic E10 (Phase 2 — Deferred) — Domain Expansion
| Priority | Story | Status |
|---|---|---|
| Won't (this release) | As an HR query user, I can get self-service answers from the bot | Deferred; contingent on HR's own KB readiness |
| Won't (this release) | As a Finance query user, I can get self-service answers from the bot | Deferred; contingent on Finance's own KB readiness |

### Epic E11 (Phase 2 — Deferred) — Proactive Assistance
| Priority | Story | Status |
|---|---|---|
| Won't (this release) | As a user, I am proactively notified of a likely upcoming issue | Explicitly parked pending a dedicated Responsible AI review of that use case |

## 5. Backlog Health Notes

- All **Must** stories for Phase 1 launch are **Done** as of the 90-day outcomes review.
- No story was descoped to protect the launch date; the hallucination-rate and bias-review gates were held even under schedule pressure (see Risk Register RR1, RR13).
- Phase 2 backlog items (E9–E11) are intentionally **not sized or sprint-planned** yet — they require their own readiness work (HR/Finance KB audits, a dedicated RAI review for proactive suggestions) before entering a future Sprint Plan.

---
*Prepared by Prachi Sharma — AI Project Manager · Technical PM · Gen AI Delivery Lead*
