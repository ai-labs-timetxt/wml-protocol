# RFC 0003: Agent Conformance

Status: Draft  
Created: 2026-05-01

## Abstract

This RFC defines what it means for an agent to be WML-compliant during a task.

WML conformance is especially important for coding agents such as Kiro, Codex, Claude Code, and similar systems.

## Agent conformance goal

A WML-compliant agent should be able to:

1. Read the WML protocol repo.
2. Understand a task world.
3. Create or update `world.wml.json`.
4. Design a task-specific workflow or sub-agent plan.
5. Use capabilities according to permission rules.
6. Produce action proposals before inspections or actions.
7. Produce receipts after inspections or actions.
8. Separate observation, inference, hypothesis, recommendation, and action.
9. Produce a final report based on evidence and receipts.
10. Avoid claiming unsupported facts.

## Agent workflow synthesis

A WML agent may design its own workflow.

It may define roles such as:

- planner
- inspector
- evidence collector
- hypothesis manager
- verifier
- report writer
- risk reviewer

The exact agent architecture does not need to be pre-defined by the human.

The human defines the protocol and boundaries. The agent designs the task workflow inside those boundaries.

## Required output artifacts

For a non-trivial task, the agent should produce:

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

## Conformance principle

A WML-compliant run should be reviewable by another agent or human without relying on the original agent's memory.

## Reviewer model

One agent may perform the task. Another agent may review conformance.

Example:

```text
Kiro = implementer
Codex = reviewer
WML repo = shared rulebook
```

## Non-conforming behavior

The following behaviors are non-conforming:

- claiming an AWS resource was inspected without evidence
- executing mutating AWS actions without explicit approval
- mixing observation and inference
- producing final conclusions that do not cite evidence
- omitting receipts for inspections
- modifying the final state directly without action proposals
- using credentials or profiles not authorized by the user
