# AWS Playbook: CloudFront 403 Troubleshooting

This playbook applies WML core plus the AWS extension to investigate CloudFront HTTP 403 responses.

## Goal

Identify the likely root cause of a CloudFront HTTP 403 response using evidence-backed WML artifacts.

## Required Inputs

- AWS profile name
- CloudFront distribution ID
- symptom description
- sample URL if available
- approximate time range if logs are involved
- relevant viewer request details if available, such as host, path, method, and source location

## Initial Hypotheses

- S3 bucket policy denies CloudFront access.
- OAC/OAI is misconfigured.
- WAF blocks the request.
- Geo restriction blocks the request.
- Signed URL or signed cookie is required.
- Origin itself returns 403.
- Behavior path pattern mismatch routes the request to the wrong origin.
- Viewer request method is not allowed.
- Custom error response masks origin behavior.
- Origin access control and bucket ownership settings are inconsistent.

## Suggested Read-Only Inspections

The agent may use equivalent AWS CLI/API commands within the authorized profile and task scope.

```text
aws cloudfront get-distribution --id <distribution-id> --profile <profile>
aws cloudfront get-distribution-config --id <distribution-id> --profile <profile>
aws cloudfront get-cloud-front-origin-access-identity --id <oai-id> --profile <profile>
aws s3api get-bucket-policy --bucket <bucket> --profile <profile>
aws s3api get-bucket-location --bucket <bucket> --profile <profile>
aws wafv2 get-web-acl --scope CLOUDFRONT --id <acl-id> --name <acl-name> --profile <profile>
aws cloudtrail lookup-events --lookup-attributes AttributeKey=ResourceName,AttributeValue=<resource> --profile <profile>
aws logs filter-log-events --log-group-name <log-group> --start-time <epoch-ms> --end-time <epoch-ms> --profile <profile>
```

Each inspection requires an action proposal, receipt, and evidence record.

## Safety Rules

- Do not update the CloudFront distribution without explicit approval.
- Do not create a CloudFront invalidation without explicit approval.
- Do not update S3 bucket policy or ownership controls without explicit approval.
- Do not modify WAF rules without explicit approval.
- Do not change Route 53 without explicit approval.
- Do not modify IAM without explicit approval.
- Do not expose credentials, secrets, or tokens in artifacts.
- Express all fixes as pending actions unless approved and receipted.

## Required WML Artifacts

Create or maintain:

```text
world.wml.json
plan.md
actions/*.proposal.json
receipts/*.receipt.json
evidence/*.evidence.json
hypotheses.json
final-report.md
conformance-report.md
```

Templates in this directory:

- [world.template.wml.json](world.template.wml.json)
- [action-proposal.template.json](action-proposal.template.json)
- [receipt.template.json](receipt.template.json)
- [evidence.template.json](evidence.template.json)
- [hypothesis.template.json](hypothesis.template.json)
- [final-report.template.md](final-report.template.md)
- [agent-prompt.md](agent-prompt.md)

## Final Report Structure

The final report must include:

1. Symptom
2. AWS profile and distribution ID used
3. Inspected AWS resources
4. Evidence table with evidence IDs
5. Hypotheses and status
6. Facts
7. Inferences
8. Likely root cause
9. Recommended fix
10. Actions requiring approval
11. Remaining unknowns
