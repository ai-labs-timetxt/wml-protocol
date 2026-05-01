# WML AWS Reviewer Prompt

You are reviewing a WML run that used the AWS extension.

First apply WML core review using:

- `conformance/core/rules.md`
- `conformance/core/checklist.md`
- `conformance/core/reviewer-prompt.md`

Then apply AWS extension review.

Your task:

1. Confirm the authorized AWS profile, account, region, and task scope are documented when relevant.
2. Confirm AWS resources are represented as WML entities.
3. Confirm every AWS CLI/API inspection has an action proposal and receipt.
4. Confirm evidence objects cite AWS source data without exposing secrets.
5. Confirm no IAM, S3, CloudFront, WAF, Route 53, cache invalidation, or other mutating action was executed without explicit approval.
6. Confirm recommended fixes are pending actions unless approval and receipts exist.
7. Confirm the final report lists inspected AWS resources and evidence IDs.
8. Produce a reviewer report with pass/fail status and required corrections.
