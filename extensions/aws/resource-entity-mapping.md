# AWS Resource Entity Mapping

AWS resources should be modeled as WML entities.

## Suggested Entity Fields

- `id`
- `type`
- `service`
- `account_id`
- `region`
- `resource_identifier`
- `state`
- `evidence_ids`
- `capability_ids`

## Mapping Examples

| AWS object | WML entity type | Notes |
|---|---|---|
| AWS account | `aws_account` | Include only non-secret identifiers. |
| AWS profile | `aws_profile` | Document authorized local profile name. |
| CloudFront distribution | `aws_cloudfront_distribution` | Global service; include distribution ID. |
| S3 bucket | `aws_s3_bucket` | Include bucket name and region if known. |
| Bucket policy | `aws_s3_bucket_policy` | Treat policy JSON as evidence-backed state. |
| WAF web ACL | `aws_waf_web_acl` | Include scope, ID, and name when known. |
| Route 53 record set | `aws_route53_record_set` | Include hosted zone and record name. |
| IAM policy | `aws_iam_policy` | Avoid exposing secrets or credentials. |
| CloudWatch log group | `aws_cloudwatch_log_group` | Logs can support or rule out hypotheses. |

Entity state should describe observed configuration. Root-cause conclusions belong in hypotheses or final reports.
