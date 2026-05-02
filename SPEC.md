# WML Specification

Status: Draft  
Version: 0.1

## 1. Purpose

World Markup Language, or WML, is a machine-readable information protocol for AI agents.

WML exists so a source can publish an agent-readable world: structured information an agent can traverse, reason over, cite, transform, and interact with without first reverse-engineering a human-facing page or note system.

WML does not render a human interface and does not execute a workflow. WML describes what exists, what is claimed, what supports it, how things relate, how content is chunked, what boundaries apply, and what actions are available.

## 2. Core Principle

```text
HTML describes pages for human browsers.
WML describes worlds for AI agents.
```

A WML world is not a visual page. It is an agent-readable information space.

## 3. Source

A source is the publisher or provider of a WML world.

A source may be a website, document system, note collection, repository, database, application, local file set, or agent-generated export.

A source should identify:

- `id`
- `name`
- `url` or local reference when available
- `published_at` or `updated_at` when available
- `worlds` when it publishes more than one world

## 4. Discovery

WML may be discovered through local files, repository paths, source indexes, or HTTP negotiation.

Non-normative examples:

```text
world.wml.json
knowledge-base.wml.json
/.well-known/wml.json
Accept: application/wml+json
```

Version `0.1` does not require a discovery mechanism. It defines the world document shape.

## 5. World

A WML world is the top-level description of an information space.

A world should define:

- `wml_version`
- `world`
- `source`
- `entities`
- `claims`
- `evidence`
- `relationships`
- `chunks`
- `constraints`
- `actions`
- `receipts`

A world must have a stable unique ID and clear scope.

## 6. Entity

An entity is an object the source wants the agent to recognize.

Entities may represent people, organizations, products, documents, notes, events, datasets, files, tasks, services, policies, claims, evidence items, or other meaningful objects.

An entity should include:

- `id`
- `type`
- `name`
- `description`
- `state`
- `source`
- `claim_ids`
- `evidence_ids`

Entities give agents stable referents. Without entities, an agent receives text but must guess what the text is about.

## 7. State

State describes what is currently known about an entity or world.

State should be evidence-backed when it comes from observation, source data, or inspection.

State is not the same as:

- claim
- inference
- hypothesis
- recommendation
- desired future condition

State should cite evidence when possible.

## 8. Claim

A claim is a statement the source asserts, reports, or presents for evaluation.

Claims should include:

- `id`
- `subject_entity`
- `predicate`
- `object`
- `text`
- `source`
- `evidence_ids`
- `confidence`
- `scope`
- `timestamp`

Claims let agents distinguish asserted information from surrounding prose.

## 9. Evidence

Evidence is support for a claim or state value.

Evidence should include:

- `id`
- `source`
- `collection_method`
- `timestamp`
- `related_entity`
- `supports_claims`
- `observation`
- `raw_reference`

Evidence is not the same as a conclusion. A claim may cite evidence; evidence should not merely restate the claim.

## 10. Relationship

A relationship is a typed connection between entities, claims, evidence, chunks, or worlds.

Relationships should include:

- `id`
- `type`
- `from`
- `to`
- `evidence_ids`
- `description`

Common relationship types may include:

- `part_of`
- `about`
- `author_of`
- `derived_from`
- `supports`
- `contradicts`
- `replaces`
- `same_as`
- `next_chunk`
- `previous_chunk`
- `related_to`

Relationships give agents graph-like structure instead of forcing them to infer meaning from links, backlinks, folders, or layout.

## 11. Chunk

A chunk is a bounded unit of content intended for agent consumption.

Chunks should include:

- `id`
- `sequence`
- `title`
- `content`
- `entity_ids`
- `claim_ids`
- `next_chunk`
- `previous_chunk`
- `token_estimate`

Chunks replace scroll-oriented pages and long unstructured notes with explicit content units. A chunk may contain natural language, structured data, or both.

## 12. Constraint

A constraint is a boundary on interpretation, use, scope, privacy, trust, freshness, or action.

Constraints should include:

- `id`
- `type`
- `applies_to`
- `rule`
- `reason`
- `severity`

Common constraint types may include:

- `scope`
- `permission`
- `privacy`
- `usage`
- `freshness`
- `trust`
- `safety`

Humans often infer boundaries from UI and context. Agents need boundaries represented explicitly because they may summarize, cite, cache, transform, combine, delegate, or act on information.

## 13. Action

An action is a machine-readable affordance exposed to an agent.

Actions should include:

- `id`
- `description`
- `target_entity`
- `input_schema`
- `permission_class`
- `expected_result`
- `constraints`

Actions are the WML counterpart to links, buttons, and forms, but they are not visual controls. They describe what an agent may request, propose, or perform.

## 14. Permission

Permission defines whether an action can be used automatically, requires approval, or is denied.

Suggested permission classes:

- `read_only_auto`
- `analysis_auto`
- `draft_only_auto`
- `explicit_user_confirmation`
- `denied_by_default`

Side-effecting actions require approval unless the active permission constraint explicitly allows them.

## 15. Receipt

A receipt records the disposition of an action.

A receipt should include:

- `id`
- `world_id`
- `action_id`
- `status`
- `timestamp`
- `evidence_id`
- `summary`

Receipt status values should include:

- `success`
- `failed`
- `rejected`
- `pending_confirmation`
- `skipped`
- `not_applicable`

An agent must not claim that an action was completed without a receipt or equivalent evidence.

## 16. Profiles

Profiles may define domain-specific entity types, claim predicates, relationship types, evidence sources, constraints, and action conventions.

Profiles must not change the core WML requirement that entities, claims, evidence, relationships, constraints, chunks, actions, and receipts remain reviewable.

Domain profiles should live outside this core protocol repo unless they are being proposed as changes to the WML standard.

## 17. Task Worlds

Some WML worlds may describe an active task. A task world may include goals, hypotheses, final reports, and conformance reports.

These fields are optional because not every WML world is a task. Many WML worlds are published information spaces.

## 18. World Links

The initial WML model assumes one world document.

Future versions may define world indexes, links between worlds, imported evidence, delegated worlds, handoff receipts, reviewer worlds, and inter-world communication. Until such behavior is specified, a WML document should keep its required information reviewable within a single world.
