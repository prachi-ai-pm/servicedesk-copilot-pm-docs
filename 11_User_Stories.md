# User Stories

**Project Name:** ServiceDesk Copilot — AI-Assisted Tier-1 IT Support
**Document Owner:** Prachi Sharma, AI/ML Project Manager
**Status:** Living document
**Version:** 1.0
**Date:** [Insert Last Updated Date]

---

## 1. Purpose

This document expands the Product Backlog's epics into full user stories with persona context, acceptance criteria in Given/When/Then format, and story-point estimates. It is the detailed authoring layer beneath the backlog — engineers and QA work from this document; the Product Backlog and Sprint Plan track priority and timing.

## 2. Personas

| Persona | Description |
|---|---|
| **Employee End User** | Any of Atlas Industrial Group's ~12,000 employees submitting an IT query via Teams or the self-service portal |
| **Service Desk Agent** | Human Tier-1 agent who receives escalated conversations |
| **Service Desk Manager** | Owns operational performance, rollback decisions, and KB freshness |
| **Data Science Lead** | Owns model/retrieval quality and evaluation |
| **Security / Compliance Officer** | Owns data protection, access control, and regulatory sign-off |
| **PM / Sponsor** | Owns scope, budget, and governance decisions |

## 3. Story Format

Each story follows: **As a** [persona], **I want** [capability], **so that** [benefit] — with acceptance criteria in **Given/When/Then** form, a story-point estimate (Fibonacci: 1, 2, 3, 5, 8, 13), and a link back to its Product Backlog epic.

---

## Epic E1 — Knowledge Ingestion & Retrieval

### US-1.1 — Ingest ServiceNow KB content
**As a** system, **I want** to ingest reviewed ServiceNow KB articles, **so that** I have a primary, trustworthy retrieval source.
- **Given** ~420 SME-reviewed ServiceNow articles, **when** the ingestion pipeline runs, **then** all articles are normalized and available to the chunking pipeline.
- **Points:** 5 | **Status:** Done

### US-1.2 — Deduplicate SharePoint IT Wiki content
**As a** system, **I want** SharePoint content deduplicated against ServiceNow, **so that** retrieval doesn't surface conflicting or redundant answers.
- **Given** ~260 SharePoint articles with known overlap, **when** deduplication runs against the ServiceNow corpus, **then** duplicate and outdated articles are archived and excluded from the active index.
- **Points:** 5 | **Status:** Done

### US-1.3 — Exclude out-of-audience content
**As a** Data Science Lead, **I want** Confluence Engineering Notes excluded from the retrieval corpus, **so that** Tier-1 end users never receive engineer-facing content.
- **Given** 90 Confluence articles aimed at an engineering audience, **when** corpus scoping is applied, **then** none of these articles are indexed for end-user retrieval.
- **Points:** 2 | **Status:** Done

### US-1.4 — Correct inconsistent chunking
**As a** system, **I want** content chunked consistently, **so that** retrieval quality isn't degraded by uneven chunk boundaries.
- **Given** the data readiness audit finding of inconsistent chunking, **when** the corrected chunking strategy is applied, **then** retrieval accuracy on the test set improves measurably versus the pre-fix baseline.
- **Points:** 8 | **Status:** Done

### US-1.5 — Close content gaps with new articles
**As an** Employee End User, **I want** the bot to know about recent changes (e.g., the VPN tool change), **so that** I get current guidance instead of outdated answers.
- **Given** an identified content gap, **when** SMEs author a new article, **then** the article is ingested and retrievable within the same sprint.
- **Points:** 3 | **Status:** Done (70 articles written)

---

## Epic E2 — Hybrid Search & Accuracy

### US-2.1 — Hybrid keyword + vector search
**As an** Employee End User, **I want** accurate results for short, informal queries like "vpn not working," **so that** I don't get irrelevant or weak matches.
- **Given** a short, informal query, **when** hybrid keyword + vector retrieval runs, **then** the top-returned result is relevant per the labeled test set definition of relevance.
- **Points:** 13 | **Status:** Done — added mid-build after a vector-only accuracy finding

### US-2.2 — Build the ground-truth test set
**As a** Data Science Lead, **I want** a labeled set of real, representative questions, **so that** "accuracy" is measurable rather than subjective.
- **Given** 4 Service Desk SMEs and real ticket patterns, **when** the labeling exercise is run, **then** 150 questions have an approved ground-truth answer.
- **Points:** 8 | **Status:** Done

### US-2.3 — Meet the relevance/accuracy threshold
**As a** Data Science Lead, **I want** ≥ 90% of test-set questions answered relevantly without hallucination, **so that** the system meets the PRD's launch bar.
- **Given** the 150-question test set, **when** the full pipeline is evaluated, **then** relevance/correctness is ≥ 90%.
- **Points:** 5 | **Status:** Done — 93% after fix (initial: 84%)

