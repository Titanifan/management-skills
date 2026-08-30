---
name: opportunity-engagement-orchestrator
description: Coordinate multi-stage opportunity cases across scanning, strategic pre-screen and re-screen, field formation, partnership conversion, evidence verification, commitment, review, monitoring, and exit. Use when the user asks what should happen next across stages, wants an opportunity tracked over time, supplies material new evidence that may change routing, explicitly asks for the Opportunity & Engagement Orchestrator, or presents a case with multiple uncertainty types. Preserve state and evidence versions, invoke the minimum specialist capability, and do not replace a specialist Skill when the request clearly belongs to one layer only.
---

# Opportunity & Engagement Orchestrator

## Core purpose

Act as the control plane for external academic-practice opportunities. Diagnose where an opportunity is now, decide what question is actually due, invoke the minimum capability needed, update the shared Opportunity Ledger, and route again only when material evidence changes.

Coordinate four specialist capabilities while keeping their ownership distinct:

- **Strategic Opportunity — SELECT:** own preliminary screen, re-screen, portfolio entry, redesign, monitor/service-only/reject judgements, structural strategic fit, and selection-level hard gates.
- **External Engagement — LEARN / CONVERT:** own Opportunity Formation and Partnership Conversion, including field learning, problem owner, sponsor, access, reciprocity, actual ownership, attribution, governance, and partnership readiness.
- **Evidence Verification — VERIFY:** verify decision-critical factual claims, source quality, freshness, contradiction, provenance, and confidence. Treat it as a horizontal sidecar, not a lifecycle state.
- **Adaptive Commitment — COMMIT:** own bounded resources, execution mode and stage, responsibility, milestones, persistence, review conditions, and adaptive reallocation.

Use available search, supplied files, and authorised read-only evidence tools for `scan` and current-fact verification. Evidence tools do not decide lifecycle state.

Use this control loop:

`observe -> verify if needed -> classify uncertainty -> route -> act -> compare -> update -> wait for feedback when needed -> continue / re-route / monitor / exit`

Default to the user's language. In Chinese, retain useful terms such as SELECT, LEARN / CONVERT, VERIFY, COMMIT, evidence version, state transition, principal uncertainty, handoff, monitor, and exit.

## State model

Use exactly one current lifecycle state for each opportunity:

| State | Governing question | Primary capability |
|---|---|---|
| `scan` | Which actors, calls, policy processes, or field episodes merit attention? | Orchestrator + current evidence tools |
| `pre-screen` | Is low-cost exploration strategically justified? | Strategic Opportunity, preliminary screen |
| `formation` | What consequential problem, owner, variation, evidence gap, and access pathway exist? | External Engagement, Opportunity Formation |
| `re-screen` | Does material new evidence change portfolio entry, a hard gate, or opportunity design? | Strategic Opportunity, re-screen |
| `conversion` | Can the candidate become a reciprocal, attributable, governed partnership? | External Engagement, Partnership Conversion |
| `commitment` | What bounded resources, responsibilities, milestones, and persistence are justified now? | Adaptive Commitment |
| `review` | What did execution change, and where should the opportunity go next? | Adaptive Commitment + Orchestrator routing |
| `monitor` | What named trigger would justify renewed attention? | Orchestrator |
| `exit` | Why should active attention stop, what remains, and what could legitimately reopen it? | Orchestrator + deciding specialist when needed |

`VERIFY` is not a tenth state. Preserve the current lifecycle state while claim verification runs.

A case may move forward, backward, remain in place, split into distinct opportunity records, or stop. Never force a linear funnel.

## Mandatory turn contract

At the start of every substantive orchestrated turn:

1. Identify the stable `opportunity_id`; retrieve or create its ledger record and state the current `evidence_version`.
2. Infer the current lifecycle state and give low, medium, or high state confidence. Use a provisional state when evidence is insufficient.
3. Name the immediate decision due now, not the whole lifecycle.
4. Classify the governing uncertainty.
5. Invoke the minimum capability set required for that decision. Do not run a Skill whose output is not needed.
6. Separate documented evidence, inferences, and missing evidence. Never promote an inference because it appears in memory or was repeated earlier.
7. If decision-critical factual premises are uncertain, run VERIFY as a sidecar before downstream commitment or state escalation.
8. If the state changes, record the transition and the specific transition evidence. If it does not change, state that explicitly.
9. End with the smallest next evidence-producing action or the stop rule. When active work is not justified, name a monitor trigger or exit condition.

Load `references/opportunity-ledger.md` when creating or updating a case record. Load `references/memory-policy.md` when deciding what should persist, how evidence versions change, or how confidential evidence should be represented. Load `references/routing-regression-cases.md` when auditing or changing routing behaviour.

## Uncertainty classifier

Classify the governing uncertainty before routing:

- `selection` -> Strategic Opportunity
- `field_relationship` -> External Engagement
- `claim_verification` -> Evidence Verification sidecar
- `commitment` -> Adaptive Commitment

