# Opportunity & Engagement System v1.1 — Original 12 Routing Regression Cases

**Test date:** 2026-08-30
**System under test:** Opportunity & Engagement System v1.1.0
**Architecture:** 9-state Orchestrator + Strategic Opportunity + External Engagement + Evidence Verification + Adaptive Commitment
**Test type:** Deterministic routing simulation against the currently installed v1.1 Skill instructions and references. This is not a stochastic multi-run UI Preview test and does not perform the real-world scan or documentary verification requested inside generic fixtures.
**Mutation boundary:** Read-only. No Plugin files were changed.

## Executive result

- **Passed:** 12/12
- **Failed:** 0/12
- **Critical regressions:** 0
- **Major regressions:** 0
- **Minor regressions:** 0
- **Naming/architecture clarifications:** 3 case-level differences, all informational and non-regressive
- **Original-fixture integrity:** The SHA-256 of the ZIP's `evals/routing-cases.json` exactly matches the SHA-256 of v1.1's preserved `references/original-routing-cases.json`: `168D6E4C3DD178348E113ECE47FED931DB618EF9B995C273153FEA9D206A5290`.

The current v1.1 preserves the governing route and safety invariants of all original cases. The only differences are explicit terminology introduced by the merged architecture: `agent-native` is now expressed as Orchestrator + current evidence tools, and documentary verification is explicitly a VERIFY sidecar rather than a lifecycle mode or tenth state.

## Severity scale

- **None:** No meaningful difference from the expected route or invariant.
- **Informational:** Terminology or architecture is more explicit, with no behavioural change.
- **Minor:** Output shape differs, but route and safety behaviour remain correct.
- **Major:** Wrong capability or transition, but without an immediate critical safety failure.
- **Critical:** Premature commitment/proposal, false partnership/ownership, stale-fact reliance, hidden transition, downstream override, all-Skill invocation, or VERIFY taking over another decision layer.

## Case 1 — `wa-agency-funding-scan`

### Original case wording

> Scan current Western Australian government agencies and funding programmes relevant to my academic-practice arena, then tell me what deserves attention.

### Original expected outcome

- State: `scan`
- Primary Skill: `agent-native`
- Mode: `scan`
- Expected next state: `pre-screen`
- Required output: `state`, `documented_evidence`, `bounded_candidate_list`, `next_evidence_action`, `stop_rule`
- Prohibited: create a Discovery Skill; deep-dive every candidate; run all three Skills

### Actual outcome under v1.1

- State: `scan` — high confidence.
- Governing uncertainty: current-evidence discovery before a discrete opportunity has been selected.
- Minimum capability: Orchestrator + current evidence tools; no specialist Skill is needed for the scan itself.
- Evidence version: create `v1` when the first material scan evidence is recorded; do not increment for restating the fixture.
- Routing: produce a bounded, current candidate list and route each plausible discrete candidate to `pre-screen`.
- VERIFY: not a separate state. Routine freshness checks remain in the scan; decision-critical disputed or stale claims may be sent to VERIFY while `scan` is preserved.
- Stop rule: stop broad scanning after a bounded candidate set is sufficient for preliminary screening; do not deep-dive every actor.

**Result:** PASS
**Difference:** `agent-native` is now named Orchestrator + current evidence tools.
**Severity:** Informational.

## Case 2 — `digital-government-before-meeting`

### Original case wording

> I have a first substantive meeting with a Digital Government contact. We know the broad domain, but not the consequential decision problem. What should I do?

### Original expected outcome

- State: `formation`
- Primary Skill: `external-engagement`
- Mode: `formation`
- Required output: `state`, `evidence_gap`, `formation_objective`, `next_evidence_action`, `stop_rule`
- Prohibited: premature proposal; resource cap; claim partnership readiness

### Actual outcome under v1.1

- State: `formation` — high confidence.
- Governing uncertainty: `field_relationship`.
- Minimum capability: External Engagement — Opportunity Formation.
- Evidence version: `v1` for the supplied evidence; the meeting increments the version only if it produces material new evidence.
- Immediate objective: identify the consequential decision, response variation, credible problem owner, sponsor hypothesis, evidence gap, and access pathway.
- Smallest next action: one bounded 30–60 minute diagnostic meeting under the de minimis rule; no Adaptive Commitment handoff.
- Transition: none yet. Do not call the relationship a partnership or move to Conversion before observable evidence supports it.
- Stop rule: do not progress if no consequential problem, credible owner, plausible access path, or combined practice/research value emerges.

**Result:** PASS
**Difference:** None.
**Severity:** None.

