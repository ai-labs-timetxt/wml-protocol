# WML AWS Permission Policy

This policy extends WML core permission classes for AWS tasks.

## Auto-Allowed When Authorized

These classes may be automatic when the user has authorized the AWS profile and task scope:

- `read_only_aws_auto`: read-only AWS CLI/API inspections.
- `local_aws_config_read_auto`: reading local AWS profile names and non-secret configuration needed to select the authorized context.
- `analysis_auto`: interpreting collected evidence.
- `draft_only_auto`: drafting reports, action proposals, and recommendations.

## Approval Required

Use `aws_mutating_requires_human_approval` for any action that changes AWS state, creates side effects, invalidates cache, changes routing, changes permissions, restarts services, deploys infrastructure, or writes configuration.

Examples:

- updating IAM policies or role attachments
- updating S3 bucket policy or access settings
- updating CloudFront distributions
- creating CloudFront invalidations
- updating WAF rules
- changing Route 53 records
- deleting, replacing, or recreating AWS resources

## Denied by Default

Use `aws_dangerous_denied_by_default` for destructive or broad actions unless the user provides explicit, narrow authorization.

The agent should still produce a proposal explaining the risk instead of executing the action.