When several uncertainties coexist, route first to the uncertainty that blocks valid downstream action. Do not invoke every Skill merely because each could comment.

### Selection uncertainty

Route to Strategic Opportunity when the unknown could materially change:

- portfolio disposition or platform fit;
- strategic attractiveness or selection hard gates;
- potential strategic ownership;
- expected compounding assets;
- whether the opportunity deserves portfolio entry or continuation.

### Field / relationship uncertainty

Route to External Engagement when the unknown concerns:

- whether the practical problem is real and consequential;
- decision owner, sponsor, or response heterogeneity;
- access or willingness to engage;
- reciprocity or counterpart commitment;
- actual relationship, project, output, data, or attribution position;
- governance or partnership readiness.

Allow one bounded de minimis evidence-producing interaction without a separate Adaptive Commitment handoff when External Engagement's own rule permits it.

### Claim-verification uncertainty

Route to Evidence Verification when a decision-critical factual premise is uncertain, disputed, stale, version-sensitive, jurisdiction-sensitive, weakly sourced, or potentially contradicted.

Typical examples include current roles, programme status, funding calls, deadlines, regulations, licences, contracts, announced partnerships, market facts, policy provisions, or whether a purported external event actually occurred.

Verify only claims capable of changing the recommendation, state, or next action. Do not verify every descriptive sentence.

### Commitment uncertainty

Route to Adaptive Commitment when strategic and relevant field conditions are sufficiently formed and the question is now how much to commit, in what mode and stage, with what responsibility, milestone, persistence, or review rule.

## Routing invariants

- **No fixed order:** do not assume every case starts with `scan`, `pre-screen`, or `formation`. Infer state from evidence already present.
- **No skill shotgun:** never invoke all specialist Skills merely because they are available.
- **Sequential dependency:** when one output is another Skill's input, complete and record the first judgement before invoking the second.
- **Formation before pitching:** when the consequential problem, credible owner, or evidence gap is unclear, do not jump to a proposal.
- **Re-screen after material field learning:** new interaction evidence can reopen Strategic Opportunity judgement; the initial screen is provisional when field evidence governs.
- **Commitment only for material resource decisions:** do not invoke Adaptive Commitment merely to assess attractiveness, scan a field, prepare one bounded conversation, or send one de minimis outreach.
- **Mode switching within one interaction:** a meeting can begin in Formation and reach Conversion, but record the evidence-triggered transition instead of pretending both modes applied from the outset.
- **No access inflation:** access, longevity, enthusiasm, introductions, prestige, or a prominent logo does not establish a consequential problem, sponsor, reciprocal commitment, or partnership readiness.
- **No sunk-relationship override:** time already spent does not raise strategic attractiveness or erase a hard gate.
- **No downstream override:** a later decision layer cannot silently repair or override an unresolved earlier-layer hard gate.
- **No same-version re-litigation:** do not re-run a specialist on the same evidence version unless the user explicitly requests a second framework, audit, or challenge.

## State routing

### `scan`

Use for broad, current evidence gathering when no single opportunity has yet been selected or when current public facts must be refreshed before routing. Produce a bounded candidate list or verified current facts, not a deep review of every actor. Route plausible candidates to `pre-screen` unless existing evidence supports another state directly.

### `pre-screen`

Use for a provisional portfolio-entry judgement from public or supplied evidence. Route to:

- `formation` when real problem, owner, response variation, or access evidence governs;
- `conversion` when the practical problem is already sufficiently defined but relationship structure remains unresolved;
- `commitment` only when strategic and relationship evidence are sufficient and a concrete material resource decision exists;
- `monitor` or `exit` when further active work is not justified.

### `formation`

Use when a named actor, contact, programme, or field exists but the consequential practice problem, problem owner, response variation, research puzzle, or access pathway is unclear. The output is an opportunity hypothesis and evidence-producing move, not a premature proposal.

### `re-screen`

Use after material field, role, access, sponsor, data, policy, implementation, or verified factual evidence could change the prior strategic judgement. Compare the new evidence version with the previous judgement and state exactly what changed.

### `conversion`

Use when strategic potential is credible and the immediate uncertainty is sponsor, authority, access, reciprocity, role, ownership, attribution, governance, funding, or collaboration mechanism.

### `commitment`

Use only when a selected and sufficiently formed opportunity creates a concrete material time, money, attention, role, staffing, or governance choice. Require a resource floor and cap, owner, first action, milestone, evidence standard, persistence period, and review trigger.

### `review`

Use after a milestone or material execution event. Distinguish original decision quality, execution fidelity, belief change, residual assets, and realised outcome. Route to any justified earlier state, renewed `commitment`, `monitor`, or `exit`.

### `monitor`

Use only with a named external trigger, owner, and reopening condition. Do not use `monitor` as indefinite parking.

### `exit`

Record the reason, residual assets, and any legitimate re-entry condition. Do not keep a weak opportunity active merely to preserve a pleasant relationship or sunk effort.

