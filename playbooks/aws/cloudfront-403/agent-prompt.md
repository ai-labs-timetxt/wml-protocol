# WML Agent Prompt: AWS CloudFront 403

You are working with the WML Protocol repo.

WML is an agent-native world protocol. It is not a UI framework, not HTML for humans, not a SaaS wrapper, and not merely tool calling.

Follow WML core, the AWS extension, and the CloudFront 403 playbook.

## Task

Troubleshoot a CloudFront HTTP 403 issue.

## Inputs to Ask For if Missing

- AWS profile name
- CloudFront distribution ID
- sample URL if available
- symptom details
- time range if logs are needed

## AWS Access

Use only the provided local AWS profile from:

```text
~/.aws/config
~/.aws/credentials
```

Do not use any other profile, account, or role unless the user explicitly authorizes it.

## Required Behavior

1. Read the WML core protocol, AWS extension, and this playbook.
2. Create a WML world for the case.
3. Treat AWS resources as WML entities.
4. Treat read-only AWS CLI/API inspections as auto capabilities only within the authorized profile and scope.
5. Treat all mutating AWS actions as requiring explicit human approval.
6. Create an action proposal before every AWS inspection.
7. Create a receipt after every AWS inspection.
8. Convert command outputs, policies, configs, logs, and events into evidence objects.
9. Separate observation from inference.
10. Update hypotheses as `verified`, `ruled_out`, `partially_supported`, or `unknown`.
11. Produce a final report with evidence IDs.
12. Produce a conformance report covering WML core and AWS extension requirements.

## Required Output Artifacts

Create a case directory with:

```text
world.wml.json
plan.md
actions/
receipts/
evidence/
hypotheses.json
final-report.md
conformance-report.md
```

## Do Not Do These Without Approval

- update CloudFront distribution
- create invalidation
- update S3 bucket policy
- modify WAF
- modify IAM
- modify Route 53
- delete or replace resources
- expose credentials, secrets, or tokens
