# WML Protocol

**WML** stands for **World Markup Language**.

WML is an agent-native information protocol for publishing worlds to AI agents. It is not HTML for humans, not Markdown for documents, not a UI framework, not a workflow engine, and not merely tool calling.

> HTML lets servers send pages to human browsers.  
> WML lets sources send worlds to AI agents.

## Why WML

The web is built around human-facing pages. A page may contain valuable information, but it is usually mixed with layout, navigation, styling, scripts, buttons, forms, repeated chrome, hidden state, and visual assumptions.

Agents can read HTML or Markdown, but they often have to reconstruct the useful world first:

1. fetch a page, note, document, or API response
2. remove human UI noise
3. infer entities and relationships
4. distinguish claims from evidence
5. split long content into usable chunks
6. infer what actions are possible
7. infer boundaries around scope, trust, privacy, and permission

WML is intended to remove that adapter step where possible.

```text
human web: source -> HTML page -> browser -> human
agent web: source -> WML world -> agent
```

## What WML Provides

A WML source can publish information so an agent receives:

- entities instead of vague page regions
- claims instead of undifferentiated prose
- evidence instead of unsupported assertions
- relationships instead of generic links
- chunks instead of scroll-oriented pages
- constraints instead of implicit human-only boundaries
- actions instead of visual buttons or forms
- receipts when actions are resolved

WML changes the unit of exchange from a page to a world.

## Existing Knowledge Tools

Tools such as note apps, document stores, wikis, websites, issue trackers, and databases can already hold useful agent context. But they are usually designed for humans first.

WML is a way for those sources to expose the same underlying information as an agent-readable world, without requiring the agent to scrape a page, reverse-engineer a note graph, or reformat content before it can reason over it.

## What This Repo Is

This repo defines the WML standard.

It is intentionally small:

```text
README.md        what WML is and why it exists
SPEC.md          the WML standard
AGENT.md         how an agent should read and produce WML
CONFORMANCE.md   how to judge whether WML content follows the standard
EXAMPLE.wml.json a small WML knowledge world
LICENSE          license terms
```

Domain profiles, examples, templates, and task guides should live in separate repos that conform to WML.

## How Agents Discover WML

WML can be used as plain files, local knowledge, or web responses.

Possible publication patterns include:

- a local `*.wml.json` file
- a repository containing WML files
- a source index such as `/.well-known/wml.json`
- HTTP content negotiation such as `Accept: application/wml+json`
- a WML export from an existing knowledge base or document system

These patterns are not required for version `0.1`; they show the intended direction.

## How Humans Use This Repo

Make this repo readable by an AI agent, then ask the agent to prefer WML when it consumes or produces structured information.

Example:

```text
Read the WML protocol at <path-to-this-repo>.

Use WML as the preferred information format for this task.

When you consume information, prefer WML if available.
When you produce structured information for another agent, produce WML.

Task:
<describe the source, question, or world>
```

## Current Scope

WML starts with one world document.

Future versions may define world indexes, world-to-world links, imported evidence, delegated worlds, and inter-world communication. Until then, a WML document should make its own entities, claims, evidence, relationships, constraints, chunks, actions, and receipts reviewable within one world.
