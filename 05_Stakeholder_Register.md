# Stakeholder Register

**Project Name:** ServiceDesk Copilot — AI-Assisted Tier-1 IT Support
**Document Owner:** Prachi Sharma, AI/ML Project Manager
**Status:** Approved
**Version:** 1.0
**Date:** [Insert Approval Date]

---

## 1. Purpose

This register identifies all individuals and groups with an interest in, or impact on, ServiceDesk Copilot, along with their influence, interest, and the engagement approach used to manage each relationship throughout the project lifecycle.

## 2. Stakeholder Power/Interest Summary

| Stakeholder | Role / Title | Power | Interest | Engagement Strategy |
|---|---|---|---|---|
| VP, IT Operations | Executive Sponsor | High | High | **Manage closely** — weekly RAID log review, gate approvals, joint rollback decision authority |
| Prachi Sharma | AI Project Manager | High | High | Drives all engagement; accountable for delivery and governance |
| IT Operations Director | Discovery sponsor / business owner | High | High | **Manage closely** — discovery interviews, ticket volume/cost validation |
| Service Desk Manager | Operations owner, pilot decision-maker | High | High | **Manage closely** — rollback trigger ownership, KB freshness SLA owner, UAT sign-off |
| Information Security Officer | Security gate owner | High | Medium | **Manage closely** — architecture approval, PII/prompt-injection review, UAT sign-off |
| Compliance Officer | Regulatory & data governance gate owner | High | Medium | **Manage closely** — data residency, retention policy, RAI sign-off |
| Finance | Budget owner | Medium | High | **Keep satisfied** — funding envelope approval, ongoing cost-per-query tracking |
| Data Science Lead | Technical delivery — model/retrieval quality | Medium | High | **Keep informed / collaborate** — weekly evaluation reviews, hallucination-rate accountability |
| ML / Data Engineers (×2) | Build team | Medium | High | **Collaborate** — sprint execution, technical risk escalation |
| Backend / Integration Engineer | Build team | Medium | High | **Collaborate** — Teams integration, milestone tracking |
| Conversation / UX Designer | Build team | Medium | Medium | **Collaborate** — tone, persona, escalation experience design |
| QA Analyst | Build team | Medium | Medium | **Collaborate** — UAT coordination, adversarial prompt testing |
| Solution Architect | Architecture decision input | Medium | Medium | **Consult** — build-vs-host-vs-buy evaluation |
| Procurement | Vendor/contract risk | Medium | Low | **Consult** — vendor lock-in risk assessment |
| Legal | Data retention & logging policy | Medium | Low | **Consult** — query log retention policy input |
| Service Desk SMEs (×4) | Test-set construction | Low | High | **Collaborate** — ground-truth Q&A labeling |
| Pilot department staff representatives / union | Workforce impact concern | Medium | High | **Manage closely during rollout** — addressed directly in communications plan to frame the tool as augmentation, not job risk |
| Pilot end users (Finance dept., then IT & Engineering) | System users | Low | High | **Keep informed** — Teams pop-up walkthrough, FAQ, escalation path communication |
| All employees (post full rollout) | System users | Low | Medium | **Keep informed** — company-wide email, ongoing CSAT survey |

## 3. Detailed Stakeholder Profiles

### VP, IT Operations (Executive Sponsor)
- **Interest:** Cost reduction, service-level improvement, defensible governance
- **Influence:** Final approval authority on charter, budget, and rollback decisions
- **Concerns raised:** Pressure to compress the Responsible AI review timeline ahead of a target launch date — resolved by accepting a short, scoped delay rather than skipping the review
- **Engagement:** Weekly RAID log review; joint rollback decision authority with PM

### IT Operations Director
- **Interest:** Validating the true scope and cost of the Tier-1 ticket problem
- **Influence:** Shaped the initial problem-sizing and scope-narrowing decision
- **Engagement:** Structured discovery interview in Stage 1

### Service Desk Manager
- **Interest:** Operational impact on the service desk team; rollout safety
- **Influence:** UAT sign-off; rollback trigger ownership; KB freshness SLA owner
- **Concerns raised:** Multilingual support request mid-build (routed through formal change request, deferred to Phase 2)
- **Engagement:** Manage closely throughout build, evaluation, and post-launch governance

### Information Security Officer
- **Interest:** Data residency, PII protection, prompt-injection resistance
- **Influence:** Rejected the original fine-tuning-on-raw-ticket-data plan, reshaping the architecture toward pure RAG
- **Engagement:** Architecture gate approval (Stage 3); UAT and RAI sign-off (Stage 5)

### Compliance Officer
- **Interest:** Regulatory exposure, data handling defensibility, bias/fairness documentation
- **Influence:** RAI sign-off authority; held the line alongside the PM when there was pressure to skip the bias review
- **Engagement:** Discovery interview (Stage 1); RAI checklist sign-off (Stage 5)

### Finance
- **Interest:** Funding envelope, build-vs-buy return threshold, ongoing cost-per-query tracking
- **Influence:** Approved the $145,000 build budget and ~$3,800/month run-cost envelope
- **Concerns raised:** Cost per query crept ~20% above forecast within the first month post-launch — addressed jointly with the PM via prompt/context optimization
- **Engagement:** Discovery interview (Stage 1); monthly cost review (Stage 7)

### Data Science Lead
- **Interest:** Retrieval/model quality, hallucination rate, technical feasibility
- **Influence:** Owns the accuracy and hallucination-rate metrics that gate launch
- **Engagement:** Requirements workshops (Stage 2); weekly evaluation reviews (Stage 5); post-launch drift monitoring (Stage 7)

### Procurement
- **Interest:** Vendor lock-in exposure, contract/pricing risk
- **Influence:** Flagged vendor lock-in late in Stage 3, prompting a paused, documented three-option comparison before the architecture decision was finalized
- **Engagement:** Consulted during the build-vs-host-vs-buy evaluation

### Legal
- **Interest:** Query log retention policy, data usage boundaries
- **Influence:** Defined retention policy constraints incorporated into the PRD
- **Engagement:** Consulted during requirements definition (Stage 2)

### Pilot Department Staff Representatives / Union
- **Interest:** Job security concerns related to automation of service desk work
- **Influence:** Raised concerns directly during Stage 6 rollout planning
- **Engagement:** Addressed explicitly in the communications plan — framing the tool as a help to employees, not a threat to service desk jobs

### Pilot & Rollout End Users
- **Interest:** Ease of use, trust in answers, ability to reach a human
- **Influence:** Adoption behavior directly determines whether projected benefits are realized
- **Concerns raised:** Lower-than-expected pilot-week adoption — diagnosed as an awareness gap (not a capability or product gap) via a quick survey, and corrected with a guided Teams walkthrough
- **Engagement:** Teams pop-up walkthrough, FAQ, post-launch survey

## 4. Stakeholder Engagement Cadence Summary

| Engagement | Frequency | Stakeholders |
|---|---|---|
| RAID log review | Weekly | PM, Sponsor |
| Sprint standups / planning | Per sprint (2-week cycle) | PM, build team |
| KPI review | Weekly (deflection, hallucination); Monthly (cost, CSAT) | PM, Service Desk Manager, Data Science Lead, Finance |
| Gate approvals | At each stage transition | Sponsor, Security, Compliance |
| Pilot adoption monitoring | Daily (week one of each rollout phase) | PM, Service Desk Manager |
| KB freshness review | Triggered by IT change record (5-business-day SLA) | Service Desk Manager |

---
*Prepared by Prachi Sharma — AI Project Manager · Technical PM · Gen AI Delivery Lead*