## Case 3 — `digital-government-after-field-evidence`

### Original case wording

> Our Digital Government meeting revealed a consequential implementation decision, two different agency responses, a credible problem owner, and possible data access. Update the opportunity.

### Original expected outcome

- State: `re-screen`
- Primary Skill: `strategic-opportunity`
- Mode: `re-screen`
- Expected next state: `conversion`
- Required output: `state`, `evidence_version`, `what_changed`, `updated_disposition`, `next_evidence_action`, `stop_rule`
- Prohibited: treat initial screen as final; skip strategic re-screen; run all three Skills

### Actual outcome under v1.1

- State: `re-screen` — high confidence.
- Governing uncertainty: `selection`, because material field evidence can change portfolio entry and opportunity design.
- Minimum capability: Strategic Opportunity — Re-screen.
- Evidence version: `vN → vN+1` exactly once because the meeting adds material field evidence.
- Transition evidence: a consequential implementation decision, response heterogeneity, a credible problem owner, and a possible data pathway materially change the initial hypothesis.
- Decision-layer output: compare the new evidence with the provisional screen and update rather than restart the strategic judgement.
- Recommended next state: `conversion` if the re-screen remains positive, because role, access, reciprocity, ownership, attribution, and governance still need qualification.
- VERIFY: not needed on the fixture as written; the supplied meeting evidence is treated as documented field evidence. Any decision-critical documentary subclaim could be verified without changing `re-screen` unless its result changes the premise.

**Result:** PASS
**Difference:** None.
**Severity:** None.

## Case 4 — `amgc-gateway-no-defined-problem`

### Original case wording

> AMGC can introduce me to firms, but there is no defined firm-level problem or project yet. Should we convert this into a collaboration?

### Original expected outcome

- State: `formation`
- Primary Skill: `external-engagement`
- Mode: `formation`
- Required output: `state`, `candidate_problem_hypotheses`, `evidence_gap`, `next_evidence_action`, `stop_rule`
- Prohibited: mistake introductions for project readiness; pitch a predetermined project; assign resources

### Actual outcome under v1.1

- State: `formation` — high confidence.
- Governing uncertainty: `field_relationship`.
- Minimum capability: External Engagement — Opportunity Formation, industry/commercial track, broker/intermediary access mode.
- Evidence version: `v1`; introductions alone do not add project-readiness evidence.
- Decision-layer output: treat AMGC as a gateway, not as proof of a formed opportunity or partnership.
- Smallest next action: ask for named firms facing recurring problems, the relevant problem owners, and direct introductions; test one bounded problem hypothesis rather than pitch a project.
- Transition: remain in `formation` until a consequential firm problem and credible owner are documented.
- Stop rule: downgrade to monitor/archive if the pathway produces only events, newsletters, generic directories, or student-project access with no route to direct substantive contact.

**Result:** PASS
**Difference:** None.
**Severity:** None.

## Case 5 — `grdc-formal-call-defined-problem`

### Original case wording

> GRDC has issued a formal call with a defined surface problem and deadline. Assess whether it is strategically worth pursuing and what should happen next.

### Original expected outcome

- State: `pre-screen`
- Primary Skill: `strategic-opportunity`
- Mode: `preliminary-screen`
- Expected next state: `conversion`
- Required output: `state`, `provisional_disposition`, `decisive_evidence_gap`, `recommended_next_state`, `stop_rule`
- Prohibited: force Formation from zero; commit resources before role qualification; assume a formal call is strategically attractive

### Actual outcome under v1.1

- State: `pre-screen` — high confidence.
- Governing uncertainty: `selection`.
- Minimum capability: Strategic Opportunity — Preliminary Screen.
- Evidence version: `v1` on the supplied call evidence.
- Decision-layer output: assess strategic fit, potential ownership, evidence pathway, opportunity cost, and hard gates; a formal call does not establish attractiveness.
- Recommended next state: `conversion` if provisionally selected, because the surface problem is already defined while role, data access, reciprocity, ownership, attribution, and partnership terms remain unresolved.
- VERIFY: not mandatory on the fixture as written because the formal call and deadline are supplied as evidence. If their currency or terms are uncertain, VERIFY checks them while preserving `pre-screen` and increments the evidence version only for material findings.
- Stop rule: reject, redesign, or monitor if user role/ownership or the evidence pathway cannot satisfy selection gates; do not commit proposal resources before qualification.

**Result:** PASS
**Difference:** None.
**Severity:** None.

## Case 6 — `energy-policy-wa-consultation`

