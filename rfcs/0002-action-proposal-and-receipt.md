# RFC 0002: Action Proposal and Receipt

Status: Draft  
Created: 2026-05-01

## Abstract

This RFC defines two central WML concepts:

- `action_proposal`
- `receipt`

An agent should propose actions. It should not directly claim that the world changed.

A receipt is the evidence that an action was executed, inspected, rejected, or deferred.

## Action proposal

An action proposal is a structured request by an agent to use a capability.

Example:

```json
{
  "type": "action_proposal",
  "world_id": "aws-cloudfront-403-case",
  "goal_id": "identify_root_cause",
  "target_entity": "cloudfront_distribution",
  "capability_id": "inspect_distribution_config",
  "permission_class": "read_only_auto",
  "arguments": {
    "distribution_id": "EXAMPLE123",
    "aws_profile": "prod"
  }
}
```

## Required fields

An action proposal should include:

- `type`
- `world_id`
- `goal_id`
- `target_entity`
- `capability_id`
- `permission_class`
- `arguments`

## Receipt

A receipt records what happened after an action proposal.

Example:

```json
{
  "type": "receipt",
  "world_id": "aws-cloudfront-403-case",
  "action_proposal_id": "ap_001",
  "status": "success",
  "permission_class": "read_only_auto",
  "evidence_id": "ev_cloudfront_config_001",
  "summary": "CloudFront distribution config was retrieved successfully.",
  "timestamp": "2026-05-01T00:00:00Z"
}
```

## Receipt status

Suggested statuses:

- `success`
- `failed`
- `rejected`
- `pending_user_confirmation`
- `skipped`
- `not_applicable`

## Important rule

An agent must not claim success without a receipt or evidence reference.

Bad:

```text
I checked the distribution and found the issue.
```

Good:

```text
Receipt r_001 confirms that the distribution config was inspected.
Evidence ev_001 shows that the origin uses an S3 bucket with OAC enabled.
```

## Mutating actions

Mutating actions must not be auto-executed unless explicitly approved.

Examples of mutating AWS actions:

- update CloudFront distribution
- update S3 bucket policy
- change IAM policy
- create invalidation
- modify WAF rules
- change Route 53 record
- delete or replace infrastructure

For these actions, an agent may create an action proposal but must mark it as requiring explicit human approval.
