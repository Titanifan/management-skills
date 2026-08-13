# Management Skills

Evidence-informed, executable management knowledge for consequential decisions.

This repository turns management research into reusable decision workflows. It is not a collection of literature summaries or generic prompts. Each Skill defines a decision problem, a sequence of diagnostic moves, the constructs and mechanisms that inform those moves, boundary conditions, failure modes, and an explicit evidence-provenance layer.

## The three decision problems

| Skill | Primary question | Stops before |
|---|---|---|
| [Strategic Opportunity](skills/strategic-opportunity/) | Should I pursue this opportunity? | Detailed execution and resource allocation |
| [External Engagement](skills/external-engagement/) | How should I build relationships that create future opportunities? | Portfolio selection and full commitment architecture |
| [Adaptive Commitment](skills/adaptive-commitment/) | How much should I commit now? | Treating an initial decision as permanently settled |

The boundaries are intentional. Strategic Opportunity decides whether an opportunity deserves portfolio entry. External Engagement converts access into direct, attributable, reciprocal relationships. Adaptive Commitment converts a justified direction into staged commitment, evidence checkpoints, learning, and reallocation.

## Repository structure

```text
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

## Evidence and limits

Each Skill routes to `references/evidence-base.md`. Those files distinguish source-supported constructs from workflow translations and authorial heuristics. The sources provide provenance; they do not validate the complete Skill as a unified predictive model.

The workflows deliberately avoid false precision. Scores and equations are structured judgement aids, not estimated causal models. Rules should be calibrated through real cases, with decision quality assessed separately from realised outcomes.
