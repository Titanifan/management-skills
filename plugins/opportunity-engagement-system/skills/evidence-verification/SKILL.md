---
name: evidence-verification
description: Verify decision-critical factual claims by decomposing them into atomic propositions, prioritising material claims, checking current and source-fit evidence, seeking contradictory evidence, tracking dates and versions, and calibrating confidence. Use when the user asks to verify, fact-check, confirm, audit, validate, or perform due diligence on claims; when a research, policy, investment, grant, commercial, or strategic recommendation depends on uncertain factual premises; or when another Skill hands off material claims for verification. Do not use for purely normative judgements, creative work, or ordinary explanations that do not depend on disputed or consequential facts.
---

# Evidence Verification

## Core purpose

Own **VERIFY**.

Determine what the available evidence supports, what it does not support, and how strongly a decision-critical factual claim can be stated.

Do not own strategic selection, field relationship development, or resource commitment. Evidence Verification may report that a premise is materially weakened, contradicted, or unresolved, but the calling Skill or user owns the resulting decision.

The governing question is:

**What can we responsibly claim, as of the relevant date, from the strongest available evidence?**

Do not treat a second model-generated answer as verification. Verification requires external or supplied evidence appropriate to the claim.

## Operating principles

1. **Verify claims, not narratives.** Break consequential prose into atomic factual propositions before searching.
2. **Prioritise decision-critical claims.** Verify first the claims most capable of changing a recommendation, eligibility decision, valuation, deadline, resource allocation, governance position, or factual conclusion.
3. **Match source to claim.** Prefer the source that is authoritative for the specific proposition, not a generic hierarchy detached from the question.
4. **Prefer primary evidence where it is fit for purpose.** Use official registers, filings, contracts, legislation, regulator notices, original studies, company announcements, or direct records where these actually establish the claim.
5. **Do not confuse first-party with neutral.** When the source has a material incentive to frame the claim favourably, seek independent corroboration when practical.
6. **Search for contradiction.** Do not verify only by finding supporting material. Look for evidence that would narrow, qualify, or falsify the claim.
7. **Check time, version, entity, and scope.** Many apparent contradictions are stale evidence, different definitions, changed status, wrong jurisdictions, or similarly named entities.
8. **Distinguish absence from falsity.** Failure to find evidence usually means unsupported or currently unknowable, not false.
9. **Separate evidence from inference.** Mark what is directly documented, what is inferred, and what remains judgement.
10. **Calibrate language to evidence.** Narrow the wording before inflating confidence.
11. **Preserve provenance.** Record enough source, date, version, and retrieval context for another reviewer to reproduce the factual check.
12. **Stop when marginal search value is low.** Do not continue searching after decision-critical claims are resolved to the level needed for the decision unless the user requests exhaustive due diligence.

## Inputs

Accept any of the following:

- one factual claim;
- a set of claims;
- a paragraph, memo, recommendation, investment thesis, policy analysis, grant argument, manuscript section, or due-diligence note from which claims must be extracted;
- a handoff from another Skill containing decision-critical claims;
- supplied files, links, records, or connected-source evidence that the user wants checked.

When the input is a long analysis, do not verify every sentence mechanically. Extract and rank the claims that could materially change the conclusion.

## Verification workflow

Follow this sequence unless the user requests a quick check.

### 1. Define the verification target

Rewrite the target as one or more atomic claims. Preserve:

- entity;
- action or state;
- quantity where relevant;
- date or effective period;
- jurisdiction or market;
- modality such as has, may, intends, expects, approved, licensed, contracted, or completed;
- material qualifier such as exclusive, second, binding, commercial, regulatory, peer-reviewed, or audited.

Do not silently strengthen the original wording.

### 2. Rank decision criticality

Classify each claim:

- **Critical:** if wrong, the recommendation or key conclusion could materially change.
- **Material:** affects confidence, scope, timing, valuation, feasibility, or interpretation but is unlikely to reverse the decision alone.
- **Contextual:** useful background with little decision effect.

Verify Critical claims first, then Material claims. Sample Contextual claims unless the user requests an exhaustive audit.

### 3. Set the evidence requirement

Before searching, state internally what kind of evidence could establish or refute the claim.

