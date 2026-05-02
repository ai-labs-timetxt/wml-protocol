# WML Agent Guide

This file describes how an AI agent should read and produce WML.

## Required Reading

Before using WML, read:

1. `README.md`
2. `SPEC.md`
3. `AGENT.md`
4. `CONFORMANCE.md`

Then read the human prompt or source-specific instructions.

## Operating Rule

Do not treat WML as a prompt template, page format, note format, or workflow engine. Treat WML as the agent-preferred representation of an information world.

When consuming information, prefer WML over human-oriented page, note, or document formats when WML is available.

When producing information for another agent, produce WML when structured exchange is useful.

## Finding WML

If a source may expose WML, look for explicit WML documents or source indexes when available.

Examples:

```text
*.wml.json
world.wml.json
/.well-known/wml.json
Accept: application/wml+json
```

Do not assume every source supports WML. If WML is not available, use the best available source and, when useful, convert the consumed information into WML for downstream agent use.

## Reading WML

When reading a WML world, identify:

1. the source
2. the world ID and scope
3. the entities the source wants recognized
4. claims made about those entities
5. evidence supporting those claims
6. relationships between entities, claims, evidence, and chunks
7. constraints on interpretation, use, privacy, trust, freshness, and action
8. chunks and their continuation order
9. actions the source exposes
10. receipts for actions already resolved

Do not treat all text as equally authoritative. Claims, evidence, relationships, and constraints have different roles.

## Producing WML

When producing WML, prefer explicit structure over prose-only output.

Represent:

- important objects as `entities`
- asserted statements as `claims`
- support for claims as `evidence`
- typed connections as `relationships`
- long content as ordered `chunks`
- boundaries as `constraints`
- available affordances as `actions`
- action outcomes as `receipts`

A WML document may still include natural language. The difference is that important information should have stable IDs and machine-readable structure.

## Converting Human-Oriented Sources

When converting a page, note, document, or knowledge base into WML:

1. preserve source references
2. identify stable entities
3. convert assertions into claims
4. keep evidence separate from claims
5. represent meaningful links as typed relationships
6. split long content into chunks
7. preserve boundaries such as freshness, privacy, trust, and scope
8. expose actions only when the source or human authorizes them

The goal is not to make prettier text. The goal is to expose the underlying information world in an agent-native form.

## Acting From WML

WML does not prescribe how work is executed, scheduled, delegated, or orchestrated.

If a WML world exposes actions, follow the action's constraints and permission class. Side-effecting actions require explicit approval unless a permission constraint says otherwise.

If an action is completed, rejected, skipped, or fails, record or expect a receipt.

## Default Scope

Unless the source says otherwise, treat one WML document as one world.

Future WML versions may define world-to-world communication. Until then, do not invent cross-world behavior as if it were part of the standard.
