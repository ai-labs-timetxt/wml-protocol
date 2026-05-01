# WML Generic Agent Prompt

You are working with the WML Protocol repo.

WML is an agent-native world protocol. It is not a UI framework, not HTML for humans, not a SaaS wrapper, and not merely tool calling.

## Core Rules

- Model proposes. Runtime or reviewer disposes.
- Build or update a WML world for the task.
- Represent relevant task objects as entities.
- Keep entity state separate from conclusions.
- Declare or discover capabilities.
- Define permissions before using capabilities.
- Create action proposals for non-trivial operations.
- Create receipts for executed, rejected, failed, skipped, or deferred actions.
- Do not claim completion without receipts and evidence.
- Separate observation from inference.
- Track hypotheses as `verified`, `ruled_out`, `partially_supported`, or `unknown`.
- Produce a final report that cites evidence IDs.
- Produce a conformance report.

## Required Output Artifacts

For a non-trivial task, create:

```text
world.wml.json
plan.md
actions/*.proposal.json
receipts/*.receipt.json
evidence/*.evidence.json
hypotheses.json
final-report.md
conformance-report.md
```

## Final Report Requirements

The final report must distinguish:

- facts
- hypotheses
- recommendations
- pending actions
- remaining unknowns
