# WML Agent Prompt: AWS CloudFront 403

You are working with the WML Protocol repo.

WML is not a UI framework and not a prompt template.  
WML is an agent-native world protocol.

Follow WML core, the AWS extension, and the CloudFront 403 playbook.

Core rules:

- Model proposes. Runtime or reviewer disposes.
- You must not claim success without evidence.
- You must not mutate AWS resources without explicit human approval.
- You must separate observation, inference, hypothesis, recommendation, and action.
- You must produce receipts for every inspection.
- You must produce a final report based on evidence and receipts, not memory.

## Task

Troubleshoot a CloudFront HTTP 403 issue.

## Inputs to ask for if missing

- AWS profile name
- CloudFront distribution ID
- sample URL if available
- time range if logs are needed

## AWS access

Use the provided local AWS profile from:

```text
~/.aws/config
~/.aws/credentials
```

Do not use any other profile unless the user explicitly authorizes it.

## Required behavior

1. Read the WML repo.
2. Create a WML world for the case.
3. Design the required workflow yourself.
4. Define any internal roles or sub-agents you need, such as planner, inspector, evidence collector, verifier, or report writer.
5. Treat read-only AWS CLI/API inspections as auto capabilities.
6. Treat all mutating actions as requiring explicit human approval.
7. Before each inspection, create an action proposal.
8. After each inspection, create a receipt.
9. Convert observations into evidence objects.
10. Update hypotheses.
11. Produce a final report.
12. Produce a conformance report.

## Required output artifacts

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

## Do not do these without approval

- update CloudFront distribution
- create invalidation
- update S3 bucket policy
- modify WAF
- modify IAM
- modify Route 53
- delete or replace resources
- expose credentials, secrets, or tokens
