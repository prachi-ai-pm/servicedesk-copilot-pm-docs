# Project Budget

**Project Name:** ServiceDesk Copilot — AI-Assisted Tier-1 IT Support
**Document Owner:** Prachi Sharma, AI/ML Project Manager
**Status:** Approved (build) — actuals tracked through 90 days post-launch
**Version:** 1.0
**Date:** [Insert Last Updated Date]

---

## 1. Purpose

This document details the approved project budget, its breakdown by cost category and phase, and actual spend/run-cost performance through the first 90 days post-launch. It expands on the headline figures in the Business Case with the level of detail Finance and the sponsor used to track cost discipline throughout delivery.

## 2. Budget Summary

| Category | Amount |
|---|---|
| One-time build cost (approved) | $145,000 |
| Projected run cost (approved) | ~$3,800/month (~$45,600/year) |
| **Total Year 1 cost envelope (approved)** | **~$190,600** |
| Projected annualized savings run-rate | ~$300,000–$324,000 |

## 3. One-Time Build Cost Breakdown

| Cost Category | Description | Estimated Allocation |
|---|---|---|
| Labor — Project Manager | 1 PM, 16 weeks discovery-to-launch | $32,000 |
| Labor — ML / Data Engineers (×2) | Pipeline, retrieval, hybrid search, model integration | $58,000 |
| Labor — Backend / Integration Engineer | Teams integration, API abstraction layer, infrastructure | $22,000 |
| Labor — Conversation / UX Designer | Tone, persona, escalation UX, tone-revision pass | $11,000 |
| Labor — QA Analyst | UAT coordination, adversarial testing | $9,000 |
| Security / Compliance / Finance (part-time partners) | Architecture review, RAI review, data audit support | $8,000 |
| Tooling & setup | Azure AI Search indexing setup, dev/test environment provisioning | $5,000 |
| **Total build cost** | | **$145,000** |

*(Labor allocations are illustrative estimates consistent with the case study's stated team composition and 16-week duration; actual internal labor costing methodology may vary by organization.)*

## 4. Ongoing Run Cost Breakdown (Monthly, Forecast)

| Cost Category | Description | Forecast Monthly Cost |
|---|---|---|
| Model inference (Azure OpenAI) | GPT-4o-class model calls at expected query volume | ~$2,100 |
| Azure AI Search indexing & hosting | Hybrid vector + keyword index hosting and queries | ~$1,200 |
| Logging / monitoring infrastructure | Query logging (per retention policy), KPI dashboards | ~$350 |
| Miscellaneous / contingency | Buffer for usage variance | ~$150 |
| **Total forecast run cost** | | **~$3,800/month** |

## 5. Cost-per-Query Forecast vs. Actual

| Metric | Forecast | Actual (Early Post-Launch) | Actual (After Optimization) |
|---|---|---|---|
| Cost per query | $0.041 | $0.049 (briefly, ~20% above forecast) | $0.038 |

**Root cause of the early overshoot:** Investigation traced the ~20% cost-per-query overshoot in month one to longer-than-expected average context windows being passed to the model. This was corrected through prompt and context optimization, bringing cost per query below the original forecast.

**Governance response:** This drift was caught via the Stage 7 monthly cost-per-query monitoring cadence (PM + Finance, with a 10%+ deviation trigger) rather than surfacing as a surprise at a later finance review — see the Risk Register (RR17) and RAID Log (I5).

## 6. Budget by Project Phase

| Phase | Budget Allocation | Notes |
|---|---|---|
| Stage 1 — Discovery & Business Case | Included in PM labor | Discovery interviews, ticket data analysis, charter drafting |
| Stage 2 — Requirements & Data Readiness | Included in PM + Data Science labor | Data readiness audit, 150-question test-set construction (4 SMEs) |
| Stage 3 — Solution Design & Architecture | Included in PM + Architect + Security labor | Build-vs-host-vs-buy evaluation, ADR |
| Stage 4 — Build (8 sprints) | Majority of engineering labor (~$80,000 of the $145,000 build cost) | Includes the 1 additional sprint added for hybrid search |
| Stage 5 — Evaluation & RAI Review | Included in QA + Data Science + Compliance labor | Test-set evaluation, UAT, bias/fairness review |
| Stage 6 — Deployment & Change Management | Included in PM + Internal Comms allocation | Phased rollout, communications materials |
| Stage 7 — Post-Launch Governance | Covered by ongoing run cost + part-time PM/Finance oversight | KPI monitoring, KB freshness SLA, cost optimization |

## 7. Budget Variance Log

| Item | Forecast | Actual | Variance | Disposition |
|---|---|---|---|---|
| Build timeline (data readiness slip) | 16 weeks | ~16 weeks (absorbed) | ~3-week data-cleanup delay absorbed within the overall schedule via a sponsor-approved change, not a separate cost overrun | Approved as a documented change (Stage 2) |
| Additional sprint for hybrid search | 7 sprints (pre-finding estimate) | 8 sprints | +1 sprint (~2 weeks) of engineering labor | Communicated to sponsor as a deliberate accuracy trade-off, not a quiet slip |
| Cost per query (month 1) | $0.041 | $0.049 | +~20% | Corrected via prompt/context optimization; resolved within month one |
| Cost per query (post-optimization) | $0.041 | $0.038 | −~7% (favorable) | No action needed |

## 8. Return on Investment Summary

| Metric | Value |
|---|---|
| Total Year 1 cost envelope | ~$190,600 |
| Actual annualized savings run-rate @ 90 days | ~$300,000 (ramping toward the ~$324,000 target as full-rollout months annualize) |
| Net projected Year 1 benefit | ~$109,400+ (savings run-rate less total cost envelope, before full-rollout annualization is complete) |
| Indicative payback period | Within Year 1, based on realized 90-day deflection (28% vs. a 25% target) |

*(These figures are illustrative projections consistent with the case study's stated outcomes, not audited financial statements.)*

## 9. Budget Governance

- **Funding approval:** $145,000 build cost and ~$3,800/month run cost approved by the VP, IT Operations, with funding confirmed by Finance during Stage 1 discovery.
- **Change control:** Any budget-impacting scope change (e.g., the additional hybrid-search sprint, the deferred multilingual request) is routed through the formal change-request process before being absorbed into the budget — see the Scope Statement, Section 9.
- **Ongoing monitoring:** Cost per query is reviewed monthly by the PM and Finance jointly, with a 10%+ forecast deviation as the trigger for an optimization review — see the Risk Register (RR17) and Governance & Monitoring Plan (Stage 7).

---
*Prepared by Prachi Sharma — AI Project Manager · Technical PM · Gen AI Delivery Lead*
