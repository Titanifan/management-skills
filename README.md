# Management Skills

Executable management knowledge for consequential decisions.

This repository translates management research, practitioner frameworks, and explicit design synthesis into reusable decision workflows. It is not a collection of literature summaries or generic prompts. Each Skill defines a decision problem, diagnostic moves, source provenance, boundary conditions, failure modes, and handoffs to adjacent decisions.

Source transparency matters more than citation volume. A scholarly construct, a cross-level translation, a practitioner thesis, and an author-designed score do not carry the same claim. See [GOVERNANCE.md](GOVERNANCE.md) for the closed provenance taxonomy and release rules.

## The three decision problems

| Skill | Primary question | Stops before |
|---|---|---|
| [Strategic Opportunity](skills/strategic-opportunity/) | Should I pursue this opportunity? | Detailed execution and resource allocation |
| [External Engagement](skills/external-engagement/) | How should I build relationships that create future opportunities? | Portfolio selection and full commitment architecture |
| [Adaptive Commitment](skills/adaptive-commitment/) | How much should I commit now? | Treating an initial decision as permanently settled |

The boundaries are intentional. Strategic Opportunity decides whether an opportunity deserves portfolio entry. External Engagement converts access into direct, attributable, reciprocal relationships. Adaptive Commitment converts a justified direction into staged commitment, evidence checkpoints, learning, and reallocation.

## Source profiles

| Skill | Source profile | Important limit |
|---|---|---|
| Strategic Opportunity | Strategy and entrepreneurship research + practitioner venture lens + authorial scoring architecture | Strategic-entrepreneurship research does not validate Peter Thiel's seven questions or the repository's thresholds. |
| External Engagement | University–industry, intermediary, policy-engagement, and career research + authorial relationship workflow | The complete relationship ladder, ownership taxonomy, dashboard, and free-work boundary are not one validated model. |
| Adaptive Commitment | Real-options, escalation, attention, learning, and decision-process research + authorial commitment architecture | The seven layers, decision modes, resource contract, and review protocol are design choices requiring calibration. |

## Repository structure

```text
GOVERNANCE.md
VERSION
evals/
  cases.md
skills/
  strategic-opportunity/
    SKILL.md
    agents/openai.yaml
    assets/
    references/
  external-engagement/
    SKILL.md
    agents/openai.yaml
    assets/
    references/
  adaptive-commitment/
    SKILL.md
    agents/openai.yaml
    assets/
    references/
```

Each directory is independently installable. Copy the desired directory into a compatible personal Skills location such as `~/.codex/skills/` or `~/.agents/skills/`.

GitHub is the canonical source. Edit and validate a repository checkout, then install a released version. Treat personal Skill directories as replaceable runtime copies rather than editing locations.

## Provenance and evaluation

Each Skill routes to `references/provenance.md`. Those files distinguish `Scholarly-direct`, `Scholarly-translated`, `Practitioner-derived`, `Authorial-synthesis`, and `Case-calibrated` knowledge. Sources provide provenance; they do not validate a complete Skill or a specific verdict.

The workflows deliberately avoid false precision. Scores and equations are structured decision aids, not estimated causal models. The synthetic cases in [evals/cases.md](evals/cases.md) test decision boundaries and failure modes without prescribing one correct verdict. Future case calibration must record poor outcomes after sound decisions as well as favourable outcomes after weak decisions.
