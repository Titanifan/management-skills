# Repository Governance

## Canonical source

The GitHub repository is the source of truth. Make substantive edits in a repository checkout, validate them, commit them, and install a released version into a runtime Skill directory.

Do not treat `~/.codex/skills/` or `~/.agents/skills/` as authoring locations. Installed copies are deployment artifacts and may be replaced during an update.

## Provenance taxonomy

Every major rule or module must use one of these labels in its Skill-level `references/provenance.md`:

| Label | Meaning | Permitted claim |
|---|---|---|
| `Scholarly-direct` | A source directly develops the named construct, mechanism, or distinction. | The Skill uses a recognised scholarly construct or mechanism. |
| `Scholarly-translated` | An executable rule adapts scholarship across level or context. | The rule is informed by scholarship but is not directly validated by it. |
| `Practitioner-derived` | A rule or lens comes from a practitioner book, interview, speech, or operating philosophy. | The source offers a practical lens whose assumptions and limits must be tested. |
| `Authorial-synthesis` | The repository combines sources into a workflow, score, threshold, classification, or artefact. | The element is an explicit design choice requiring calibration. |
| `Case-calibrated` | Repeated documented cases support a behaviour under stated conditions. | The behaviour has local calibration evidence, not universal validation. |

Version 0.2.0 assigns no component `Case-calibrated` status.

## Claim discipline

- Organise a Skill by the decision it improves, not by whether its sources are academic or practical.
- Separate what a source claims from how the Skill operationalises it.
- Do not use adjacent scholarship to imply validation of a practitioner framework.
- Do not describe a score, threshold, taxonomy, or complete workflow as evidence-based unless that exact element has direct support.
- State level-of-analysis transfers. Firm-, team-, and organisation-level constructs do not automatically validate individual career rules.
- Keep evidence, inference, recommendation, and realised outcome distinct.
- Citation quantity does not validate a verdict.
- Preserve contradictory evidence and known failure modes.

## Source integrity

- Verify scholarly citations against DOI or publisher metadata before adding them.
- Cite a practitioner framework to an exact primary source where possible.
- Distinguish a quotation, paraphrase, and repository interpretation.
- Do not add a famous aphorism from memory and then backfill an academically adjacent citation.
- Keep book-derived modules selective and decision-relevant. Do not reconstruct a copyrighted book chapter by chapter or create a substitute for the source.
- Mark an unverified source or attribution as requiring verification; do not guess.

## Contribution workflow

1. Define the decision problem and the failure in current behaviour.
2. Identify whether the proposed change is direct scholarship, a translation, practitioner-derived, authorial synthesis, or case calibration.
3. Update the Skill's workflow and `references/provenance.md` together.
4. Add or revise a synthetic evaluation case when behaviour changes.
5. Run the official Skill validator and repository checks.
6. Inspect the complete diff for source overclaiming, broken boundaries, and unnecessary context.
7. Commit and publish only after validation succeeds.

Do not add a new reference merely to make an existing rule appear more academic. Change the rule, narrow the claim, or label the design honestly.

## Evaluation rules

Synthetic cases test whether a Skill respects its decision boundary, distinguishes evidence from inference, exposes uncertainty and failure modes, and hands off the next decision correctly. They do not prove predictive accuracy.

Use `Case-calibrated` only after a documented set of comparable real or independently forward-tested cases includes:

- the facts available at decision time;
- the Skill version;
- the recommendation and confidence;
- the mechanism expected to matter;
- the evidence or event that changed the decision;
- execution fidelity;
- realised outcomes and residual assets;
- counterexamples and failure cases.

One success, one failure, or retrospective fit is insufficient.

## Versioning

Use semantic versioning for the repository:

- **Major:** changes a decision boundary, removes or renames a Skill, or makes previous invocation behaviour incompatible.
- **Minor:** adds or materially changes a workflow, module, provenance architecture, or evaluation surface while preserving the three decision boundaries.
- **Patch:** corrects metadata, paths, citations, wording, or formatting without materially changing decisions.

Keep the root `VERSION` file authoritative for the repository release.

## Release gates

A release requires:

1. official validation of every Skill;
2. valid `agents/openai.yaml` metadata and icon paths;
3. resolution of every `references/*.md` route;
4. use of only the closed provenance labels;
5. no stale `evidence-base.md` route;
6. no placeholder citation or unverified attribution presented as fact;
7. evaluation coverage for all three decision boundaries;
8. clean Git status and intentional commit scope;
9. byte-for-byte verification of the published GitHub tree.

## Local installation and rollback

Install all three Skills from the same repository version and under one runtime root where practical. Before replacing an installed copy, move it to a timestamped backup outside Skill discovery roots. Validate installed copies and compare their hashes with the released repository directories.

Automatic updates are intentionally out of scope. A release should be reviewed before it replaces a working local installation.