### US-2.4 — Stay within the hallucination ceiling
**As a** Compliance Officer, **I want** hallucination rate ≤ 3% on the validated test set, **so that** the system doesn't erode user trust with confidently wrong answers.
- **Given** the 150-question test set, **when** evaluated post-fix, **then** hallucination rate is ≤ 3%.
- **Points:** 8 | **Status:** Done — 2.1% after chunking fix (initial: 8%)

---

## Epic E3 — Trust, Safety & Guardrails

### US-3.1 — Escalate low-confidence answers to a human
**As an** Employee End User, **I want** to be handed off to a human agent when the bot isn't confident, **so that** I never receive a confidently wrong answer dressed up as correct.
- **Given** a query whose retrieval confidence falls below the agreed threshold, **when** the bot responds, **then** the conversation is escalated to a human agent with full context, never presented as a final answer.
- **Points:** 8 | **Status:** Done — added as a hard, non-negotiable requirement after a pre-UAT dry-run finding

### US-3.2 — Redact PII from retrieved content and logs
**As a** Security Officer, **I want** PII redacted from retrieved content and logged queries, **so that** the system never exposes personal data through the model or its logs.
- **Given** retrieved content or a logged query containing PII, **when** it is processed, **then** PII is redacted before reaching the model or persistent storage.
- **Points:** 8 | **Status:** Done — verified end-to-end on anonymized sample patterns

### US-3.3 — Resist prompt injection
**As a** Security Officer, **I want** the system tested against adversarial prompts, **so that** an employee can't manipulate the bot into unintended behavior.
- **Given** a standard adversarial prompt set, **when** tested against the production system, **then** zero successful injections occur in the final test pass.
- **Points:** 5 | **Status:** Done

### US-3.4 — Scope access to general knowledge only
**As a** Security Officer, **I want** strict access scoping, **so that** one employee can never retrieve another employee's ticket or account data through the bot.
- **Given** any user query, **when** retrieval executes, **then** only general knowledge base content is returned — never ticket- or account-level data belonging to another user.
- **Points:** 5 | **Status:** Done

### US-3.5 — Block unsafe workaround suggestions
**As a** Service Desk Manager, **I want** the bot blocked from suggesting change-control bypasses, **so that** a near-miss incident can't recur.
- **Given** a query pattern resembling the pilot near-miss, **when** the bot would otherwise suggest a change-control bypass, **then** the guardrail rule blocks the suggestion and routes to escalation instead.
- **Points:** 3 | **Status:** Done — added after a pilot near-miss, before expanding beyond the pilot department

---

## Epic E4 — Conversation Experience

### US-4.1 — Natural, non-robotic tone
**As an** Employee End User, **I want** the bot to sound natural rather than robotic and overly hedged, **so that** I trust and actually want to use it.
- **Given** UAT feedback describing the bot's tone as robotic, **when** the tone-revision pass is applied, **then** re-tested UAT satisfaction improves measurably.
- **Points:** 5 | **Status:** Done — UAT satisfaction rose from 3.4 to 4.2 (target: ≥ 4.0)

### US-4.2 — Graceful human handoff experience
**As an** Employee End User, **I want** a clear, graceful handoff when I'm escalated, **so that** I don't feel dropped or ignored.
- **Given** an escalation trigger, **when** the handoff occurs, **then** the user is told plainly that they're being connected to a human agent, with their context already carried over.
- **Points:** 3 | **Status:** Done

---

## Epic E5 — Channel Integration

### US-5.1 — Access via Microsoft Teams
**As an** Employee End User, **I want** to reach the bot inside Microsoft Teams, **so that** I don't have to leave the tool I already work in.
- **Given** a Teams-integrated deployment, **when** a user opens the bot in Teams, **then** the full query/escalation experience functions identically to the portal.
- **Points:** 8 | **Status:** Done — functional in UAT

### US-5.2 — Access via the self-service portal
**As an** Employee End User, **I want** to reach the bot via the self-service portal widget, **so that** I have a channel option outside of Teams.
- **Given** a portal-integrated deployment, **when** a user opens the widget, **then** the full query/escalation experience functions identically to Teams.
- **Points:** 5 | **Status:** Done — functional in UAT

### US-5.3 — Respond within latency targets
**As an** Employee End User, **I want** a fast response, **so that** the tool feels like a real shortcut, not a slower alternative to filing a ticket.
- **Given** expected production load, **when** a query is submitted, **then** average response latency is ≤ 3 seconds.
- **Points:** 5 | **Status:** Done — 2.4s after optimization (initial: 2.8s)

### US-5.4 — Screen-reader accessibility in Teams
**As an** Employee End User with accessibility needs, **I want** the Teams interface to work with a screen reader, **so that** I'm not excluded from using the tool.
- **Given** a screen-reader-dependent user, **when** they interact with the bot in Teams, **then** all interactions are correctly announced and navigable.
- **Points:** 3 | **Status:** Done

---

## Epic E6 — Evaluation & Responsible AI

