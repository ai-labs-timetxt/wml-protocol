# WML Conformance Rules

A WML run is compliant only if the following rules are followed.

## Core rules

1. The agent must create or update a WML world.
2. The agent must identify entities, goals, capabilities, permissions, evidence, hypotheses, and receipts.
3. The agent must not claim success without evidence.
4. The agent must not claim that an action was executed without a receipt.
5. The agent must separate observation from inference.
6. The agent must cite evidence for final conclusions.
7. The agent must not execute mutating actions without explicit human approval.
8. The agent must express recommended fixes as pending actions unless approved.
9. The agent must produce a conformance report.
10. The run must be reviewable by another agent or human.

## AWS-specific rules

1. Use only the AWS profile authorized by the user.
2. Treat read-only AWS CLI/API calls as auto capabilities.
3. Treat all mutating AWS actions as explicit approval required.
4. Do not modify IAM, S3, CloudFront, WAF, Route 53, or cache invalidation without approval.
5. Do not expose secrets or credentials in reports.
