# State

State describes what is currently known about an entity or world.

State should include observations and values that can be reviewed, refreshed, or linked to evidence.

State is not the same as:

- inference
- hypothesis
- recommendation
- desired future condition
- final conclusion

Entity state should cite evidence when the value comes from an inspection or observation.

## Suggested Fields

- `id`
- `entity_id`
- `value`
- `source`
- `evidence_id`
- `observed_at`
- `confidence`

## Rule

An agent should update state only through evidence-backed observation or through a receipt for an approved action.
