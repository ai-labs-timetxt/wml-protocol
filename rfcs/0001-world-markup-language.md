# RFC 0001: World Markup Language

Status: Draft  
Created: 2026-05-01

## Abstract

World Markup Language, or WML, is a proposed machine-readable world protocol for AI agents.

Where HTML describes pages for human browsers, WML describes worlds for AI agents.

A WML world contains entities, states, goals, capabilities, permissions, risks, evidence, hypotheses, and receipts.

WML does not primarily render a human interface. Its purpose is to allow an agent to understand a structured task world, propose actions, collect evidence, and produce verifiable results.

## Motivation

Current LLM ecosystems are still largely text-first and prompt-driven. This resembles the early MUD era of the internet: text commands, text responses, imagined state, and ad hoc interaction.

Many current AI UI approaches generate dashboards, forms, web components, or SaaS wrappers. These are useful, but still human-interface-first.

WML proposes a different direction:

> Instead of asking how AI can use human web pages, ask what kind of document an AI-native browser should read.

## Design goal

WML should help an agent answer:

- What world am I in?
- What entities exist?
- What is the current state?
- What is the goal?
- What capabilities are available?
- Which actions are read-only?
- Which actions require explicit human approval?
- What evidence has been collected?
- Which hypotheses are verified, ruled out, or unknown?
- What receipts prove that actions happened?
- What final report can be justified by evidence?

## Non-goals

WML is not:

- a replacement for HTML
- a visual UI framework
- a React component format
- a prompt template
- a SaaS wrapper
- a guarantee that models will behave correctly
- a requirement to write a specific runtime in a specific language

## Core principle

```text
Model proposes. Runtime or reviewer disposes.
```

The model may plan, interpret, and propose. A runtime, reviewer, second agent, or deterministic validator should verify conformance.

## Minimal world concepts

A WML world should define:

- `world`
- `entities`
- `state`
- `goals`
- `capabilities`
- `permissions`
- `evidence`
- `hypotheses`
- `receipts`

## WML as protocol, not product

WML is not necessarily a software package.

A GitHub repo can act as a WML protocol source. A coding agent can download the repo, read the RFCs and templates, and use WML to structure a real task.

## Hello World, not Hello Page

Traditional HTML Hello World:

```html
<h1>Hello World</h1>
```

WML Hello World:

```text
World contains a task.
Task exposes capabilities.
Agent proposes an action.
Evidence or state changes.
Receipt records what happened.
Goal is verified.
```

## Summary

WML is a world format, not a page format.

```text
HTML describes what a human can see.
WML describes what an agent can understand, investigate, and safely change.
```