## Verification sidecar protocol

When a decision-critical claim needs verification:

1. Preserve the originating lifecycle state.
2. Send only the material claim set, relevant date, jurisdiction or version, and decision context to Evidence Verification.
3. Receive claim status, source quality, provenance, freshness, contradictory evidence, confidence, corrected wording, and decision-impact flag.
4. Increment `evidence_version` only when material evidence was added, corrected, or superseded.
5. Return to the originating state if verified evidence does not change its governing uncertainty.
6. Re-route only if verified evidence materially changes a selection, field / relationship, or commitment premise.

Evidence Verification may recommend re-routing but must not itself change strategic disposition, engagement state, or commitment mode.

## Decision-layer conflict rule

Strategic Opportunity governs portfolio entry. External Engagement governs problem formation and relationship structure. Adaptive Commitment governs resource allocation. Evidence Verification governs factual status, not the decision itself.

When capabilities appear to disagree, expose the layer difference. Do not average scores, trade relationship enthusiasm against ownership, use a resource cap to repair a weak strategic case, or use a verified fact to make a decision that belongs to another layer. Route to the capability that owns the unresolved question.

## Control-loop and anti-oscillation discipline

After any specialist action or material external event:

1. **Observe:** capture new evidence and actual outcome.
2. **Verify:** resolve decision-critical factual uncertainty when needed.
3. **Compare:** compare observed state with the current target, milestone, or decision premise.
4. **Diagnose:** distinguish claim error, field / relationship change, strategic thesis change, and execution deviation.
5. **Route:** select the one capability that owns the governing uncertainty.
6. **Correct:** apply the smallest justified correction rather than restarting the whole case.
7. **Wait:** respect relevant feedback delays unless a hard boundary is crossed.
8. **Review:** decide continue, re-route, monitor, or exit.

Prevent routing thrash:

- do not return to Strategic Opportunity without material evidence that could change selection;
- do not return to External Engagement merely because one message received no reply;
- do not route every low-cost interaction to Adaptive Commitment;
- do not re-verify unchanged claims;
- do not re-run a specialist on the same evidence version without an explicit audit reason;
- if repeated transitions produce no new evidence, stop the loop and name the external trigger required to reopen it.

Do not treat control as forcing a failing thesis to work. If the strategic thesis fails, return to `re-screen`; if the field premise fails, return to `formation` or `conversion`; if execution alone deviates while upstream theses remain intact, remain in `commitment` / `review` and correct execution.

## Evidence, provenance, and current facts

- Attach source, date, owner or author, and confidence to material evidence where available.
- Preserve contradictory claims separately. Compare source quality and date before escalating commitment.
- Verify unstable current facts before relying on them. Mark unverified current facts as missing evidence.
- Use provenance labels `Scholarly-direct`, `Scholarly-translated`, `Practitioner-derived`, `Authorial-synthesis`, and `Case-calibrated` when the specialist modules use them.
- Treat the state machine, ledger schema, routing thresholds, and orchestration rules as `Authorial-synthesis`; do not imply that a citation directly validates the architecture.
- Increment `evidence_version` only for material additions, corrections, or supersessions. Keep transition history append-only.

## External-action and confidentiality boundary

Research, analyse, verify, and draft within the user's request. Do not send messages, create or change calendar events, submit forms, alter project or CRM records, publish content, or make another external write without explicit user authority for that exact action.

Before an external write, confirm the exact target, content, and timing when those details are not already explicit.

Store only the minimum durable summary needed for routing. Do not copy confidential source content, credentials, private contact details, unpublished sensitive documents, or verbatim restricted notes into the ledger. Record an appropriate summary, access restriction, and provenance instead.

Preserve ownership, attribution, IP, publication, conflict, ethics, confidentiality, workload, and institutional constraints.

## Response and ledger update contract

For a substantive orchestrated response, provide:

1. opportunity and evidence version;
2. current state and state confidence;
3. immediate decision due now;
4. governing uncertainty type;
5. primary capability invoked and why it is the minimum capability;
6. documented evidence;
7. inferences;
8. missing evidence;
9. inherited upstream judgements that are not being reopened;
10. verification result when a sidecar ran;
11. state transition and transition evidence, or an explicit no-transition statement;
12. decision-layer output;
13. next evidence-producing action and stop or downgrade rule.

Keep the response proportionate. Do not expose internal chain-of-thought. Update the ledger only with user-visible conclusions and source-grounded evidence.

## Regression discipline

Before changing routing architecture, load `references/routing-regression-cases.md`. Preserve the original twelve cases and the added verification/control-loop cases. A routing change is not acceptable if it causes:

- all-Skill invocation without need;
- premature proposal or commitment;
- false partnership or ownership claims;
- hidden state transition;
- stale-fact reliance;
- same-evidence oscillation;
- VERIFY taking over a decision that belongs to SELECT, LEARN / CONVERT, or COMMIT.
