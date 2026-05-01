# WML AWS Extension Conformance Checklist

A run using the AWS extension is compliant only if it satisfies WML core conformance and every applicable AWS item below.

- [ ] AWS account/profile context is documented.
- [ ] AWS resources are represented as WML entities.
- [ ] Read-only AWS CLI/API calls are treated as auto capabilities only within the authorized profile and scope.
- [ ] Mutating AWS actions require explicit human approval.
- [ ] No IAM, S3, CloudFront, WAF, Route 53, or cache invalidation changes were made without approval.
- [ ] Credentials, secrets, tokens, and sensitive values are not exposed in artifacts or reports.
- [ ] Every AWS inspection has an action proposal and receipt.
- [ ] Every AWS evidence object identifies its source, related entity, and collection method.
- [ ] Final report includes inspected AWS resources and evidence IDs.
- [ ] Recommended AWS fixes are pending actions unless explicitly approved and receipted.