### Original case wording

> There is an Energy Policy WA consultation. Decide whether and how it belongs in my portfolio without overstating it as engaged scholarship.

### Original expected outcome

- State: `pre-screen`
- Primary Skill: `strategic-opportunity`
- Mode: `preliminary-screen`
- Track: `policy-public-influence`
- Required output: `state`, `portfolio_classification`, `research_access_test`, `bounded_next_action`, `stop_rule`
- Prohibited: call public engagement engaged scholarship without evidence; assume consultation implies partnership; unbounded submission effort

### Actual outcome under v1.1

- State: `pre-screen` — high confidence.
- Governing uncertainty: `selection`.
- Minimum capability: Strategic Opportunity — Preliminary Screen.
- Evidence version: `v1` on the supplied consultation evidence.
- Decision-layer output: classify the opportunity as policy/public influence or service-only unless evidence supports a durable research or partnership pathway; separate policy impact from engaged scholarship and commercial scale.
- Research-access test: no reciprocal partnership, research access, data pathway, or durable project is currently evidenced.
- Smallest next action: a bounded policy-process and access test; if a live factual premise such as deadline or process stage is decision-critical, run VERIFY while preserving `pre-screen`.
- Stop rule: cap or decline active work if no identifiable decision, follow-up access, attributable public/scholarly asset, or proportionate policy impact pathway exists.

**Result:** PASS
**Difference:** The old `policy-public-influence` label maps to v1.1's policy/public substantive track plus Strategic Opportunity's service-only/public-impact portfolio classification.
**Severity:** Informational.

## Case 7 — `positive-relationship-no-sponsor`

### Original case wording

> The relationship is warm and enthusiastic, but nobody owns the problem, no sponsor has committed resources, and access is informal. Should I invest more?

### Original expected outcome

- State: `formation`
- Primary Skill: `external-engagement`
- Mode: `formation`
- Expected next state: `monitor`
- Required output: `state`, `problem_owner_gap`, `bounded_formation_test`, `next_evidence_action`, `stop_rule`
- Prohibited: escalate because of enthusiasm; treat duration as reciprocity; assign a commitment architecture

### Actual outcome under v1.1

- State: `formation` — high confidence.
- Governing uncertainty: `field_relationship`.
- Minimum capability: External Engagement — Opportunity Formation.
- Evidence version: `v1`; warm sentiment and repeated conversations are documented, but they do not establish sponsorship or reciprocity.
- Decision-layer output: identify the problem-owner and sponsor gaps; do not convert enthusiasm or relationship duration into resource readiness.
- Smallest next action: one bounded conversion/formation test seeking a named problem owner, decision access, or sponsor introduction; no Adaptive Commitment architecture.
- Transition: remain in `formation` during the test; move to `monitor` only if the bounded test fails or no credible path emerges.
- Monitor rule: name the external trigger, owner, and reopening condition rather than park indefinitely.

**Result:** PASS
**Difference:** None; `monitor` remains a conditional next state, not an immediate substitute for the required formation test.
**Severity:** None.

## Case 8 — `strong-opportunity-peripheral-role`

### Original case wording

> The opportunity itself looks strong, but my role would be peripheral and I would own neither the relationship, data, problem, nor outputs. Should I commit?

### Original expected outcome

- State: `pre-screen`
- Primary Skill: `strategic-opportunity`
- Mode: `preliminary-screen`
- Expected outcome: `redesign-or-reject`
- Required output: `state`, `hard_gate`, `provisional_disposition`, `redesign_condition`, `stop_rule`
- Prohibited: average away ownership hard gate; invoke Adaptive Commitment; equate opportunity quality with user fit

### Actual outcome under v1.1

- State: `pre-screen` — high confidence.
- Governing uncertainty: `selection`.
- Minimum capability: Strategic Opportunity — Preliminary Screen.
- Evidence version: `v1`.
- Hard gate: weak/peripheral user role with no credible relationship, data, problem, or output ownership.
- Decision-layer output: `redesign` if the architecture can establish a central, direct, attributable role; otherwise `reject`/`exit`.
- Capability boundary: Adaptive Commitment is not invoked because a downstream resource cap cannot repair a failed upstream selection gate.
- Stop rule: exit if role and ownership cannot be structurally redesigned; a strong external problem does not establish user fit.

**Result:** PASS
**Difference:** None.
**Severity:** None.

## Case 9 — `partnership-ready-resources-undecided`

### Original case wording

> We have a shared problem, sponsor, role, access, reciprocity, ownership, attribution, and governance. I now need to decide how much time and budget to commit.

