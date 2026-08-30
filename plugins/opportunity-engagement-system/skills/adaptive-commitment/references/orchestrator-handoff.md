# Orchestrator Handoff

Use this record when Adaptive Commitment receives a selected opportunity from the Opportunity & Engagement Orchestrator and when it returns execution learning for the Agent to route. The shared Opportunity Ledger remains authoritative; do not create a competing case history inside this Skill.

## Intake record

Record the following fields before designing a commitment:

1. `opportunity_id`: stable identifier shared across all Skills.
2. `opportunity_name`: concise human-readable label.
3. `from_state`: the Agent state that produced the handoff.
4. `current_state`: normally `commitment` once the handoff is accepted.
5. `evidence_version`: integer identifying the evidence set used for this decision.
6. `strategic_disposition`: the latest Strategic Opportunity disposition and its confidence.
7. `engagement_mode`: the last External Engagement mode, if one was used.
8. `engagement_evidence`: documented signals for problem owner, decision authority, sponsor, access, reciprocity, role, ownership, attribution, and governance.
9. `ownership_access_position`: what the user can own, access, influence, and credibly deliver.
10. `reciprocal_commitment`: what each relevant counterpart has actually committed, distinguished from expressed interest.
11. `principal_uncertainty`: the one unknown most likely to change the commitment. Classify it before accepting the handoff: selection uncertainty -> return to Strategic Opportunity; field/relationship uncertainty -> return to External Engagement; commitment uncertainty -> accept into Adaptive Commitment. Accept a mixed case only when the commitment decision remains materially actionable without first resolving an upstream hard gate.
12. `governance_boundary`: ethical, institutional, contractual, conflict, confidentiality, workload, and approval constraints.
13. `concrete_resource_decision`: the time, money, attention, role, or governance choice requiring a decision now.
14. `documented_evidence`: source-linked observations or records.
15. `inferences`: interpretations not yet directly documented.
16. `missing_evidence`: decisive gaps and how they could be resolved.
17. `provenance`: source, date, author or owner, and confidence for material claims.
18. `stop_rule`: the condition that prevents further commitment or returns the opportunity to an earlier state.

Reject the intake as not ready when portfolio entry, relationship readiness, or a concrete resource decision is absent. Name the governing uncertainty and recommend the smallest appropriate return route.

## Review record

Return the following fields after the milestone, review date, or material evidence event:

1. `opportunity_id`: the same stable identifier used at intake.
2. `from_state`: normally `review`, or `commitment` when review is performed inline.
3. `recommended_state`: one of `commitment`, `re-screen`, `formation`, `conversion`, `monitor`, or `exit`.
4. `evidence_version`: the incremented version when material evidence was added; otherwise retain the current version.
5. `transition_evidence`: the specific evidence that warrants the recommended state change or continued commitment.
6. `milestone_result`: met, partly met, missed, invalidated, or not assessable, with the evidence standard used.
7. `execution_fidelity`: whether the agreed resource floor, cap, first action, role, and persistence period were followed.
8. `belief_change`: what changed in the opportunity, relationship, or commitment thesis and why.
9. `resource_use`: actual time, money, attention, and governance burden against the contract.
10. `residual_assets`: theory, data, method, relationship, distribution, capability, or insight retained.
11. `documented_evidence`: new source-linked observations or records.
12. `inferences`: interpretations introduced by the review.
13. `missing_evidence`: remaining decisive gaps.
14. `provenance`: source, date, author or owner, and confidence for each material update.
15. `next_evidence_action`: the smallest action that could resolve the governing uncertainty in the recommended state.
16. `stop_rule`: the next boundary for exit, downgrade, or return.

Use these routing meanings:

- `commitment`: the thesis remains adequate and another bounded commitment is justified.
- `re-screen`: new evidence could change strategic attractiveness, a hard gate, or portfolio disposition.
- `formation`: the problem, actor, demand, or practice context requires renewed field learning.
- `conversion`: strategic potential is credible, but sponsor, access, role, reciprocity, ownership, attribution, or governance requires qualification.
- `monitor`: no active commitment is justified, but a named external trigger could warrant reopening.
- `exit`: a stop rule or hard gate has been met and no proportionate redesign is justified.

The review record is a routing recommendation. The Agent decides and logs the state transition in the shared Opportunity Ledger.
