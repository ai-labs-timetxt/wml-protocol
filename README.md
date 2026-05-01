# WML Protocol

**WML** stands for **World Markup Language**.

WML is an agent-native world protocol. It is not a UI framework, not HTML for humans, not a SaaS wrapper, and not merely tool calling.

The core idea:

> HTML describes pages for human browsers.  
> WML describes worlds for AI agents.

WML exists to help agents understand a task world, design a compliant workflow, distinguish observation from inference, follow permission boundaries, produce evidence, and emit receipts.

## Core mottos

> Model proposes. Runtime or reviewer disposes.

> Hello World, not Hello Page.

## What this repo is

This repo is a protocol-first, code-free draft.

It contains:

- RFC drafts
- Core protocol concepts
- Agent conformance rules
- AWS troubleshooting playbooks
- CloudFront 403 templates
- Prompts for Kiro, Codex, and Claude Code

The intended usage is simple:

1. Give this repo URL to a coding agent.
2. Ask the agent to read and follow WML.
3. Give the agent a real task, such as AWS CloudFront 403 troubleshooting.
4. The agent should create a WML world, design the required workflow, collect evidence, produce receipts, and generate a final report.
5. A second agent or human reviewer can check WML conformance.

## What WML is for

WML is most useful when a task has:

- state
- tools
- permissions
- consequences
- evidence
- hypotheses
- long-running steps
- audit requirements
- multi-agent handoff

Examples:

- AWS troubleshooting
- DevOps incident investigation
- security review
- infrastructure audit
- technical research with evidence
- multi-agent workflow design

## Recommended first real-world use case

**WML for AWS CloudFront 403 Troubleshooting**

AWS is a strong fit for WML because AWS resources, configurations, logs, policies, events, and CLI outputs are highly text-structured.

The agent can use a local AWS profile from:

```text
~/.aws/config
~/.aws/credentials
```

Read-only AWS inspections may be treated as `auto` capabilities. Mutating actions must require explicit human approval.

## Minimal usage prompt

```text
Download and read this WML protocol repo.

Follow the WML protocol strictly.

Task:
Troubleshoot a CloudFront 403 issue in my AWS account.

AWS access:
Use local AWS profile: <profile-name>
Profile is configured in ~/.aws/config and ~/.aws/credentials.

Target:
CloudFront distribution ID: <distribution-id>
Symptom:
Viewer receives HTTP 403.

Rules:
1. Build a WML world for this troubleshooting case.
2. Treat AWS resources as WML entities.
3. Treat AWS CLI read-only commands as auto capabilities.
4. Do not make any configuration changes.
5. Do not modify IAM, S3 bucket policy, CloudFront distribution, WAF, Route 53, or cache invalidation without explicit approval.
6. Every inspection must produce a receipt.
7. Every conclusion must be backed by evidence.
8. Produce a final troubleshooting report with symptom, inspected resources, evidence, ruled-out hypotheses, likely root cause, recommended fix, and actions requiring approval.
```

## Repository structure

```text
rfcs/
  0001-world-markup-language.md
  0002-action-proposal-and-receipt.md
  0003-agent-conformance.md
  0004-wml-for-aws-troubleshooting.md

protocols/core/
  world.md
  entity.md
  capability.md
  permission.md
  evidence.md
  receipt.md
  hypothesis.md

playbooks/aws/
  cloudfront-403.md

templates/aws-cloudfront-403/
  world.wml.json
  action-proposal.template.json
  receipt.template.json
  evidence.template.json
  hypothesis.template.json
  final-report.template.md

prompts/
  kiro/cloudfront-403-agent.md
  codex/cloudfront-403-agent.md
  claude-code/cloudfront-403-agent.md

conformance/
  rules.md
  checklist.md
  reviewer-prompt.md
```
