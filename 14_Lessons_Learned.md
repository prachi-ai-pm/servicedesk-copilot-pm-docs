# Lessons Learned

**Project Name:** ServiceDesk Copilot — AI-Assisted Tier-1 IT Support
**Document Owner:** Prachi Sharma, AI/ML Project Manager
**Status:** Final
**Version:** 1.0
**Date:** [Insert Closure Date]

---

## 1. Purpose

This register captures what worked, what didn't, and what should change for the next AI/ML delivery — feeding directly into the Phase 2 roadmap and into how future similar projects should be scoped and governed. It is organized by theme rather than strictly by stage, since several lessons span multiple stages.

## 2. What Went Well

| Theme | Lesson | Evidence |
|---|---|---|
| Scope discipline | Converting an open-ended "AI helpdesk" ambition into a bounded MVP via an effort-vs-impact exercise prevented scope creep from stalling the entire programme before it started | IT Tier-1-only scope approved; HR/Finance phased to a later release |
| Measurable quality bar | Building a ground-truth test set before a model existed turned "accuracy" from a subjective claim into a measurable one | 150-question labeled test set; used to validate every evaluation cycle |
| Early risk surfacing | Treating the RAID log as a live decision tool (not a compliance artifact) caught and resolved risks before they became launch blockers | Hybrid-search gap, key-engineer unavailability, and the data-readiness slip were all surfaced and resolved before they affected the launch date materially |
| Holding the line under pressure | Refusing to compress or skip the Responsible AI / bias review despite sponsor pressure protected both the launch and the broader case for AI adoption | Sponsor accepted a short, scoped delay instead of launching without the review |
| Correct diagnosis before reacting | Treating low pilot-week adoption as a hypothesis to test (awareness gap vs. capability gap) rather than an assumed product failure avoided an unnecessary rollback or redesign | Quick survey correctly diagnosed an awareness gap; fixed with a guided walkthrough, not a product change |
| Structural fixes over one-time patches | Converting recurring problems (KB staleness, cost drift) into standing mechanisms (SLA, monthly monitoring) rather than one-off fixes prevents recurrence | 5-business-day KB freshness SLA; monthly cost-per-query review with a 10% trigger |
| Documented architecture rationale | Logging every architecture decision and its rationale in a single ADR meant the reasoning survived scrutiny and would hold up in a later audit | Vendor lock-in comparison and fine-tuning rejection both fully traceable |

## 3. What Could Have Gone Better

| Theme | Lesson | Evidence | Recommendation for Next Project |
|---|---|---|---|
| Discovery-stage data assumptions | Discovery interviews underestimated how bad the knowledge base actually was; the formal audit found worse fragmentation than anecdotal interviews suggested | 18% (ServiceNow) and 35% (SharePoint) outdated/duplicate content found only after a formal audit, adding ~3 weeks | Commission the formal data readiness audit *in parallel with* discovery interviews, not after charter approval, for any future RAG project — don't wait for a sequential Stage 2 |
| Stakeholder alignment on success | Three stakeholders held different private definitions of "success" well into Stage 2, which could have caused a launch-time dispute if it had surfaced later | Service Desk Manager wanted volume, VP wanted cost, end-user reps wanted satisfaction | Run the success-metric weighting exercise during the charter stage, not after requirements are underway — alignment gaps are cheaper to close earlier |
| Initial retrieval architecture assumption | Assuming pure vector search would be sufficient cost a sprint when it underperformed on short, informal queries | Hybrid search added after a mid-sprint finding, extending Stage 4 by one sprint | For future RAG builds, default to hybrid (keyword + vector) search from sprint one rather than treating it as an upgrade path — the informal-query weakness of vector-only search is a known, predictable failure mode |
| Late-surfaced vendor risk | Vendor lock-in wasn't raised by Procurement until the team had already informally settled on a platform | Required pausing an informal decision to run a documented 3-option comparison | Involve Procurement in the architecture evaluation from the start of Stage 3, not after a default has already formed |
| UX validation timing | Tone and "robotic" feedback only surfaced in UAT, late enough that fixing it required a short delay right before launch | UAT satisfaction was 3.4/5 initially (target ≥ 4.0), requiring a tone-revision pass | Run a lightweight conversational tone review with a small user sample mid-build (e.g., end of Stage 4), not only at formal UAT |
| Hallucination root cause was content-specific, not systemic | The 8% hallucination rate traced to a narrow, specific cause (password-policy article chunking) but wasn't caught until formal evaluation | Required a dedicated root-cause session post-evaluation | Run targeted chunking-quality spot checks on the highest-risk content categories (e.g., security/password policy) during Stage 4, before the formal Stage 5 evaluation |
| Cost modeling didn't anticipate context-window growth | The original cost-per-query forecast didn't account for context windows growing longer than expected in real usage | ~20% cost overshoot in month one | Build a cost-per-query sensitivity range (not a single point forecast) into future business cases, explicitly modeling context-window growth as a variable |

## 4. Lessons by Project Phase

| Phase | Key Lesson |
|---|---|
| Discovery & Business Case | Validate the data, not just the ambition, before sizing the MVP |
| Requirements & Data Readiness | Make "success" and "accuracy" measurable before any model exists |
| Solution Design & Architecture | Default to the safer, more auditable architecture choice (RAG over fine-tuning on PII-bearing data) even when it's slower to start |
| Build & Delivery Coordination | Treat the RAID log as an active steering tool; protect scope through formal change control, not informal yes/no decisions |
| Evaluation & Responsible AI Review | Never relax a quality or ethics threshold to protect a date — the cost of a confidently wrong AI system is higher than a short delay |
| Deployment & Change Management | Diagnose adoption problems before reacting to them; address workforce trust concerns directly and early |
| Post-Launch Governance | Convert every recurring risk into a named, owned, standing mechanism — not a one-time fix |

## 5. Recommendations for Future AI/ML Projects

1. **Run the data readiness audit in parallel with discovery**, not after charter approval, to avoid a downstream schedule surprise.
2. **Default to hybrid retrieval (keyword + vector) from the start** for any RAG-based system serving informal, short-form queries.
3. **Resolve the success-metric weighting exercise at the charter stage**, before requirements work begins.
4. **Build a cost-per-query sensitivity range into the business case**, not a single-point forecast, accounting for context-window variability.
5. **Involve Procurement in architecture evaluation from day one** of the design stage to avoid a late-stage vendor-lock-in surprise.
6. **Treat the Responsible AI / bias review as non-negotiable** in the stage-gate structure for any future AI system — this is the single highest-leverage governance decision in the whole project.
7. **Build a lightweight mid-build UX/tone checkpoint** rather than waiting until formal UAT to catch usability issues.
8. **Gate any future domain expansion (HR, Finance) on that domain's own data-readiness audit**, mirroring the rigor applied to the original IT Tier-1 scope — don't assume reusability of the Stage 2 process's conclusions for a different content domain.

## 6. Disposition

This Lessons Learned register has been incorporated into:
- The **Phase 2 Roadmap** (Product Backlog, Epics E9–E11), where domain-expansion gating (Recommendation 8) is explicitly reflected
- The **Risk Register** (RR20), which remains open by design pending the data-readiness gating described above
- Internal practice guidance for future AI/ML PM engagements led by Prachi Sharma

---
*Prepared by Prachi Sharma — AI Project Manager · Technical PM · Gen AI Delivery Lead*
