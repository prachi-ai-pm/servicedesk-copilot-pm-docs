# Business Case

**Project Name:** ServiceDesk Copilot — AI-Assisted Tier-1 IT Support
**Document Owner:** Prachi Sharma, AI/ML Project Manager
**Status:** Approved
**Version:** 1.0
**Date:** [Insert Approval Date]

---

## 1. Executive Summary

Atlas Industrial Group's IT service desk handles approximately 9,000 Tier-1 tickets per month at a fully loaded cost of roughly $1.3M annually. About 65% of this volume falls into five repetitive, low-complexity categories well suited to automation. ServiceDesk Copilot, a Retrieval-Augmented Generation (RAG) chatbot, is proposed to deflect a meaningful share of this volume to self-service while preserving a frictionless escalation path to human agents and operating within enterprise security, compliance, and cost constraints.

This business case replaces an unscoped vendor pitch — a generic "AI helpdesk" platform — with a validated, fundable MVP backed by 12 months of ticket data and named accountable stakeholders.

## 2. Problem Statement

| Dimension | Detail |
|---|---|
| Current volume | ~9,000 Tier-1 tickets/month |
| Fully loaded cost per ticket | $12 |
| Annual cost exposure | ~$1.3M |
| Automatable volume | ~65% across five repetitive categories (password resets, software access, VPN/connectivity, printer/hardware, general how-to) |
| Current state | All volume handled by human agents around the clock, including highly repetitive, low-complexity queries |

## 3. Strategic Alignment

The project supports IT Operations' goals of cost containment and service-level improvement without compromising security or compliance posture, and positions the organization to evaluate further AI-assisted service domains (HR, Finance) in later phases once readiness is validated.

## 4. Options Considered

| Option | Description | Assessment |
|---|---|---|
| **Do nothing** | Continue current fully human-handled model | No cost reduction; ticket volume and cost continue to scale with headcount/business growth |
| **Off-the-shelf SaaS chatbot** | Adopt the vendor's generic "AI helpdesk" platform as originally pitched | Fastest to deploy but lowest data control; data leaves tenant; conflicts with residency/security requirements |
| **Self-hosted open-source LLM** | Build and operate the full stack in-house | Highest control and lowest lock-in, but slowest time-to-market and highest fixed infrastructure cost |
| **Recommended: Azure OpenAI + Azure AI Search (RAG)** | In-tenant managed service, hybrid vector + keyword retrieval over curated KB content | Meets data residency and security requirements; fast time-to-market using existing Azure footprint; moderate, mitigated vendor lock-in |

*(Full option-by-option comparison is documented in the Architecture Decision Record produced in Stage 3.)*

## 5. Recommended Solution

Build ServiceDesk Copilot on **Azure OpenAI (GPT-4o-class model) with Azure AI Search** for hybrid retrieval, sourcing content from the ServiceNow Knowledge Base and SharePoint, delivered via Microsoft Teams and a self-service portal widget. The system uses confidence-threshold routing to escalate uncertain answers to a human agent rather than risk a confidently wrong response.

## 6. Costs

| Item | Amount |
|---|---|
| One-time build cost | $145,000 |
| Ongoing run cost | ~$3,800/month (model inference, search indexing, hosting) |
| Implied Year 1 total cost | ~$145,000 + ~$45,600 (run cost) ≈ $190,600 |

## 7. Benefits & Return

| Benefit | Quantification |
|---|---|
| Ticket deflection | Target 25% of eligible Tier-1 volume within 90 days of launch (achieved 28% — see Outcomes Summary) |
| Annualized savings run-rate | ~$300,000–$324,000 projected, based on deflected ticket volume at $12/ticket fully loaded cost |
| Service availability | 24/7 self-service for the five highest-volume query categories, reducing after-hours load on human agents |
| Customer experience | Target CSAT ≥ 4.0/5, maintaining or improving on the human-handled baseline |

**Indicative payback:** At a ~$300K annualized savings run-rate against a ~$190,600 Year 1 total cost, the project is projected to pay back its build investment within the first year of full operation, with ongoing run costs (~$45,600/year) substantially below the recurring savings thereafter. *(Illustrative; not a financial guarantee — see Section 9 for cost sensitivity.)*

## 8. Risks to the Business Case

| Risk | Impact on Case |
|---|---|
| Knowledge base fragmentation across three disconnected systems with overlap and outdated content | Could degrade answer accuracy if not remediated before launch (addressed via the Stage 2 Data Readiness Assessment) |
| Hallucination / confidently wrong answers | Directly threatens the CSAT and trust assumptions underpinning the benefit case |
| Vendor/model cost drift | Cost per query crept ~20% above forecast within the first month post-launch in practice, driven by longer-than-expected context windows; required active engineering optimization to correct |
| Low initial adoption | Diagnosed post-launch as an awareness gap rather than a product failure; required an active change-management response to realize projected benefits |

## 9. Funding Decision & Conditions

| Decision | Detail |
|---|---|
| **Outcome** | Approved by VP, IT Operations |
| **Conditions** | Security and Compliance sign-off required before any production data exposure (tracked as a Stage 3 gate) |
| **Funding envelope** | $145,000 one-time + ~$3,800/month run cost, as confirmed with Finance during discovery |

## 10. Actual Outcomes (90 Days Post-Launch)

| Metric | Baseline | 90-Day Target | Actual @ 90 Days |
|---|---|---|---|
| Monthly Tier-1 ticket volume | 9,000 | ↓ 25% | ↓ 28% (6,480) |
| Annualized cost savings run-rate | — | ~$324,000 | ~$300,000 (ramping to target as full-rollout months annualize) |
| Hallucination rate | N/A (pre-launch) | ≤ 3% | 2.1% |
| User CSAT | N/A (pre-launch) | ≥ 4.0/5 | 4.2/5 |
| Average response latency | N/A (pre-launch) | ≤ 3 seconds | 2.4 seconds |
| Cost per query | $0.041 (forecast) | Within 10% of forecast | $0.038 after optimization (briefly peaked at $0.049) |

This validates the original business case: the realized benefit (28% deflection, ~$300K savings run-rate) exceeded the approved target, and cost and quality risks that emerged post-launch were identified and corrected within the governance structure established in Stage 7.

---
*Prepared by Prachi Sharma — AI Project Manager · Technical PM · Gen AI Delivery Lead*