Load `references/source-hierarchy.md` when source authority, source conflict, domain-specific evidence, or primary-source selection is non-trivial.

Examples:

- licence or regulatory status -> regulator, official register, or issuing authority;
- listed-company financial fact -> audited filing, exchange filing, or company report tied to the reporting period;
- contract or customer relationship -> executed agreement where available, formal filing, named counterparty confirmation, or carefully qualified company disclosure;
- policy deadline or eligibility -> official program page, legislation, guidelines, or issuing body;
- scientific claim -> original study for a specific result; systematic review, meta-analysis, or guideline for a general body-of-evidence claim;
- current organisational role -> authoritative current organisation page or direct official record.

### 4. Retrieve the strongest available evidence

Use the user's supplied sources first when the task is explicitly based on them. Use current public sources when the claim requires external verification and browsing is available.

Use connected private sources only when the claim concerns the user's authorised private data or the user explicitly requests that source. Do not inspect private sources merely because they might be convenient.

Do not use memory or prior conversation as evidentiary proof. Memory may identify what to verify, but evidence must come from supplied, connected, or externally retrievable sources.

### 5. Check freshness, identity, version, and scope

For each material source, check:

- publication or issue date;
- effective date where different;
- latest known version or amendment;
- whether the evidence is contemporaneous with the claim;
- exact legal or organisational entity;
- jurisdiction;
- whether the source supports the full wording or only a narrower proposition.

For time-sensitive claims, search specifically for superseding evidence.

### 6. Seek disconfirming evidence

Run at least one meaningful contradiction check for every Critical claim unless the evidence is mechanically decisive, such as a definitive official register entry.

Look for:

- later reversals or amendments;
- counterparty statements;
- regulator actions;
- filings inconsistent with promotional language;
- changed dates or eligibility rules;
- definitional differences;
- methodological limitations;
- evidence that the claim is true only under a narrower scope.

Do not treat disagreement between two sources as a tie. Diagnose why they differ.

### 7. Classify the claim

Use exactly one primary status:

- **Verified:** strong, source-fit evidence supports the material wording and no material contradiction remains.
- **Partially verified:** an important core is supported, but scope, date, quantity, terminology, modality, or another material qualifier needs narrowing.
- **Unsupported:** adequate evidence for the claim was not found. This does not by itself establish falsity.
- **Contradicted:** stronger or more current evidence materially conflicts with the claim.
- **Currently unknowable:** the claim depends on non-public, unavailable, ambiguous, or not-yet-observable evidence that cannot presently be resolved.

Load `references/claim-status-confidence.md` when classification or confidence is contested or consequential.

### 8. Calibrate confidence separately from status

Assign **High / Medium / Low** confidence based on source fit, recency, specificity, independence where relevant, consistency, and completeness.

Do not translate confidence into fake probabilities unless a domain provides a defensible statistical basis.

A claim may be:

- Verified with Medium confidence because the primary source is incomplete;
- Unsupported with High confidence because exhaustive authoritative records were checked;
- Currently unknowable with High confidence because the decisive evidence is explicitly non-public.

### 9. Correct the wording

Rewrite the claim at the strongest level the evidence supports.

Prefer narrowing over binary dismissal when appropriate.

Examples:

- from "has secured a second OEM licence" to "announced a second OEM relationship, but the available evidence does not establish that it is a licence";
- from "the program closes on 30 September" to "the current official guidelines list 30 September 2026 as the closing date";
- from "research proves" to "one study reports" when the broader evidence base is not established.

### 10. Assess decision impact

State whether the verification result has:

- **No material impact**;
- **Minor qualification**;
- **Material impact**;
- **Premise-invalidating impact**.

Do not make the downstream strategic or resource decision unless the user explicitly asks for it and the appropriate Skill is also invoked.

### 11. Stop or escalate

Stop when the decision-critical claims have sufficient evidence for the decision at hand.

Escalate or leave unresolved when:

- only non-public evidence could resolve the claim;
- source conflict cannot be reconciled;
- legal, technical, or scientific expertise beyond the available evidence is required;
- the claim depends on a future event;
- the remaining uncertainty is field evidence rather than documentary evidence.

## Tool and source discipline

