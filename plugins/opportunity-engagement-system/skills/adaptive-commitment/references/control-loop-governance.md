# Control-Loop Governance for Adaptive Commitment

## Purpose

Use this reference when execution must remain aligned with a target under uncertainty, delay, disturbance, noisy evidence, changing constraints, or repeated review. It converts the Adaptive Commitment learning loop into an explicit closed-loop governance discipline.

Do not use control language to force persistence toward a target after the strategic thesis has become invalid. The loop governs commitment and execution; it does not own the legitimacy of the strategic target. Material evidence that changes strategic attractiveness must be routed to Strategic Opportunity. Material evidence that reopens the external problem, sponsor, access, ownership, or partnership must be routed to External Engagement.

This reference is inspired by engineering cybernetics and control theory, including feedback-control ideas associated with Norbert Wiener, W. Ross Ashby, and H. S. Tsien's *Engineering Cybernetics*. The translation to project, portfolio, and academic execution is an authorial synthesis, not a technical control model and not a claim that organisational systems behave like linear engineered systems.

## Table of contents

1. Trigger conditions
2. Control-loop model
3. Governance workflow
4. Delay, noise, and over-correction
5. Requisite response capacity
6. Stability and stopping rules
7. Integration with existing Adaptive Commitment modules
8. Common failure modes
9. Output template
10. Routing rules

## 1. Trigger conditions

Load this reference when:

- the opportunity will be reviewed repeatedly rather than decided once;
- execution has meaningful delay between action and observable outcome;
- milestones can be missed for several different reasons;
- the environment can disturb the plan after commitment;
- progress indicators are noisy or lagged;
- repeated correction could create oscillation or thrashing;
- the user must distinguish thesis failure from execution failure;
- multiple agents, collaborators, teams, students, vendors, or workstreams require coordinated correction;
- scale decisions depend on whether the current system is stable and controllable;
- the commitment needs explicit stop, escalation, fallback, or safe-state rules.

Do not load this reference for a trivial one-step action with immediate and unambiguous feedback.

## 2. Control-loop model

Represent the commitment using the following elements.

### 2.1 Target state

Define the desired state or milestone clearly enough to observe whether execution is converging toward it.

The target should include:

- desired outcome or state;
- evidence standard;
- time or condition horizon;
- non-negotiable governance boundary;
- acceptable range rather than false single-point precision where appropriate.

Do not substitute activity volume for target state.

### 2.2 Observed state

Identify what can actually be measured or documented now.

Separate:

- leading indicators;
- lagging outcomes;
- execution inputs;
- external disturbances;
- qualitative evidence that cannot be reduced to one metric.

### 2.3 Error or deviation

Define the meaningful gap between target and observed state.

Ask whether the deviation is:

- within normal variance;
- a small correctable drift;
- a persistent execution problem;
- evidence that the target or thesis is wrong;
- caused by an external disturbance;
- caused by measurement delay or poor observability.

Do not treat every deviation as failure.

### 2.4 Controller

Name who or what has authority to change the commitment.

The controller may be:

- the user;
- a project lead;
- a supervisory team;
- a steering group;
- a jointly agreed governance mechanism;
- an orchestrator routing decision.

Avoid ambiguous control where many people can intervene but nobody owns correction.

### 2.5 Control action

Specify the type of correction available, such as:

- narrow scope;
- increase or decrease resource;
- change sequencing;
- change responsible owner;
- add capability;
- remove a dependency;
- redesign the experiment;
- slow or pause execution;
- escalate governance;
- delegate;
- terminate.

Do not prescribe resource amounts here without using the main Adaptive Commitment contract.

### 2.6 Disturbances

Identify material external changes that can move the system independently of execution quality.

Examples include:

- policy change;
- collaborator departure;
- data loss;
- market shift;
- procurement delay;
- health or capacity shock;
- technology change;
- sponsor change;
- competitor action;
- regulatory intervention.

Do not punish execution for disturbances that invalidate the original assumptions. Re-route when appropriate.

## 3. Governance workflow

### Step 1: Define the controlled variable

State what must remain within an acceptable range or move toward a target.

Examples:

- evidence quality;
- milestone completion;
- customer adoption;
- manuscript progress;
- budget exposure;
- workload burden;
- partner reciprocity;
- model performance;
- implementation reliability.

