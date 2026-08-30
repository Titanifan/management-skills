# Opportunity Ledger Memory Policy

## Purpose

Maintain one stable state record per opportunity so the Orchestrator can update a judgement when evidence changes. The ledger is not a CRM, source repository, contact database, or substitute for meeting notes, contracts, or agreements.

## Record identity

- Create one stable human-readable `opportunity_id` per distinct opportunity.
- Reuse the same record when the opportunity changes state.
- Split a record only when one relationship produces genuinely distinct problems, owners, governance, or resource decisions. Link the new records in a transition note.
- Do not merge opportunities merely because they involve the same organisation.

## Evidence versioning

- Start `evidence_version` at `1` when the first material evidence record is created.
- Increase it by exactly one when material evidence is added, corrected, or superseded.
- Do not increment for formatting, restatement, repeated discussion, or a decision made from an unchanged evidence set.
- Every judgement must state which evidence version it used.

## Evidence discipline

- Keep documented evidence, inference, missing evidence, and material claims needing verification separate.
- Never promote an inference because it appears in memory or has been repeated.
- Preserve contradictory evidence as separate entries. Do not silently reconcile it.
- Verify unstable current facts before relying on them and record the verification date where practical.
- A VERIFY sidecar may add material evidence without changing lifecycle state. Increment the evidence version only when evidence actually changes.

## State history

- Keep `transition_log` append-only.
- Record `from`, `to`, date, evidence version, transition evidence, decision, and provenance.
- A no-transition review may be logged when it materially confirms or weakens the current state.
- Never delete or rewrite an earlier transition to make the history appear linear.

## Memory minimisation and confidentiality

- Store only the minimum durable summary needed for later routing.
- Do not store confidential source content, credentials, private contact details, unpublished sensitive documents, or verbatim restricted notes.
- When confidential evidence matters, store an appropriate summary plus access restriction and provenance.
- If suitable summarisation is not possible, record only that restricted evidence exists and where the authorised user can retrieve it.
- Preserve ownership, attribution, IP, publication, conflict, ethics, institutional, and access constraints.

## Update protocol

After each material turn:

1. identify the stable opportunity record;
2. decide whether evidence changed and increment the version only when warranted;
3. update evidence, inference, gaps, and verification fields separately;
4. update lifecycle state only when transition evidence warrants it;
5. append the transition record rather than rewriting history;
6. set the next evidence action and stop or downgrade rule;
7. update `updated_at` in ISO-8601 format.

When persistent memory is unavailable, use the ledger schema as a user-controlled record and apply the same rules.
