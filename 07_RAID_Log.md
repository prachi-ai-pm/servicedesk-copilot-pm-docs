# RAID Log

**Project Name:** ServiceDesk Copilot — AI-Assisted Tier-1 IT Support
**Document Owner:** Prachi Sharma, AI/ML Project Manager
**Status:** Living document — reviewed weekly with sponsor
**Version:** 1.0
**Date:** [Insert Last Updated Date]

---

## 1. Purpose

This log tracks Risks, Assumptions, Issues, and Dependencies across the project lifecycle. It was reviewed weekly with the sponsor as the actual mechanism for catching and acting on risk early — not as a compliance exercise.

## 2. Risks

| ID | Description | Stage Identified | Owner | Likelihood | Impact | Mitigation | Status |
|---|---|---|---|---|---|---|---|
| R1 | Key ML engineer unavailability could stall pipeline work mid-sprint | 4 (flagged at kickoff) | PM | Medium | High | Second engineer cross-trained in advance as a documented contingency | **Mitigated** — engineer became unavailable for 2 weeks; contingency activated immediately, sprint plan absorbed a short ramp-up cost instead of a hard stop |
| R2 | Retrieval accuracy on short/informal queries may be insufficient with vector-only search | 3–4 | ML Engineer | Medium | High | Add hybrid keyword + vector search if accuracy testing confirms the gap | **Realized & resolved** — confirmed in mid-sprint testing (e.g., "vpn not working" returned weak matches); backlog reprioritized, one sprint added |
| R3 | Knowledge base fragmentation across three disconnected systems could undermine retrieval quality | 1 (flagged in charter) | PM | High | High | Formal data readiness audit before any retrieval pipeline work begins | **Realized & resolved** — audit confirmed 18%/35% outdated/duplicate content; cleanup completed in Stage 2, ~3-week schedule impact approved by sponsor |
| R4 | Architecture disagreement between Security (in-tenant) and original vendor pitch (public SaaS) could stall the business case | 1 | PM | Medium | Medium | Defer architecture decision to Stage 3 with a documented placeholder assumption | **Closed** — resolved at Stage 3 gate; Option B (Azure OpenAI + Azure AI Search) selected |
| R5 | Vendor lock-in risk if the team defaults into one platform without a documented comparison | 3 | Procurement / PM | Medium | Medium | Pause informal decision; run documented 3-option comparison | **Closed** — comparison completed; Option B retained on record with risk acknowledged and an abstraction-layer mitigation |
| R6 | No formal escalation path when the bot lacks confidence could create a trust risk | 3 | PM / UX | Medium | High | Add hard requirement: any below-threshold answer triggers explicit human handoff with context | **Closed** — surfaced in a pre-UAT dry run with the Service Desk Manager; requirement added before build proceeded |
| R7 | Hallucination rate could exceed the 3% PRD threshold | 5 | Data Science Lead | Medium | High | Root-cause analysis and chunking-strategy fix before allowing sign-off | **Realized & resolved** — initial rate came in at 8%; traced to weak chunking on password-policy articles; fixed and re-tested at 2.1% |
| R8 | Pressure to compress or skip the Responsible AI / bias review to hit a target launch date | 5 | PM / Compliance | Medium | High | Hold the RAI gate as non-negotiable; explain reputational/compliance exposure in plain terms to sponsor | **Closed** — sponsor agreed to a short, scoped delay rather than launching without the review |
| R9 | Low pilot-week adoption could be misdiagnosed as a product failure | 6 | PM | Medium | Medium | Quick survey to distinguish an awareness gap from a capability gap before concluding the product had failed | **Realized & resolved** — diagnosed as an awareness gap; guided Teams walkthrough added mid-pilot |
| R10 | A bot-suggested workaround could bypass a required change-control step | 6 | PM / Security | Low | High | Add explicit guardrail rule blocking that category of suggestion | **Realized & resolved (near-miss)** — caught during pilot before any employee acted on it; guardrail added before expanding beyond pilot department |
| R11 | Cost per query could drift above forecast post-launch | 7 | PM / Finance | Medium | Medium | Monitor monthly; investigate and optimize if 10%+ above forecast | **Realized & resolved** — crept ~20% above forecast within month one, traced to longer-than-expected context windows; corrected via prompt/context optimization |
| R12 | Answer quality could drift as source content ages without a formal freshness owner | 7 | Service Desk Manager | Medium | Medium | Tie KB updates to the IT change management process | **Realized & resolved** — a VPN tool change rolled out without a KB update, causing brief outdated guidance; standing 5-business-day update SLA established |

