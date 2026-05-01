# WML Specification

Status: Draft  
Version: 0.1

## 1. Purpose

World Markup Language, or WML, is a machine-readable world protocol for AI agents.

WML exists so an agent can understand a task world, reason about what is allowed, propose actions, collect evidence, record receipts, track hypotheses, and produce reviewable results.

WML does not render a human interface. WML describes what an agent can understand, investigate, and safely change.

## 2. Core Principle

```text
Model proposes. Runtime or reviewer disposes.
```

An agent may plan, interpret, and propose. A runtime, reviewer, validator, or human should be able to verify what happened from WML artifacts.

## 3. World

A WML world is the top-level task environment.

A world should define:

- `wml_version`
- `world`
- `goals`
- `entities`
- `capabilities`
- `permissions`
- `action_proposals`
- `receipts`
- `evidence`
- `hypotheses`
- `final_report`

A world must have a stable unique ID.

## 4. Entity

An entity is an object inside a WML world.

Entities may represent people, tasks, resources, documents, services, policies, configurations, evidence items, hypotheses, reports, or other task-relevant objects.

An entity should include:

- `id`
- `type`
- `description`
- `state`
- `capabilities`
- `evidence_ids`

Entity state must be separate from conclusions, recommendations, and hypotheses.

## 5. State

State describes what is currently known about an entity or world.

State should be evidence-backed when it comes from observation or inspection.

State is not the same as:

- inference
- hypothesis
- recommendation
- desired future condition
- final conclusion

An agent should update state only through evidence-backed observation or through a receipt for an approved action.

## 6. Goal

A goal describes what the WML run is trying to accomplish.

A goal should include:

- `id`
- `description`
- `status`
- `success_criteria`
- `evidence_ids`

Goal status values should include:

- `unknown`
- `in_progress`
- `satisfied`
- `blocked`
- `abandoned`

## 7. Capability

A capability is something an agent may propose to do.

A capability should include:

- `id`
- `description`
- `target_entity`
- `input_requirements`
- `permission_class`
- `expected_evidence`
- `expected_effect`
- `risk`

The agent should produce an action proposal before using a non-trivial capability.

## 8. Permission

Permission defines whether a capability can be used automatically, requires approval, or is denied.

Suggested permission classes:

- `read_only_auto`
- `local_file_read_auto`
- `analysis_auto`
- `draft_only_auto`
- `explicit_user_confirmation`
- `dangerous_denied_by_default`

Side-effecting actions require approval unless the active permission policy explicitly allows them.

## 9. Action Proposal

An action proposal is a structured request to use a capability.

An action proposal should include:

- `id`
- `world_id`
- `goal_id`
- `target_entity`
- `capability_id`
- `permission_class`
- `arguments`
- `expected_evidence`
- `expected_effect`
- `risk`

An action proposal is not proof that an action happened.

## 10. Receipt

A receipt records the disposition of an action proposal.

A receipt should include:

- `id`
- `world_id`
- `action_proposal_id`
- `status`
- `permission_class`
- `timestamp`
- `evidence_id`
- `summary`

Receipt status values should include:

- `success`
- `failed`
- `rejected`
- `pending_user_confirmation`
- `skipped`
- `not_applicable`

An agent must not claim that an action was executed without a receipt.

## 11. Evidence

Evidence is an observed fact or artifact.

Evidence should include:

- `id`
- `world_id`
- `source`
- `collection_method`
- `timestamp`
- `related_entity`
- `observation`
- `raw_reference`
- `supports_hypotheses`
- `rules_out_hypotheses`

Evidence is not the same as inference. An agent must not cite a conclusion as evidence.

## 12. Hypothesis

A hypothesis is a possible explanation or claim under evaluation.

A hypothesis should include:

- `id`
- `claim`
- `status`
- `evidence_ids`
- `notes`

Hypothesis status values should include:

- `unknown`
- `investigating`
- `verified`
- `ruled_out`
- `partially_supported`

## 13. Final Report

A final report summarizes the run in human-readable form.

The final report must distinguish:

- facts
- hypotheses
- recommendations
- pending actions
- remaining unknowns

The final report must cite evidence IDs for factual claims and receipt IDs for completed actions.

## 14. Conformance Report

A conformance report records whether the run followed WML.

The report should identify:

- satisfied conformance checks
- missing artifacts
- unsupported claims
- missing receipts
- permission violations
- remaining review risks

## 15. Extensions

Domain extensions may define domain-specific entity types, permission classes, evidence sources, capability conventions, and playbooks.

Extensions must not change the core WML requirement that actions, evidence, state, hypotheses, receipts, and final reports remain reviewable.

Domain extensions should live outside this core protocol repo unless they are being proposed as changes to the WML standard.

## 16. World Links

The initial WML model assumes one task world.

Future versions may define links between worlds, delegated goals, imported evidence, handoff receipts, reviewer worlds, and inter-world communication. Until such behavior is specified, a WML run should keep the task inside a single world unless the human explicitly defines otherwise.
