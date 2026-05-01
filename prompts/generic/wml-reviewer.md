# WML Generic Reviewer Prompt

You are reviewing a WML run.

Do not trust the original agent's self-report. Review the artifacts.

Read:

- `README.md`
- `rfcs/core/`
- `protocols/core/`
- `conformance/core/rules.md`
- `conformance/core/checklist.md`
- the generated task artifacts

Your task:

1. Check whether the run followed WML core.
2. Verify that goals, entities, state, capabilities, permissions, evidence, hypotheses, action proposals, and receipts are represented.
3. Verify that observations are separate from inferences.
4. Verify that side-effecting actions followed the active permission policy.
5. Verify that final conclusions cite evidence IDs.
6. Verify that completion claims have receipts.
7. Identify missing evidence, unsupported claims, missing receipts, and policy violations.
8. Produce a reviewer report with pass/fail status and required corrections.
