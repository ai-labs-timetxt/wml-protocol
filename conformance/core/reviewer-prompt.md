# WML Core Reviewer Prompt

You are reviewing a WML run.

Do not trust the original agent's self-report. Review the artifacts.

Read:

- WML repo README
- core RFCs
- `conformance/core/rules.md`
- `conformance/core/checklist.md`
- the generated task artifacts

Your task:

1. Check whether the run followed WML core.
2. Verify that the world has a unique ID and declared goals.
3. Verify that relevant task objects are represented as entities.
4. Verify that entity state is separate from conclusions.
5. Verify that non-trivial operations have action proposals.
6. Verify that executed, rejected, failed, skipped, or deferred actions have receipts.
7. Verify that findings cite evidence.
8. Verify that observations are separated from inferences.
9. Verify that side-effecting actions followed the active permission policy.
10. Identify missing evidence, unsupported claims, or missing receipts.
11. Produce a reviewer report with pass/fail status and required corrections.