Use only variables that meaningfully affect the decision.

### Step 2: Define target band and guardrails

Specify:

- target or acceptable band;
- minimum acceptable threshold;
- hard boundary that must not be crossed;
- evidence required to justify scale or deeper commitment.

Prefer ranges when the underlying system is noisy.

### Step 3: Define observation points

Choose observations that are frequent enough to detect meaningful drift but not so frequent that noise drives constant intervention.

Match review timing to the system's delay.

### Step 4: Define correction classes before execution

Pre-commit the available responses:

- **hold:** deviation is within tolerance;
- **correct:** execution remains valid but needs adjustment;
- **redesign:** mechanism or implementation architecture requires change;
- **de-escalate:** reduce resource or scope;
- **pause:** wait for an external condition or missing evidence;
- **re-route:** send the case back to Strategic Opportunity or External Engagement;
- **exit:** stop because a hard boundary or kill condition has been reached;
- **scale:** increase commitment only when evidence and system stability justify it.

### Step 5: Observe before correcting

At each review, record:

- observed state;
- expected state at this point;
- deviation;
- likely cause;
- confidence in the measurement;
- whether the evidence is leading, lagging, or noisy.

### Step 6: Diagnose the source of deviation

Distinguish:

- execution failure;
- capability deficit;
- resource insufficiency;
- sequencing error;
- governance failure;
- external disturbance;
- measurement error;
- thesis failure;
- field-assumption failure.

Do not correct the wrong layer.

### Step 7: Apply the smallest correction likely to restore control

Avoid large changes when a smaller reversible intervention can resolve the deviation.

Prefer corrections that produce additional diagnostic information.

### Step 8: Re-observe after the relevant delay

Do not judge the correction before enough time has passed for its effect to become observable.

### Step 9: Escalate only when evidence justifies it

Scale intervention when:

- deviation persists;
- the consequence of drift is material;
- the system remains controllable;
- the corrective action does not violate resource or governance boundaries.

### Step 10: Update the rule only after learning

If the correction reveals a repeatable pattern, update the relevant execution, routing, or calibration rule. Do not rewrite the system after one noisy case.

## 4. Delay, noise, and over-correction

### 4.1 Delay discipline

When action and outcome are separated by delay:

- identify the expected delay explicitly;
- use leading indicators where legitimate;
- avoid interpreting absence of immediate outcome as failure;
- avoid adding new interventions before the prior intervention can be observed;
- shorten the loop only when a reliable earlier signal exists.

### 4.2 Noise discipline

Do not react to every fluctuation.

Use a tolerance band when:

- the metric varies naturally;
- data are sparse;
- qualitative judgement is involved;
- outcomes are affected by external shocks.

Escalate when deviation is persistent, directional, decision-relevant, or boundary-threatening.

### 4.3 Over-correction and oscillation

Repeated aggressive changes can create instability.

Watch for:

- alternating priorities;
- repeated scope expansion and contraction;
- hiring then freezing;
- changing research questions after every result;
- changing outreach strategy after every unanswered message;
- adding and removing resources before effects can be observed.

When oscillation appears:

- slow the correction cadence;
- reduce correction magnitude;
- separate structural from temporary causes;
- wait through the relevant delay;
- improve measurement before intervening again.

### 4.4 Integral-like accumulation without technical formalism

A small deviation that persists can matter more than one large temporary deviation.

Track cumulative burden such as:

- repeated missed milestones;
- persistent workload overruns;
- recurring free work;
- repeated collaborator rescue;
- chronic low adoption;
- continuing budget leakage.

Do not reset the diagnosis merely because each individual deviation looks small.

## 5. Requisite response capacity

A control system cannot manage disturbances that exceed its ability to sense, interpret, and respond.

Translate this into governance questions:

- Are the important states observable?
- Is there enough decision authority to correct them?
- Does the team possess enough capability variety to respond to different failure modes?
- Can the user distinguish technical, relational, strategic, and governance problems?
- Are there fallback options when one response channel fails?

If the project requires more response variety than the team or governance system can supply, reduce scope, add capability, delegate, or redesign rather than relying on optimism.