## 3. Assumptions

| ID | Description | Stage Identified | Owner | Validation Status |
|---|---|---|---|---|
| A1 | Existing KB content is substantially reusable after a cleanup pass | 1 | PM | **Partially invalidated** — Stage 2 audit found 18% (ServiceNow) and 35% (SharePoint) outdated/duplicate; remediated via SME review, deduplication, and 70 new articles |
| A2 | Security will approve an in-tenant model hosting option | 1 | PM | **Validated** — confirmed at the Stage 3 architecture gate (Option B selected) |
| A3 | Service Desk leadership will support a phased pilot rollout rather than a single big-bang launch | 1 | PM | **Validated** — phased rollout plan (pilot → expanded pilot → full company) executed as designed |
| A4 | IT Tier-1 alone represents the largest, cleanest, fastest win versus a multi-domain (HR/Finance) launch | 1 | PM | **Validated** — confirmed via effort-vs-impact exercise with ticket data; HR/Finance phased to a later release |

## 4. Issues

| ID | Description | Stage Identified | Owner | Resolution | Status |
|---|---|---|---|---|---|
| I1 | Hallucination rate on initial test exceeded the 3% threshold (came in at 8%) | 5 | Data Science Lead | Root-cause traced to weak chunking on password-policy articles; chunking strategy fixed and re-tested at 2.1% | **Resolved** |
| I2 | UAT users described the bot's tone as "robotic" and overly hedged | 5 | UX / Conversation Design | Tone pass completed before launch despite the short delay it caused | **Resolved** |
| I3 | Pilot-week adoption was lower than expected | 6 | PM | Diagnosed via quick survey as an awareness gap, not a capability gap; guided Teams walkthrough added mid-pilot | **Resolved** |
| I4 | A near-miss workaround suggestion could have bypassed required change control | 6 | Security / PM | Explicit guardrail rule added blocking that category of suggestion before expanding beyond the pilot | **Resolved** |
| I5 | Cost per query crept ~20% above forecast within the first month post-launch | 7 | PM / Engineering | Traced to longer-than-expected context windows; corrected via prompt and context optimization | **Resolved** |
| I6 | Answer drift after a VPN tool change rolled out without a corresponding KB update | 7 | Service Desk Manager | Standing SLA established: in-scope IT change records trigger a KB update within 5 business days | **Resolved (structural fix)** |

## 5. Dependencies

| ID | Description | Depends On | Owner | Status |
|---|---|---|---|---|
| D1 | Production data exposure requires Security sign-off | Stage 3 architecture gate | Information Security Officer | **Closed** — approved at Stage 3 gate |
| D2 | Build cannot begin against final requirements until the PRD is signed off | Stage 2 alignment workshop and audit completion | PM | **Closed** |
| D3 | Pilot rollout cannot proceed until UAT and Responsible AI sign-off are complete | Stage 5 gate | Service Desk Manager, InfoSec, Compliance, Sponsor | **Closed** |
| D4 | Expanded pilot (Phase 2) is contingent on Phase 1 success gate (no critical incidents, CSAT ≥ 4.0) | Stage 6 Phase 1 results | Sponsor | **Closed** |
| D5 | Full rollout (Phase 3) is contingent on sponsor sign-off of Phase 2 results | Stage 6 Phase 2 results | Sponsor | **Closed** |
| D6 | KB freshness is dependent on the IT change management process correctly flagging in-scope changes | ServiceNow change record process | Service Desk Manager | **Ongoing** |

---
*Prepared by Prachi Sharma — AI Project Manager · Technical PM · Gen AI Delivery Lead*
