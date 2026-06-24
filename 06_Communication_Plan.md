# Communication Plan

**Project Name:** ServiceDesk Copilot — AI-Assisted Tier-1 IT Support
**Document Owner:** Prachi Sharma, AI/ML Project Manager
**Status:** Approved
**Version:** 1.0
**Date:** [Insert Approval Date]

---

## 1. Purpose

This plan defines how project information is communicated to stakeholders throughout delivery and rollout — including governance reporting during build, and the change-management communications used to land the launch without triggering avoidable resistance or confusion. A technically sound chatbot that nobody uses, or that employees actively distrust, is a failed project just a quieter one; this plan treats adoption and trust as things to be actively managed, not assumed.

## 2. Communication Objectives

- Keep the sponsor and governance stakeholders (Security, Compliance, Finance) informed early enough to act on risk, not just aware of outcomes after the fact
- Keep the build team aligned on sprint goals, technical findings, and scope decisions
- Frame the tool to the workforce as an addition to support, not a threat to service desk jobs
- Give every end user a clear, repeated path to reach a human at any time
- Surface adoption and trust issues fast enough to correct them within the pilot window, not after full rollout

## 3. Internal Project Communications (Discovery → Build → Evaluation)

| Communication | Audience | Purpose | Frequency | Channel | Owner |
|---|---|---|---|---|---|
| Discovery interviews | IT Ops Director, Service Desk Manager, InfoSec, Finance | Size the problem, surface constraints | One-time (Stage 1) | In-person/video interview | PM |
| Sponsor approval gate briefing | VP, IT Operations | Charter & business case approval | One-time (Stage 1) | Formal presentation | PM |
| Requirements workshops | Data Science Lead, Engineering | Translate objectives into requirements | One-time (Stage 2) | Workshop | PM |
| Architecture decision briefing | Security, Procurement, Solution Architect | Build-vs-host-vs-buy decision and sign-off | One-time (Stage 3) | Workshop + ADR document | PM |
| Sprint planning & daily standups | Build team (ML/data engineers, backend engineer, UX designer, QA) | Coordinate sprint execution | Daily / per 2-week sprint | Standup, sprint planning session | PM |
| RAID log review | Sponsor | Surface and act on risk early | Weekly | Document review meeting | PM |
| Sprint review / demo | Sponsor, Service Desk Manager | Visibility into progress and technical findings | Per sprint (2-week cycle) | Demo session | PM |
| Change-request briefings | Sponsor | Decision on scope changes (e.g., multilingual request) | As triggered | Document + meeting | PM |
| Evaluation results review | Data Science Lead, Compliance, Sponsor | Hallucination rate, accuracy, RAI sign-off | At Stage 5 gate | Formal review + Evaluation Report | PM |
| UAT debrief | Service Desk agents, end-user volunteers | Gather usability feedback | End of UAT period (2 weeks) | Survey + debrief session | PM / QA |

## 4. External / Workforce Communications (Launch & Rollout)

| Audience | Channel | Message | Timing |
|---|---|---|---|
| All employees | Company email | Introducing a faster way to get IT help — framed as an addition, not a replacement | 2 weeks before pilot |
| Pilot department managers | Manager toolkit + briefing | What to expect, how to escalate concerns, FAQ for their teams | 1 week before pilot |
| Pilot department employees | Teams pop-up + guided walkthrough | How to use it, and how to reach a human at any time | Day of pilot launch |
| All users | Short survey | Feedback on the experience to inform Phase 2 and 3 | 2 weeks post-launch |
| Pilot department staff representatives / union | Direct briefing | Address job-security concerns directly and honestly | Prior to pilot communications going company-wide |

## 5. Key Messaging Principles

- **Augmentation, not replacement.** Every workforce-facing message frames the bot as faster help for employees, not a signal that service desk jobs are at risk — this was raised directly by one pilot department's staff representatives and addressed head-on rather than deflected.
- **The human path is always visible.** Every touchpoint (Teams walkthrough, FAQ, manager toolkit) repeats how to reach a human agent at any time — this is a non-negotiable design and communications principle, not just a technical fallback.
- **Bad news goes up immediately, not on a schedule.** Technical findings, slippage, and cost drift are raised to the sponsor as they're discovered (e.g., the data-readiness slip, the hallucination-rate miss, the post-launch cost creep) rather than held for a scheduled review — this is the actual mechanism the RAID log review and weekly cadence exist to support.

## 6. Post-Launch Governance Communications

| Communication | Audience | Frequency | Owner |
|---|---|---|---|
| Ticket deflection rate report | Service Desk Manager | Weekly | Service Desk Manager |
| Hallucination / escalation-needed rate report | Data Science Lead, PM | Weekly | Data Science Lead |
| Cost-per-query report | PM, Finance | Monthly | PM + Finance |
| User CSAT survey results | PM | Monthly | PM |
| KB freshness / change-trigger notifications | Service Desk Manager | Triggered by relevant IT change record (5-business-day SLA) | Service Desk Manager |
| Lessons-learned review | Sponsor, full project team | One-time, post-90-day mark | PM |

## 7. Escalation Path for Communication Issues

If a stakeholder concern is not resolved through standard cadence (e.g., the staff-representative job-security concern, or the pilot-week adoption gap diagnosed mid-rollout), the PM convenes an ad-hoc session with the relevant stakeholder group within 48 hours rather than waiting for the next scheduled touchpoint.

---
*Prepared by Prachi Sharma — AI Project Manager · Technical PM · Gen AI Delivery Lead*
