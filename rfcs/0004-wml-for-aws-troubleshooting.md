# RFC 0004: WML for AWS Troubleshooting

Status: Draft  
Created: 2026-05-01

## Abstract

AWS troubleshooting is a strong use case for WML because AWS environments are highly text-structured, API-driven, and evidence-rich.

AWS resources, policies, configurations, events, logs, and CLI outputs can be represented as WML entities, states, evidence, hypotheses, and receipts.

## Why AWS fits WML

AWS is not literally 100% pure text, but it is highly text-representable.

Examples:

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

These are naturally suited for WML.

## Permission model

Suggested AWS permission classes:

```text
read_only_auto
local_file_read_auto
analysis_auto
draft_only_auto
mutating_requires_human_approval
dangerous_denied_by_default
```

## Read-only examples

These may usually be treated as `read_only_auto` if the user grants AWS profile access:

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

## Mutating examples

These require explicit human approval:

```text
aws cloudfront update-distribution
aws cloudfront create-invalidation
aws s3api put-bucket-policy
aws wafv2 update-web-acl
aws route53 change-resource-record-sets
aws iam put-role-policy
aws iam attach-role-policy
```

## WML troubleshooting lifecycle

A WML AWS troubleshooting task should follow this lifecycle:

1. Build a task world.
2. Identify entities.
3. Identify initial hypotheses.
4. Define read-only capabilities.
5. Generate an inspection plan.
6. Produce action proposals.
7. Execute read-only inspections only.
8. Store evidence.
9. Emit receipts.
10. Update hypothesis status.
11. Produce a final report.
12. Express fixes as pending actions requiring approval.

## CloudFront 403 as first use case

CloudFront 403 is an ideal first scenario because:

- symptom is clear
- likely causes are bounded
- evidence sources are structured
- many inspections are read-only
- fixes often require explicit approval
- final report is easy to review

Common hypothesis set:

- S3 bucket policy denies CloudFront OAC/OAI
- OAC/OAI misconfigured
- WAF blocks request
- geo restriction blocks request
- signed URL or signed cookie required
- origin returns 403
- behavior path pattern mismatch
- viewer protocol policy or method mismatch
- custom error response masks origin behavior

## Final report requirement

The final report must separate:

- symptom
- inspected resources
- evidence
- ruled-out hypotheses
- unknowns
- likely root cause
- recommended fix
- actions requiring approval
