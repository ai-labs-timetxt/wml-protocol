# WML Agent Guide

This file describes how an AI agent should maintain WML artifacts when asked to follow WML.

## Required Reading

Before starting a WML-governed task, read:

1. `README.md`
2. `SPEC.md`
3. `AGENT.md`
4. `CONFORMANCE.md`

Then read the human task prompt.

## Operating Rule

Do not treat WML as a prompt template or workflow engine. Treat WML as the world protocol for the task.

The human gives the task. WML defines how the task world is represented, how action proposals are recorded, how evidence is recorded, and how final claims are reviewed.

## Maintaining a WML World

For a non-trivial task, maintain WML artifacts that show:

1. the world ID
2. the goals and success criteria
3. the relevant entities
4. entity state, separate from conclusions
5. available capabilities
6. active permissions
7. action proposals for non-trivial operations
8. receipts for executed, rejected, failed, skipped, or deferred actions
9. observations recorded as evidence
10. hypotheses and their statuses
11. final claims with evidence IDs and receipt IDs
12. a conformance report

## Runtime Independence

WML does not prescribe how work is executed, scheduled, delegated, or orchestrated.

An agent may use any available runtime or tool environment. That execution environment is outside the WML standard.

The WML requirement is that the resulting world remains reviewable: proposed actions, observations, evidence, receipts, hypotheses, and final claims must be represented clearly.

## Human Approval

Side-effecting actions require explicit approval unless the active permission policy says otherwise.

If approval is needed:

1. Create an action proposal.
2. Mark it as requiring confirmation.
3. Ask the human or runtime for approval.
4. Act only after approval.
5. Record the result in a receipt.

## Evidence Discipline

Separate:

- observation: what was seen
- inference: what the observation may mean
- hypothesis: a claim under evaluation
- recommendation: what should happen next
- receipt: what happened to a proposed action

Do not claim completion without receipts. Do not claim facts without evidence.

## Output Artifacts

A WML-governed run should produce records equivalent to:

```text
world.wml.json
actions/*.proposal.json
receipts/*.receipt.json
evidence/*.evidence.json
hypotheses.json
final-report.md
conformance-report.md
```

The exact file layout may vary, but the information must be present and reviewable.

## Default Scope

Unless the human says otherwise, keep the task inside one WML world.

Future WML versions may define world-to-world communication. Until then, do not invent cross-world behavior as if it were part of the standard.
