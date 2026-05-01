# WML Agent Guide

This file describes how an AI agent should operate when asked to follow WML.

## Required Reading

Before starting a WML-governed task, read:

1. `README.md`
2. `SPEC.md`
3. `AGENT.md`
4. `CONFORMANCE.md`

Then read the human task prompt.

## Operating Rule

Do not treat WML as a prompt template. Treat WML as the world protocol for the task.

The human gives the task. WML defines how the task world is represented, how actions are proposed, how evidence is recorded, and how the final output is reviewed.

## Task Lifecycle

For a non-trivial task:

1. Create or update a WML world.
2. Assign a unique world ID.
3. Declare goals and success criteria.
4. Identify relevant entities.
5. Separate entity state from conclusions.
6. Declare or discover capabilities.
7. Define permissions.
8. Create action proposals for non-trivial operations.
9. Execute only actions allowed by the active permission policy.
10. Create receipts for executed, rejected, failed, skipped, or deferred actions.
11. Convert observations into evidence.
12. Track hypotheses and update their statuses.
13. Produce a final report citing evidence IDs and receipt IDs.
14. Produce a conformance report.

## Tools and Runtimes

WML does not prescribe how work is executed.

An agent may use:

- direct tool calls
- local commands
- external tool servers
- sub-agents
- reviewer agents
- harness workflows
- generated task-specific agents
- other runtime mechanisms available in the environment

The execution method is valid only if the resulting run remains WML-conformant.

## Human Approval

Side-effecting actions require explicit approval unless the active permission policy says otherwise.

If approval is needed:

1. Create an action proposal.
2. Mark it as requiring confirmation.
3. Ask the human or runtime for approval.
4. Execute only after approval.
5. Record the result in a receipt.

## Evidence Discipline

Separate:

- observation: what was seen
- inference: what the observation may mean
- hypothesis: a claim under evaluation
- recommendation: what should happen next
- action: what was actually done

Do not claim completion without receipts. Do not claim facts without evidence.

## Output Artifacts

A WML-governed run should produce artifacts equivalent to:

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