### US-6.1 — Bias and fairness review
**As a** Compliance Officer, **I want** documented bias and fairness testing, **so that** I can sign off with confidence the system doesn't produce discriminatory outputs.
- **Given** simulated user phrasing variations across demographics, **when** outputs are reviewed, **then** no patterns of concern are identified, and the review is documented for audit.
- **Points:** 8 | **Status:** Done — held as a non-negotiable gate despite sponsor pressure to compress the timeline

### US-6.2 — Document known model limitations
**As a** Compliance Officer, **I want** known limitations documented, **so that** users and auditors understand what the system is not designed to do.
- **Given** the v1 scope boundaries, **when** the limitations document is produced, **then** it explicitly lists exclusions (account-level changes, multilingual, HR/Finance topics).
- **Points:** 2 | **Status:** Done

### US-6.3 — UAT with real agents and end users
**As a** PM, **I want** UAT validation beyond internal testing, **so that** launch confidence reflects real-world usage, not just lab conditions.
- **Given** a 2-week UAT period, **when** 8 service desk agents and 25 end-user volunteers across 3 departments participate, **then** sign-off conditions (hallucination fix, tone revision) are verified in re-test before approval.
- **Points:** 8 | **Status:** Done

---

## Epic E7 — Rollout & Change Management

### US-7.1 — Phased rollout with rollback option
**As a** Sponsor, **I want** a phased rollout with a defined rollback trigger and owner, **so that** I have a real decision point if the bot underperforms, not an irreversible big-bang launch.
- **Given** the Phase 1 pilot, **when** a rollback trigger condition is met, **then** the VP of IT Operations and PM jointly decide within 24 hours.
- **Points:** 5 | **Status:** Done

### US-7.2 — Workforce reassurance communications
**As an** Employee End User (and staff representative), **I want** clear communication that this tool supports, not threatens, my job, **so that** I don't resist or distrust the rollout.
- **Given** a pilot department with staff representative concerns, **when** the communications plan is executed, **then** concerns are addressed directly prior to company-wide messaging.
- **Points:** 3 | **Status:** Done

### US-7.3 — Guided walkthrough for low awareness
**As an** Employee End User, **I want** a guided walkthrough if I don't know the tool exists, **so that** I actually discover and use it.
- **Given** a diagnosed awareness gap (not a capability gap), **when** the guided Teams walkthrough is added mid-pilot, **then** adoption increases without further product changes.
- **Points:** 3 | **Status:** Done

---

## Epic E8 — Governance & Monitoring

### US-8.1 — Named KPI ownership
**As a** Sponsor, **I want** every KPI to have a named owner and cadence, **so that** monitoring is somebody's job, not everyone's vague responsibility.
- **Given** the post-launch KPI set, **when** the governance plan is stood up, **then** every KPI has an owner, a cadence, and a defined threshold/trigger.
- **Points:** 3 | **Status:** Done

### US-8.2 — Automatic KB freshness updates
**As a** Service Desk Manager, **I want** KB updates triggered automatically by relevant IT changes, **so that** content doesn't go stale the way it did after the VPN tool change.
- **Given** an in-scope ServiceNow change record, **when** it is logged, **then** a KB update is completed within 5 business days.
- **Points:** 5 | **Status:** Done — standing SLA established after a real drift incident

### US-8.3 — Catch cost-per-query drift early
**As a** PM, **I want** monthly cost-per-query monitoring with a deviation trigger, **so that** cost overruns are caught before they become a budget surprise.
- **Given** actual cost per query 10%+ above forecast, **when** the monthly review runs, **then** an optimization review is triggered automatically.
- **Points:** 3 | **Status:** Done — drift of ~20% caught and corrected within month one

---

## Epics E9–E11 (Phase 2 — Deferred, Not Yet Authored as Full Stories)

These remain at epic/backlog level only, pending their own readiness work:

- **E9 — Multilingual & Channel Expansion:** Requires a localization and voice-channel feasibility pass before stories can be written.
- **E10 — Domain Expansion (HR/Finance):** Requires those teams' own data readiness audits (parallel to Stage 2 of this project) before stories can be written.
- **E11 — Proactive Assistance:** Requires a dedicated Responsible AI review of the proactive-suggestion use case before any story is authored — explicitly parked, not just deprioritized.

## 4. Story Point Summary

| Epic | Total Points (Delivered) |
|---|---|
| E1 — Knowledge Ingestion & Retrieval | 23 |
| E2 — Hybrid Search & Accuracy | 34 |
| E3 — Trust, Safety & Guardrails | 29 |
| E4 — Conversation Experience | 8 |
| E5 — Channel Integration | 21 |
| E6 — Evaluation & Responsible AI | 18 |
| E7 — Rollout & Change Management | 11 |
| E8 — Governance & Monitoring | 11 |
| **Total delivered (Phase 1)** | **155** |

---
*Prepared by Prachi Sharma — AI Project Manager · Technical PM · Gen AI Delivery Lead*
