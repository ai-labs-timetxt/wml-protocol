# AWS CLI Capabilities

AWS CLI/API operations can be represented as WML capabilities.

## Read-Only Capabilities

Read-only commands may use `read_only_aws_auto` when the user has authorized the AWS profile and task scope.

Examples:

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

Each inspection should still have:

- an action proposal
- a receipt
- evidence derived from output or documented failure

## Mutating Capabilities

Mutating commands must use `aws_mutating_requires_human_approval` or `aws_dangerous_denied_by_default`.

Examples:

```text
aws cloudfront update-distribution
aws cloudfront create-invalidation
aws s3api put-bucket-policy
aws wafv2 update-web-acl
aws route53 change-resource-record-sets
aws iam put-role-policy
aws iam attach-role-policy
```

The agent may draft proposals for these actions, but must not execute them without explicit approval.
