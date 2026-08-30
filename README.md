# Management Skills

Executable management knowledge for consequential decisions.

This repository translates management research, practitioner frameworks, and explicit design synthesis into reusable decision workflows. It is not a collection of literature summaries or generic prompts. Each Skill defines a decision problem, diagnostic moves, source provenance, boundary conditions, failure modes, and handoffs to adjacent decisions.

Source transparency matters more than citation volume. A scholarly construct, a cross-level translation, a practitioner thesis, and an author-designed score do not carry the same claim. See [GOVERNANCE.md](GOVERNANCE.md) for the closed provenance taxonomy and release rules.

## Current workspace plugin: Opportunity & Engagement System v1.1

The recommended installation is the consolidated [Opportunity & Engagement System](plugins/opportunity-engagement-system/) plugin. It contains five coordinated Skills:

- Opportunity & Engagement Orchestrator
- Strategic Opportunity
- External Engagement
- Evidence Verification
- Adaptive Commitment

The plugin coordinates a nine-state lifecycle and preserves evidence versions, routing history, verification sidecars, commitment reviews, monitoring, and exit logic. The root-level `skills/` directories remain available as the legacy v0.2 standalone source, but they are not the recommended current installation.

Release evidence: [v1.1 original 12-case routing regression report](evals/opportunity-engagement-v1.1-regression-report.md) — 12/12 passed, with no critical, major, or minor regression found in the deterministic routing simulation.

### Import into a ChatGPT workspace

Workspace admins can import this repository as a Git marketplace:

1. Open **Admin → Plugins → Add → Import marketplace**.
2. Use `https://github.com/Titanifan/management-skills` as **Source**.
3. Leave **Path** blank.
4. Use `main` as **Branch**, or leave Branch blank to follow the repository default.
5. Import the marketplace, then set the plugin's installation policy for the intended roles.

After future GitHub releases, use **Admin → Plugins → Marketplaces → Management Skills → Sync now** to request an immediate update.

## Legacy standalone decision Skills

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
.agents/
  plugins/
    marketplace.json
GOVERNANCE.md
VERSION
evals/
  cases.md
  opportunity-engagement-v1.1-regression-report.md
plugins/
  opportunity-engagement-system/
    .codex-plugin/
      plugin.json
    skills/
      opportunity-engagement-orchestrator/
      strategic-opportunity/
      external-engagement/
      evidence-verification/
      adaptive-commitment/
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

The consolidated plugin under `plugins/` is the canonical v1.1 release. Each root-level legacy Skill directory remains independently installable for rollback or historical comparison.

GitHub is the canonical source. Edit and validate a repository checkout, then sync or install a released version. Treat personal Skill directories and plugin caches as replaceable runtime copies rather than editing locations.

## Provenance and evaluation

Each Skill routes to `references/provenance.md`. Those files distinguish `Scholarly-direct`, `Scholarly-translated`, `Practitioner-derived`, `Authorial-synthesis`, and `Case-calibrated` knowledge. Sources provide provenance; they do not validate a complete Skill or a specific verdict.

The workflows deliberately avoid false precision. Scores and equations are structured decision aids, not estimated causal models. The synthetic cases in [evals/cases.md](evals/cases.md) test decision boundaries and failure modes without prescribing one correct verdict. Future case calibration must record poor outcomes after sound decisions as well as favourable outcomes after weak decisions.
