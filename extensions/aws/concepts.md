# AWS Concepts in WML

## Why AWS Fits WML

AWS task worlds are usually made of resources, configuration documents, policies, events, logs, and proposed changes. These map cleanly onto WML:

- resources become entities
- current configuration becomes state
- CLI/API reads become capabilities
- command outputs, logs, and policies become evidence
- possible causes become hypotheses
- proposed fixes become action proposals
- executed, rejected, failed, skipped, or deferred operations become receipts

## Resources as Entities

Represent each relevant AWS resource as an entity with an ID, type, service, region if applicable, and evidence-backed state.

Examples:

- CloudFront distribution
- S3 bucket
- bucket policy
- WAF web ACL
- Route 53 record set
- IAM role or policy
- CloudWatch log group
- CloudTrail event

## Policies, Config, and Logs as Evidence

AWS policies, configuration documents, command outputs, and logs may be evidence if they are collected through a recorded action proposal and receipt.

Evidence should cite source, collection method, related entity, and timestamp when available.

## Mutating Operations

AWS mutating operations should be represented as approval-required action proposals. They should not be executed automatically.
