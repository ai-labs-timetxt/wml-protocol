# AWS Playbook: CloudFront 403 Troubleshooting

## Goal

Identify the likely root cause of a CloudFront HTTP 403 response using WML.

## Required inputs

- AWS profile name
- CloudFront distribution ID
- symptom description
- sample URL if available
- approximate time range if logs are involved

## Initial hypotheses

- S3 bucket policy denies CloudFront
- OAC/OAI is misconfigured
- WAF blocks the request
- geo restriction blocks the request
- signed URL or signed cookie is required
- origin itself returns 403
- behavior path pattern mismatch
- viewer request method is not allowed
- custom error response masks origin behavior

## Suggested read-only inspections

The agent may use equivalent AWS CLI/API commands.

```text
aws cloudfront get-distribution --id <distribution-id> --profile <profile>
aws cloudfront get-distribution-config --id <distribution-id> --profile <profile>
aws cloudfront get-cloud-front-origin-access-identity --id <oai-id> --profile <profile>
aws s3api get-bucket-policy --bucket <bucket> --profile <profile>
aws s3api get-bucket-location --bucket <bucket> --profile <profile>
aws wafv2 get-web-acl --scope CLOUDFRONT --id <acl-id> --name <acl-name> --profile <profile>
```

## Required WML artifacts

The agent should create:

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

## Safety rules

- Do not update CloudFront distribution.
- Do not update S3 bucket policy.
- Do not modify WAF rules.
- Do not create invalidations.
- Do not change Route 53.
- Do not modify IAM.
- Express all fixes as pending actions requiring explicit human approval.

## Final report structure

The final report must include:

1. Symptom
2. AWS profile and distribution ID used
3. Inspected resources
4. Evidence table
5. Hypotheses and status
6. Likely root cause
7. Recommended fix
8. Actions requiring approval
9. Remaining unknowns
