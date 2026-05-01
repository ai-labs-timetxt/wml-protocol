# WML Protocol

**WML** stands for **World Markup Language**.

WML is an agent-native world protocol. It is not HTML for humans, not a UI framework, not a SaaS wrapper, and not merely tool calling.

> HTML describes pages for human browsers.  
> WML describes worlds for AI agents.

WML gives AI agents a shared way to describe a task world: entities, state, goals, capabilities, permissions, action proposals, evidence, hypotheses, receipts, and final reports.

The model proposes. A runtime, reviewer, validator, or human disposes.

## What This Repo Is

This repo defines the WML standard.

It is intentionally small:

```text
README.md        what this is and how humans give it to agents
SPEC.md          the WML standard
AGENT.md         how an agent should operate in a WML world
CONFORMANCE.md   how to judge whether a run followed WML
EXAMPLE.wml.json a minimal WML world
LICENSE          license terms
```

This repo does not define domain-specific procedures. Domain profiles, examples, templates, and task guides should live in separate repos that conform to WML.

## How Humans Use WML With Agents

Make this repo readable by the AI agent. Common options:

- open this repo as the agent's project or working context
- place this repo in an agent-readable skills, knowledge, or reference directory
- reference the local path to this repo in the task prompt
- paste the relevant WML files into the agent session when persistent files are not available

Then give the agent a human task prompt and tell it to follow WML.

Example:

```text
Read the WML protocol at <path-to-this-repo>.

Use WML as the governing protocol for this task.

First read:
- README.md
- SPEC.md
- AGENT.md
- CONFORMANCE.md

Create a WML world for the task, maintain that world as the task progresses, and produce WML-conformant outputs.

Task:
<describe the task>
```

## What WML Describes

WML describes:

- the world an agent is operating in
- the objects that exist in that world
- what is currently known about those objects
- what the agent is trying to accomplish
- what capabilities are available
- what permissions constrain those capabilities
- what actions were proposed
- what observations became evidence
- what hypotheses are under consideration
- what receipts show about proposed actions
- what final claims are justified

WML does not schedule, execute, or orchestrate the task. An agent may use any execution mechanism available in its environment. WML is the shared description of the world and the reviewable record of what happened in that world.

## Current Scope

WML starts with one task inside one WML world.

Future versions may define how WML worlds link, delegate, import evidence, and communicate with each other. Until then, a WML run should keep all required task artifacts in one world unless the human explicitly defines a larger structure.
