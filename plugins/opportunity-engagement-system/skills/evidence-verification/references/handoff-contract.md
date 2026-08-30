# Inter-Skill Handoff Contract

## Purpose

Use this structure when Evidence Verification receives claims from, or returns findings to, another decision Skill or an Orchestrator.

Evidence Verification owns the factual audit. The caller retains decision authority.

## Intake record

Accept when available:

1. `caller`: Strategic Opportunity, External Engagement, Adaptive Commitment, Orchestrator, or standalone user.
2. `opportunity_id`: stable shared identifier when part of an opportunity workflow.
3. `evidence_version`: current evidence version.
4. `as_of_date`: date at which the claim should be evaluated.
5. `claim_id`: stable identifier for each material claim.
6. `claim_text`: exact proposition to verify.
7. `criticality`: Critical, Material, or Contextual.
8. `decision_context`: what decision the claim affects.
9. `decision_dependency`: why the claim could change the decision.
10. `known_sources`: supplied or already retrieved evidence.
11. `source_constraints`: required or prohibited evidence channels.
12. `jurisdiction_or_market`: where relevant.
13. `known_contradictions`: evidence already in tension with the claim.
14. `verification_question`: the exact evidentiary issue to resolve.

If the caller sends a narrative rather than atomic claims, decompose it before verification and return the extracted Critical claims.

## Return record

Return:

1. `claim_id`;
2. `original_claim`;
3. `corrected_claim`;
4. `status`: Verified, Partially verified, Unsupported, Contradicted, or Currently unknowable;
5. `confidence`: High, Medium, or Low;
6. `best_evidence`: source, date, version, and what it establishes;
7. `contradictory_or_limiting_evidence`;
8. `freshness_note`;
9. `remaining_uncertainty`;
10. `decision_impact`: No material impact, Minor qualification, Material impact, or Premise-invalidating impact;
11. `material_new_evidence`: yes or no;
12. `recommended_return_route`;
13. `provenance` sufficient for reproducibility.

Increment `evidence_version` only when material new evidence is added.

## Return routes

### To Strategic Opportunity

Recommend `re-screen` when verification materially changes:

- a strategic hard gate;
- feasibility;
- timing;
- role or ownership potential;
- expected compounding assets;
- practice-impact or venture architecture premise;
- another selection-critical fact.

Do not set the new portfolio disposition.

### To External Engagement

Return an unresolved field question when documentary verification cannot establish:

- actual problem significance;
- sponsor willingness;
- access;
- reciprocity;
- role acceptance;
- partner commitment;
- attribution;
- non-public relationship facts.

Do not invent field evidence.

### To Adaptive Commitment

Recommend commitment review when verification materially changes:

- current cost or resource assumption;
- milestone result;
- stage readiness;
- deadline;
- implementation progress;
- evidence standard;
- another commitment premise.

Do not change the resource cap, mode, stage, or persistence period inside Evidence Verification.

### To Orchestrator

Return the factual record and decision-impact flag. The Orchestrator owns state transition.

Do not bounce between Skills merely because a claim is uncertain. Route according to the type of missing evidence.
