# Action Proposal

An action proposal is a structured request to use a capability in a world.

The proposal records what the agent wants to do before the action is executed, rejected, skipped, or deferred.

## Suggested Fields

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

## Rule

Non-trivial operations should have action proposals. Side-effecting operations must follow the active permission policy before execution.

An action proposal is not proof that the action happened. A receipt records the disposition of the proposal.