Do not use "requisite variety" as a numerical rule unless a real technical model exists.

## 6. Stability and stopping rules

### Stable enough to continue

Continue when:

- key variables remain within guardrails;
- deviations are understandable and correctable;
- the resource cap remains credible;
- learning accumulates;
- the strategic thesis remains intact.

### Ready to scale

Scale only when:

- the relevant mechanism has repeated support;
- execution is not dependent on heroic intervention;
- bottlenecks are visible and manageable;
- governance can absorb greater volume;
- the system does not become unstable when load increases;
- required field and strategic assumptions remain valid.

### Redesign

Redesign when:

- the target remains valid but the control architecture cannot reliably reach it;
- feedback is too delayed or noisy;
- the wrong variable is being controlled;
- responsibility or decision rights are unclear;
- a recurring failure mode is structural rather than incidental.

### Re-route

Re-route instead of correcting harder when:

- evidence changes strategic attractiveness -> Strategic Opportunity;
- the real problem, sponsor, access, reciprocity, ownership, or partnership becomes unclear -> External Engagement.

### Exit

Exit when:

- a hard safety, ethics, governance, workload, or financial boundary is crossed;
- the core mechanism is contradicted and proportionate redesign is unavailable;
- repeated correction fails to restore control;
- the commitment requires persistent heroic effort with no compounding asset;
- the system is not observable or governable at a proportionate cost.

## 7. Integration with existing Adaptive Commitment modules

Use this reference with, not instead of, the existing modules.

### With `execution-doctrine.md`

Execution Doctrine defines the commitment contract. Control-Loop Governance defines how to observe and correct that contract during execution.

### With `learning-loop-calibration.md`

Learning-Loop Calibration evaluates decision quality, execution fidelity, learning, and realised outcome across review periods. Control-Loop Governance manages shorter-cycle deviation and correction between those calibration reviews.

### With `commitment-and-convergence.md`

Commitment and Convergence determines when comparison should stop and bounded action should begin. Control-Loop Governance prevents that commitment from becoming blind persistence.

### With `orchestrator-handoff.md`

The orchestrator receives material evidence and decides whether the case remains in commitment or returns to re-screen, formation, conversion, monitor, or exit.

## 8. Common failure modes

### Open-loop execution

A plan is launched and reviewed only at the end.

Correction: define observation points and correction classes before execution.

### Metric fixation

One easy metric becomes the target even when it no longer represents the desired outcome.

Correction: retain qualitative evidence, guardrails, and thesis-level checks.

### Control harder after thesis failure

Negative strategic evidence triggers more execution effort.

Correction: re-route rather than intensify control.

### Hyper-reactive management

Every deviation triggers a new intervention.

Correction: account for noise and delay; use tolerance bands.

### Controller ambiguity

Multiple actors intervene without clear authority.

Correction: name the controller and escalation path.

### Heroic stabilisation

The system appears stable only because one person repeatedly rescues it.

Correction: treat rescue dependency as evidence of structural instability.

### Review without consequence

Milestones are discussed but no action follows.

Correction: predefine correction, redesign, de-escalation, scale, and exit responses.

## 9. Output template

For a control-sensitive commitment, report:

- **Controlled variable:**
- **Target / acceptable band:**
- **Guardrails / hard boundary:**
- **Observed state:**
- **Expected state:**
- **Deviation:**
- **Likely source:** execution / capability / resource / sequencing / governance / disturbance / measurement / thesis / field assumption
- **Expected feedback delay:**
- **Correction class:** hold / correct / redesign / de-escalate / pause / re-route / exit / scale
- **Smallest justified correction:**
- **Next observation condition:**
- **Re-route trigger:**
- **Exit trigger:**

## 10. Routing rules

- Keep the case in Adaptive Commitment when the strategic thesis and field conditions remain adequate and the issue is execution control.
- Return to Strategic Opportunity when material evidence changes strategic attractiveness, platform fit, potential ownership, hard gates, or portfolio disposition.
- Return to External Engagement when the real problem, decision owner, sponsor, access, reciprocity, actual ownership, or partnership readiness becomes unresolved.
- Route claim-level factual disputes to an Evidence Verification capability when available; do not manufacture certainty through repeated internal reasoning.
