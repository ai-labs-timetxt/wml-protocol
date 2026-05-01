# WML Core Conformance Rules

A WML run is compliant only if the following domain-neutral rules are followed.

## Core Rules

1. The agent must create or update a WML world.
2. The agent must identify entities, goals, state, capabilities, permissions, evidence, hypotheses, action proposals, and receipts.
3. The agent must keep entity state separate from conclusions and recommendations.
4. The agent must not claim success or completion without evidence and receipts.
5. The agent must not claim that an action was executed without a receipt.
6. The agent must separate observation from inference.
7. The agent must cite evidence for final conclusions.
8. The agent must not execute side-effecting actions without approval unless the active permission policy explicitly allows them.
9. The agent must express unapproved recommended fixes or next steps as pending actions.
10. The agent must produce a conformance report.
11. The run must be reviewable by another agent, human, validator, or runtime without relying on the original agent's memory.

## Non-Conforming Behavior

The following behaviors are non-conforming:

- claiming an entity was inspected without evidence
- claiming an action was executed without a receipt
- mixing observation and inference
- producing final conclusions that do not cite evidence
- omitting receipts for non-trivial operations
- modifying state directly without an action proposal and receipt
- executing side-effecting actions outside the active permission policy
- treating a hypothesis as fact before it is verified by evidence