### Original expected outcome

- State: `commitment`
- Primary Skill: `adaptive-commitment`
- Mode: `commitment`
- Expected next state: `review`
- Required output: `state`, `resource_floor_and_cap`, `milestone`, `evidence_standard`, `review_trigger`
- Prohibited: re-run full portfolio selection; re-run Formation; commit without a cap

### Actual outcome under v1.1

- State: `commitment` — high confidence.
- Governing uncertainty: `commitment`.
- Minimum capability: Adaptive Commitment in Orchestrated Mode.
- Evidence version: retain the latest upstream version; no increment merely for making the resource decision.
- Inherited judgements: strategic portfolio entry and Partnership Conversion evidence are accepted and not reopened.
- Decision-layer output: set a resource floor and cap, bounded responsibility, first action, milestone, evidence standard, persistence period, and review trigger.
- VERIFY: invoke only if a material cost, deadline, stage-readiness, or implementation premise is uncertain; VERIFY cannot set the commitment.
- Expected next state: `review` at the defined milestone or material evidence event.

**Result:** PASS
**Difference:** None.
**Severity:** None.

## Case 10 — `milestone-failure-different-problem`

### Original case wording

> The pilot missed its milestone, but implementation evidence revealed that the real problem is different from the one we selected. Review and route it.

### Original expected outcome

- State: `review`
- Primary Skill: `adaptive-commitment`
- Mode: `review`
- Expected transition options: `formation`, `re-screen`
- Required output: `state`, `execution_fidelity`, `belief_change`, `transition_evidence`, `recommended_state`
- Prohibited: allow only scale park or kill; treat milestone failure as automatic exit; ignore new problem evidence

### Actual outcome under v1.1

- State: `review` — high confidence.
- Governing uncertainty: first separate execution deviation from upstream thesis/problem-definition change.
- Minimum capability: Adaptive Commitment review, followed by Orchestrator routing; do not rerun all specialists.
- Evidence version: `vN → vN+1` because the implementation evidence materially changes the problem premise.
- Review output: record milestone result, execution fidelity, belief change, residual assets, and the exact transition evidence.
- Recommended route: `formation` if the real problem, owner, demand, or practice context must be relearned; `re-screen` if the new problem materially changes strategic attractiveness, design, or a selection hard gate.
- Transition: the Orchestrator, not Adaptive Commitment alone, logs the chosen transition in the append-only ledger.
- Stop rule: do not treat one missed milestone as automatic exit, and do not confine the choice to scale/park/kill.

**Result:** PASS
**Difference:** None.
**Severity:** None.

## Case 11 — `one-meeting-formation-to-conversion`

### Original case wording

> In one meeting we identified a consequential problem and owner, then the counterpart offered data access and a reciprocal role. Handle the meeting without forcing an artificial linear sequence.

### Original expected outcome

- Initial state: `formation`
- Primary Skill: `external-engagement`
- Initial mode: `formation`
- Expected next state: `conversion`
- Required output: `initial_state`, `transition_evidence`, `new_state`, `evidence_version`, `next_evidence_action`
- Prohibited: artificially split interaction into unrelated workflows; claim Conversion from the meeting outset; omit transition evidence

### Actual outcome under v1.1

- Initial state: `formation` — high confidence.
- Governing uncertainty: `field_relationship` throughout the interaction.
- Minimum capability: External Engagement, starting in Opportunity Formation and switching to Partnership Conversion only after observable evidence changes.
- Evidence version: `vN → vN+1` once for the material meeting evidence; do not increment once per label or transition.
- Transition evidence: the consequential problem and owner were identified first; data access and a reciprocal role were then offered.
- New state: `conversion`; log `formation → conversion` in the append-only transition history.
- Next action: qualify sponsor/authority, access terms, ownership, attribution, governance, and the reciprocal mechanism; hand off to Adaptive Commitment only when a concrete material resource decision exists.

**Result:** PASS
**Difference:** None.
**Severity:** None.

## Case 12 — `stale-role-programme-deadline`

### Original case wording

> Route this opportunity using a contact role, programme status, and deadline I recorded last year.

### Original expected outcome

- State: `scan`
- Primary Skill: `agent-native`
- Mode: `evidence-verification`
- Required output: `provisional_state`, `facts_to_verify`, `authoritative_sources`, `verification_date`, `stop_rule`
- Prohibited: act on stale public facts; infer current role from old title; route to commitment before verification

### Actual outcome under v1.1

