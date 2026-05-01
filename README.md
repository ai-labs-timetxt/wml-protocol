# WML Protocol

**WML** stands for **World Markup Language**.

WML is an agent-native world protocol. It is not HTML for humans, not a UI framework, not a SaaS wrapper, and not merely tool calling.

> HTML describes pages for human browsers.  
> WML describes worlds for AI agents.

WML helps agents represent task worlds, entities, state, capabilities, permissions, action proposals, evidence, hypotheses, receipts, and final reports. The model proposes; a runtime, reviewer, validator, or human disposes.

## Three Layers

This repo separates WML into three layers:

1. **Core Protocol**: domain-neutral WML concepts and conformance rules.
2. **Domain Extensions**: mappings from WML concepts into a specific environment.
3. **Use-case Playbooks**: concrete task guides, templates, prompts, and report structures built on core plus one or more extensions.

Core WML should be useful across troubleshooting, research, security review, infrastructure audit, long-running task execution, and multi-agent handoff. Domain extensions and playbooks make those generic concepts practical for specific worlds.

## What This Repo Is

This repo is a protocol-first, code-free draft.

It contains:

- core RFC drafts
- core protocol concept documents
- domain extension drafts
- conformance checklists and reviewer prompts
- use-case playbooks and templates
- generic and domain-specific agent prompts

It does not contain a runtime, SDK, Python implementation, or execution framework.

## Core Positioning

> Model proposes. Runtime or reviewer disposes.

> Hello World, not Hello Page.

A WML-compliant agent should:

1. Read the shared protocol.
2. Build or update a task world.
3. Represent relevant task objects as entities.
4. Declare goals, state, capabilities, and permissions.
5. Propose non-trivial actions before execution.
6. Record receipts after execution, rejection, failure, or deferral.
7. Store evidence separately from inference.
8. Track hypotheses by status.
9. Produce a final report that cites evidence and receipts.
10. Produce a conformance report that another agent or human can review.

## Repository Structure

```text
rfcs/
  core/
    0001-world-markup-language.md
    0002-action-proposal-and-receipt.md
    0003-agent-conformance.md
  extensions/
    aws/
      0101-wml-aws-extension.md

protocols/
  core/
    world.md
    entity.md
    state.md
    capability.md
    permission.md
    action-proposal.md
    receipt.md
    evidence.md
    hypothesis.md

conformance/
  core/
    checklist.md
    rules.md
    reviewer-prompt.md
  extensions/
    aws/
      checklist.md
      permission-policy.md
      reviewer-prompt.md

extensions/
  aws/
    README.md
    concepts.md
    permission-classes.md
    resource-entity-mapping.md
    aws-cli-capabilities.md

playbooks/
  aws/
    cloudfront-403/
      README.md
      world.template.wml.json
      action-proposal.template.json
      receipt.template.json
      evidence.template.json
      hypothesis.template.json
      final-report.template.md
      agent-prompt.md

prompts/
  generic/
    wml-agent.md
    wml-reviewer.md
  aws/
    cloudfront-403-agent.md

examples/
  hello-world/
    world.wml.json
  aws/
    cloudfront-403/
      README.md
```

## Starting Points

- Core protocol: [rfcs/core/0001-world-markup-language.md](rfcs/core/0001-world-markup-language.md)
- Action proposals and receipts: [rfcs/core/0002-action-proposal-and-receipt.md](rfcs/core/0002-action-proposal-and-receipt.md)
- Agent conformance: [rfcs/core/0003-agent-conformance.md](rfcs/core/0003-agent-conformance.md)
- Core checklist: [conformance/core/checklist.md](conformance/core/checklist.md)
- Generic agent prompt: [prompts/generic/wml-agent.md](prompts/generic/wml-agent.md)

## First Domain Extension

The first concrete extension is AWS:

- AWS extension RFC: [rfcs/extensions/aws/0101-wml-aws-extension.md](rfcs/extensions/aws/0101-wml-aws-extension.md)
- AWS extension guide: [extensions/aws/README.md](extensions/aws/README.md)
- AWS conformance checklist: [conformance/extensions/aws/checklist.md](conformance/extensions/aws/checklist.md)
- CloudFront 403 playbook: [playbooks/aws/cloudfront-403/README.md](playbooks/aws/cloudfront-403/README.md)
- CloudFront 403 agent prompt: [prompts/aws/cloudfront-403-agent.md](prompts/aws/cloudfront-403-agent.md)

AWS troubleshooting is a strong use case for WML because resources, configuration, policies, logs, events, and CLI outputs are structured and evidence-rich. AWS is an example extension, not the definition of WML.

## Minimal Generic Usage Prompt

```text
Download and read this WML protocol repo.

Follow the WML protocol strictly.

Task:
<describe the task world and goal>

Rules:
1. Build or update a WML world for this task.
2. Represent relevant task objects as WML entities.
3. Declare capabilities and permissions before using them.
4. Create action proposals for non-trivial operations.
5. Create receipts for executed, rejected, failed, or deferred actions.
6. Separate observation from inference.
7. Back findings with evidence IDs.
8. Track hypotheses as verified, ruled_out, partially_supported, or unknown.
9. Do not claim completion without receipts and evidence.
10. Produce a final report and conformance report.
```
