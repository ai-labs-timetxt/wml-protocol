# RFC 0101: WML AWS Extension

Status: Draft  
Created: 2026-05-01

## Abstract

The WML AWS Extension maps WML core concepts onto AWS troubleshooting and review tasks.

AWS environments are highly text-structured, API-driven, and evidence-rich. AWS resources, policies, configurations, events, logs, and CLI outputs can be represented as WML entities, states, evidence, hypotheses, capabilities, action proposals, and receipts.

## Why AWS Fits WML

AWS is not the definition of WML, but it is a strong first extension because many AWS task worlds can be inspected through structured data:

- IAM policy JSON
- S3 bucket policy JSON
- CloudFormation templates
- Terraform state and plans
- CloudTrail event JSON
- CloudWatch logs
- CloudFront distribution config
- WAF web ACL JSON
- Route 53 records
- ECS task definitions
- Lambda configuration
- AWS Config timelines

These artifacts are naturally suited for evidence-backed agent workflows.

## AWS Resources as WML Entities

AWS resources should be represented as WML entities. Common entity types include:

- account
- profile
- region
- service
- resource
- policy
- log_group
- event
- configuration
- alarm
- hypothesis
- evidence_item

An entity state should record observed values, not final conclusions. Conclusions belong in hypotheses, recommendations, or final reports.

## AWS Capabilities

AWS CLI/API read-only commands may be modeled as capabilities when the user has authorized the profile and scope.

Read-only examples:

```text
aws cloudfront get-distribution
aws cloudfront get-distribution-config
aws cloudfront list-distributions
aws s3api get-bucket-policy
aws s3api get-bucket-location
aws wafv2 get-web-acl
aws logs filter-log-events
aws cloudtrail lookup-events
```

## AWS Evidence

AWS policies, configurations, events, logs, and command outputs may be evidence when they are collected with a receipt and tied to an action proposal.

Evidence should avoid exposing credentials, secrets, tokens, or unnecessary personally identifiable information.

## AWS Permission Model

Suggested AWS permission classes:

```text
read_only_aws_auto
local_aws_config_read_auto
analysis_auto
draft_only_auto
aws_mutating_requires_human_approval
aws_dangerous_denied_by_default
```

Mutating examples that require explicit human approval:

```text
aws cloudfront update-distribution
aws cloudfront create-invalidation
aws s3api put-bucket-policy
aws wafv2 update-web-acl
aws route53 change-resource-record-sets
aws iam put-role-policy
aws iam attach-role-policy
```

## AWS Profile Usage

An AWS WML run should document the authorized profile and where profile configuration is expected:

```text
~/.aws/config
~/.aws/credentials
```

The agent must not use a different AWS profile, account, or role unless the user explicitly authorizes it.

## AWS Troubleshooting Lifecycle

A WML AWS troubleshooting task should follow this lifecycle:

1. Build a task world.
2. Identify AWS entities.
3. Identify initial hypotheses.
4. Define read-only AWS capabilities.
5. Generate an inspection plan.
6. Produce action proposals.
7. Execute authorized read-only inspections.
8. Store evidence.
9. Emit receipts.
10. Update hypothesis status.
11. Produce a final report.
12. Express fixes as pending actions requiring approval.

## First Playbook

CloudFront 403 troubleshooting is the first AWS playbook because:

- the symptom is clear
- likely causes are bounded
- evidence sources are structured
- many inspections are read-only
- fixes often require explicit approval
- the final report is easy to review

See [playbooks/aws/cloudfront-403/README.md](../../../playbooks/aws/cloudfront-403/README.md).
