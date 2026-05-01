# WML Agent Workflow Conformance Checklist

A run is WML-compliant only if:

- [ ] A `world.wml.json` was created.
- [ ] The world includes task goals.
- [ ] AWS resources are represented as entities.
- [ ] Permissions are clearly defined.
- [ ] Every AWS inspection has an action proposal.
- [ ] Every executed inspection has a receipt.
- [ ] Every finding has an evidence reference.
- [ ] Every hypothesis is marked as `verified`, `ruled_out`, `partially_supported`, or `unknown`.
- [ ] No mutating AWS action was executed without explicit approval.
- [ ] Final report cites evidence IDs.
- [ ] Recommended fixes are pending actions unless approved.
- [ ] A `conformance-report.md` was produced.