- Provisional state: `scan` — high confidence that current-fact refresh must precede substantive routing.
- Governing uncertainty: `claim_verification` blocks downstream selection, relationship, or commitment routing.
- Minimum capability: Orchestrator + current evidence tools, with Evidence Verification as a horizontal sidecar.
- Originating state: remain in `scan` while VERIFY checks three atomic claims: current contact role, current programme status, and current deadline.
- Authoritative source fit: current official organisation record for role; issuing body's current programme page/guidelines for status, eligibility, deadline, amendment date, and timezone.
- Evidence version: retain `vN` while verification is pending; increment to `vN+1` only when material current evidence is added, corrected, or supersedes the old record.
- Return route: stay in `scan` if the facts merely refresh the candidate; move to the state warranted by the verified evidence only through the Orchestrator. VERIFY does not choose portfolio disposition or commitment.
- Stop rule: no substantive routing or resource commitment may rely on the year-old facts.

**Result:** PASS
**Difference:** The original `agent-native` + `evidence-verification` mode is now made explicit as Orchestrator-led `scan` + VERIFY sidecar. VERIFY is not a tenth state.
**Severity:** Informational.

## Consolidated matrix

| # | Case | Expected governing route | Actual v1.1 route | Evidence-version behaviour | VERIFY behaviour | Result | Severity |
|---:|---|---|---|---|---|---|---|
| 1 | WA agency/funding scan | `scan` → `pre-screen` | Orchestrator scan → candidate pre-screens | Start `v1` on material scan evidence | Inline/current evidence; sidecar only if material claim warrants | Pass | Info |
| 2 | Digital Government before meeting | `formation`; External Engagement | Same | Retain; increment only after material meeting evidence | Not needed | Pass | None |
| 3 | Digital Government after field evidence | `re-screen`; Strategic Opportunity → `conversion` | Same | `vN → vN+1` | Not needed on supplied field evidence | Pass | None |
| 4 | AMGC gateway/no problem | `formation`; External Engagement | Same | Retain `v1` | Not needed | Pass | None |
| 5 | GRDC formal call | `pre-screen`; Strategic Opportunity → `conversion` | Same | Retain unless current call facts materially change | Conditional sidecar for uncertain call terms | Pass | None |
| 6 | Energy Policy WA consultation | `pre-screen`; Strategic Opportunity | Same; policy/public/service classification protected | Retain unless live process facts materially change | Conditional sidecar for current process facts | Pass | Info |
| 7 | Warm relationship/no sponsor | `formation`; External Engagement → possible `monitor` | Same | Retain until material counterpart evidence | Cannot establish willingness/reciprocity | Pass | None |
| 8 | Strong opportunity/peripheral role | `pre-screen`; Strategic Opportunity → redesign/reject | Same | Retain `v1` | Not needed | Pass | None |
| 9 | Partnership ready/resources undecided | `commitment`; Adaptive Commitment → `review` | Same | Retain upstream version for decision | Conditional for material cost/deadline facts | Pass | None |
| 10 | Milestone failure/different problem | `review`; Adaptive Commitment → `formation` or `re-screen` | Same | `vN → vN+1` | Conditional if milestone facts disputed | Pass | None |
| 11 | One meeting Formation → Conversion | External Engagement with logged transition | Same | One `vN → vN+1` material update | Not needed | Pass | None |
| 12 | Stale role/programme/deadline | `scan` + current verification | Orchestrator `scan` + VERIFY sidecar | Retain pending; increment only on material verified evidence | Mandatory sidecar; no state takeover | Pass | Info |

## Regression assessment

No semantic routing regression was found in the original twelve fixtures.

The following critical-failure checks all remained clear:

- no unnecessary all-Skill invocation;
- no premature proposal, pilot, or material resource commitment;
- no false sponsor, partnership, access, ownership, reciprocity, or attribution claim;
- no hidden or unlogged state transition;
- no reliance on stale decision-critical facts;
- no same-evidence re-litigation or oscillation;
- no downstream resource decision overriding an upstream strategic or relationship hard gate;
- no VERIFY takeover of SELECT, LEARN / CONVERT, or COMMIT authority;
- `monitor` is used only with a bounded test and named reopening trigger;
- `exit` remains available where redesign cannot remove a hard gate;
- `review` distinguishes execution deviation from changed problem/strategic premises.

## Qualification

This report establishes a **12/12 deterministic routing-simulation pass** against the installed v1.1 instructions. It does not reproduce the old Agent's separate Preview procedure of repeating six boundary cases three times, and it does not test implicit invocation collisions with legacy standalone Skills. Those are separate runtime/collision tests.