Use the best available evidence channel for the claim.

- **Supplied files:** treat them as the requested basis when the user asks to verify within those materials. Do not silently replace them with outside knowledge.
- **Public web:** use for current public facts, primary-source retrieval, official notices, filings, registers, and independent corroboration.
- **Connected sources:** use only when relevant to the user's authorised private evidence, such as their email or calendar records.
- **Code or scripts:** use only when deterministic parsing, comparison, arithmetic, tabulation, or large-scale claim extraction materially improves reliability.

When outside evidence is used to expand or challenge supplied material, clearly distinguish source-derived facts from external verification.

## Source-conflict protocol

When credible sources conflict, do not average them or pick the more convenient one.

Check in this order:

1. same entity?
2. same definition?
3. same date or effective period?
4. same jurisdiction?
5. same version?
6. same evidentiary question?
7. one source supersedes the other?
8. first-party incentive or methodological weakness?

If conflict remains, preserve it in the output and lower confidence.

## Output modes

### Quick verification

Use for one or two claims:

- verdict;
- strongest evidence;
- material contradiction or limitation;
- corrected wording;
- confidence;
- decision impact.

### Verification ledger

Use for multiple claims or due diligence. Default columns:

| Claim | Criticality | Status | Best evidence | Contradiction / limitation | Confidence | Corrected wording | Decision impact |
|---|---|---|---|---|---|---|---|

Keep the ledger concise. Cite each material factual determination using the citation system available in the environment.

### Deep audit

Use when the user requests exhaustive verification, due diligence, or source auditing. Add:

- scope and as-of date;
- source coverage and exclusions;
- unresolved source conflicts;
- version and jurisdiction notes;
- missing evidence;
- residual verification risk;
- claims that should be rechecked later.

## Boundary with other Skills

Evidence Verification is horizontal. It verifies premises for other Skills but does not absorb their decisions.

### Strategic Opportunity

Verify claims that materially affect strategic attractiveness, platform fit, feasibility, timing, moat, practice impact, venture architecture, or selection-level hard gates.

Return the verification result and decision-impact flag. If a strategic premise changes materially, recommend **re-screen** rather than changing the portfolio disposition inside Evidence Verification.

### External Engagement

Verify documentary claims about organisations, current roles, policy processes, public commitments, previous relationships, counterpart statements, or other field facts.

When the remaining evidence requires a conversation, access, sponsor confirmation, willingness, reciprocity, or other external behaviour rather than document retrieval, return the unresolved field question to External Engagement.

### Adaptive Commitment

Verify factual premises supporting resource levels, milestones, stage readiness, implementation progress, costs, deadlines, or outcome claims.

If new evidence changes the commitment premise, return a material-impact flag for Adaptive Commitment review. Do not independently change mode, resource cap, milestone, or persistence rule.

Load `references/handoff-contract.md` for structured inter-Skill handoffs.

## Evidence versioning

When used inside an orchestrated workflow:

- preserve `opportunity_id` where provided;
- preserve the caller's `evidence_version`;
- increment the evidence version only when material new evidence is added;
- identify which claim changed and why;
- do not rewrite the shared case history;
- return evidence to the caller or Orchestrator for state transition.

## Safety and restraint

Do not imply certainty that the evidence does not support.

Do not fabricate inaccessible records, private communications, unpublished contracts, proprietary datasets, regulatory decisions, or citations.

Do not treat promotional language, analyst consensus, media repetition, or search-result frequency as independent confirmation.

Do not infer a person's intent, private belief, health, criminality, political affiliation, or other sensitive personal attribute from weak evidence.

For high-stakes legal, medical, financial, safety, or regulatory matters, state the evidence limits and rely on authoritative domain sources where available.

## Reference loading guide

- Use `references/source-hierarchy.md` for claim-specific source selection, domain source patterns, source conflicts, and corroboration rules.
- Use `references/claim-status-confidence.md` for classification thresholds, confidence calibration, absence-of-evidence rules, and wording discipline.
- Use `references/handoff-contract.md` for structured exchange with Strategic Opportunity, External Engagement, Adaptive Commitment, or an Orchestrator.
- Use `references/verification-patterns.md` for compact examples across research, policy, investment, and organisational claims.
