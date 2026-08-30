# Shared Opportunity Ledger

Maintain one authoritative state record per distinct opportunity. The ledger is not a CRM, source repository, contact database, or substitute for meeting notes, contracts, or agreements.

## Canonical schema

```yaml
opportunity_id: stable-human-readable-id
name: short-name
state: scan|pre-screen|formation|re-screen|conversion|commitment|review|monitor|exit
mode: null|preliminary-screen|formation|re-screen|conversion|commitment|review
state_confidence: low|medium|high
evidence_version: 1
last_evidence_event: dated-summary

documented_evidence: []
inferences: []
missing_evidence: []

candidate_problem: null
practice_decision: null
research_puzzle: null
problem_owner: null
sponsor: null
access:
  problem: unknown
  decision: unknown
  data: unknown
  implementation: unknown

strategic_disposition: null
platform_classification: null
selection_hard_gates: []
potential_strategic_ownership: null

engagement_position: null
engagement_mode: null
ownership_and_attribution: null
ownership_access_position: null
reciprocal_commitment: null

commitment_mode: null
commitment_stage: null
resource_boundary: null
responsibility_boundary: null
milestone: null
review_condition: null

material_claims_needing_verification: []
verification_result: null

principal_uncertainty_type: selection|field_relationship|claim_verification|commitment
principal_uncertainty: null
governance_boundary: null
next_evidence_action: null
stop_or_downgrade_rule: null
transition_log: []
updated_at: ISO-8601
```

## Record identity

- Create one stable human-readable `opportunity_id` per distinct opportunity.
- Reuse the same record as state changes.
- Split a record only when one relationship produces genuinely distinct problems, owners, governance, or resource decisions. Link the records in a transition note.
- Do not merge opportunities merely because they involve the same organisation.

## Evidence versioning

- Start `evidence_version` at `1` when the first material evidence record is created.
- Increase it by exactly one when material evidence is added, corrected, or superseded.
- Do not increment for formatting, restatement, repeated discussion, or a new interpretation of unchanged evidence.
- Every substantive judgement must state which evidence version it used.

## Evidence fields

- `documented_evidence`: source-grounded observations with date, source, owner or author, and confidence where available.
- `inferences`: interpretations, hypotheses, and provisional mappings.
- `missing_evidence`: gaps capable of changing state, disposition, mode, or resource decision.
- `material_claims_needing_verification`: only factual claims whose truth could change recommendation or routing.
- `verification_result`: latest material claim status, source quality, freshness, contradiction, confidence, corrected wording, provenance, and decision impact.

Preserve contradictory evidence as separate entries. Never convert an inference into evidence because it was remembered or repeated.

## State history

Keep `transition_log` append-only. For each material transition record:

```yaml
- from_state: previous-state
  to_state: new-state
  date: ISO-8601
  evidence_version: integer
  transition_evidence: concise-source-grounded-summary
  governing_uncertainty_type: selection|field_relationship|claim_verification|commitment
  decision: concise-user-visible-decision
  prior_specialist_verdict: null
  new_specialist_verdict_or_correction: null
  provenance: source-and-confidence-summary
  next_evidence_action: null
  stop_rule: null
```

A material no-transition review may be logged when it confirms or weakens the current state. Never rewrite earlier transitions to make history appear linear.

## Control fields

- `principal_uncertainty_type`: the layer currently blocking valid downstream action.
- `principal_uncertainty`: the one unknown most likely to change the immediate decision.
- `governance_boundary`: ethical, institutional, contractual, confidentiality, conflict, workload, attribution, and approval constraints.
- `next_evidence_action`: the smallest justified action capable of resolving the governing uncertainty.
- `stop_or_downgrade_rule`: the condition that prevents further active work or forces monitoring, redesign, or exit.
