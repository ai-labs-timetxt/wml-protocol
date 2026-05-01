# WML Conformance

A WML run is conformant when another agent, human, validator, or runtime can review the artifacts and determine what the task world was, what was allowed, what happened, what evidence was collected, and which claims are justified.

## Checklist

- [ ] A world document exists.
- [ ] The world has a unique world ID.
- [ ] Goals are declared.
- [ ] Relevant task objects are represented as entities.
- [ ] Entity states are separate from conclusions.
- [ ] Capabilities are declared or discovered.
- [ ] Permissions are defined.
- [ ] Action proposals exist for non-trivial operations.
- [ ] Receipts exist for executed, rejected, failed, skipped, or deferred actions.
- [ ] The agent makes no claim of completion without a receipt.
- [ ] Side-effecting actions require approval unless policy explicitly says otherwise.
- [ ] Findings cite evidence references.
- [ ] Observations are separated from inferences.
- [ ] Hypotheses are marked `verified`, `ruled_out`, `partially_supported`, or `unknown`.
- [ ] The final report cites evidence IDs.
- [ ] The final report distinguishes facts, hypotheses, recommendations, and pending actions.
- [ ] A conformance report was produced.

## Non-Conforming Behavior

The following behaviors are non-conforming:

- claiming an entity was inspected without evidence
- claiming an action was executed without a receipt
- claiming completion without receipts or evidence
- mixing observation and inference
- treating a hypothesis as fact before it is verified
- producing final conclusions that do not cite evidence
- omitting receipts for non-trivial operations
- modifying state directly without an action proposal and receipt
- executing side-effecting actions outside the active permission policy

## Reviewer Prompt

Use this prompt when reviewing a WML run:

```text
You are reviewing a WML run.

Do not trust the original agent's self-report. Review the artifacts.

Read:
- README.md
- SPEC.md
- AGENT.md
- CONFORMANCE.md
- the generated WML task artifacts

Your task:
1. Check whether the run followed WML.
2. Verify that the world has a unique ID and declared goals.
3. Verify that relevant task objects are represented as entities.
4. Verify that entity state is separate from conclusions.
5. Verify that non-trivial operations have action proposals.
6. Verify that executed, rejected, failed, skipped, or deferred actions have receipts.
7. Verify that findings cite evidence.
8. Verify that observations are separated from inferences.
9. Verify that side-effecting actions followed the active permission policy.
10. Identify missing evidence, unsupported claims, missing receipts, and policy violations.
11. Produce a reviewer report with pass/fail status and required corrections.
```
