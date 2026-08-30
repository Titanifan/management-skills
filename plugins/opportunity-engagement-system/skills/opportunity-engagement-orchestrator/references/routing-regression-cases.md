# Routing Regression Cases

Use these cases to audit changes to the Orchestrator. Preserve the governing route and prohibited behaviours rather than exact prose.

## Original twelve cases

| Case | Expected route | Key invariant |
|---|---|---|
| WA agency and funding scan | `scan`; Orchestrator + current evidence tools | bounded current candidate list; no deep-dive of every candidate; no all-Skill invocation |
| Digital Government before first substantive meeting | `formation`; External Engagement Formation | diagnose consequential problem and owner before proposal or commitment |
| Digital Government after material field evidence | `re-screen`; Strategic Opportunity | initial screen is provisional; compare evidence versions |
| AMGC gateway with no defined firm problem | `formation`; External Engagement Formation | introductions are not project readiness |
| Formal call with defined surface problem and deadline | `pre-screen`; Strategic Opportunity | a formal call is not automatically attractive; field structure may route next to Conversion |
| Energy Policy WA consultation | `pre-screen`; Strategic Opportunity | protect service/public-impact classification; do not overclaim engaged scholarship or partnership |
| Warm relationship without sponsor | `formation`; External Engagement Formation | enthusiasm and duration do not equal reciprocity or resource readiness |
| Strong opportunity with peripheral user role | `pre-screen`; Strategic Opportunity | do not average away ownership/role hard gates; redesign or reject |
| Partnership ready, resources undecided | `commitment`; Adaptive Commitment | do not rerun full strategic selection or Formation; require bounded commitment |
| Milestone failure reveals a different real problem | `review`; Adaptive Commitment, then `formation` or `re-screen` | distinguish execution failure from thesis/problem-definition change |
| One meeting moves Formation to Conversion | begin `formation`, transition to `conversion` only after evidence | log transition evidence; do not claim Conversion from outset |
| Contact role, programme status, or deadline is stale | `scan` + VERIFY/current evidence | do not act on stale facts or infer current status from old records |

## Added verification and control-loop cases

### Disputed decision-critical factual premise

**Prompt pattern:** The recommendation depends on whether a licence, policy approval, contract, second OEM relationship, programme rule, or similar factual claim is true.

**Expected behaviour:** Preserve current lifecycle state; run Evidence Verification as a sidecar; update evidence version only if material evidence changes; return to the originating state unless the verified result changes an upstream premise.

**Prohibited:** treat VERIFY as a lifecycle state; let VERIFY choose portfolio disposition or resource commitment.

### De minimis outreach

**Prompt pattern:** A strategically plausible case needs one short outreach message or one 30-60 minute exploratory conversation to resolve a field uncertainty.

**Expected route:** `formation` or `conversion`; External Engagement may design the bounded interaction under its de minimis rule.

**Prohibited:** invoke Adaptive Commitment merely because the interaction consumes some time.

### Same evidence, repeated request to reconsider

**Prompt pattern:** No material evidence has changed, but the case is repeatedly reopened.

**Expected behaviour:** Keep the same evidence version, do not silently re-run the specialist, identify oscillation, and require a named new evidence trigger or explicit audit request.

### Missed milestone caused by execution drift only

**Prompt pattern:** Strategic thesis and field conditions remain intact; execution deviated from the commitment plan.

**Expected route:** `review` -> renewed `commitment` or correction within Adaptive Commitment.

**Prohibited:** strategic re-screen without material selection evidence.

### Verified fact invalidates the strategic thesis

**Prompt pattern:** VERIFY finds that a decision-critical factual premise is contradicted and the premise was material to portfolio attractiveness.

**Expected behaviour:** Preserve the originating state during VERIFY, increment evidence version, then route to `re-screen`.

**Prohibited:** Evidence Verification itself changes strategic disposition.

### No response to one outreach

**Prompt pattern:** A single outreach receives no reply and no other evidence changes.

**Expected behaviour:** Do not bounce automatically to another Skill. Follow the bounded follow-up/stop rule from External Engagement, or monitor if the rule is exhausted.

**Prohibited:** treat silence as strategic rejection or relationship evidence beyond what it supports.

## Critical failure conditions

Any of the following is a regression:

- unnecessary invocation of all specialist Skills;
- premature proposal, pilot, or resource commitment;
- false partnership, sponsor, access, ownership, or attribution claim;
- hidden or unlogged state transition;
- reliance on stale decision-critical facts without verification;
- same-evidence routing oscillation;
- downstream layer overriding an unresolved upstream hard gate;
- VERIFY making a SELECT, LEARN / CONVERT, or COMMIT decision.

## Exact original fixtures

The exact twelve original JSON fixtures from the prior Workspace Agent deployment are preserved in `references/original-routing-cases.json`. Use that file when reproducing the original eval semantics or comparing future routing changes against the prior deployment.
