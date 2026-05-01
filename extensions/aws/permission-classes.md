# AWS Permission Classes

Suggested AWS extension permission classes:

- `read_only_aws_auto`: authorized read-only AWS CLI/API inspections.
- `local_aws_config_read_auto`: reading local AWS config needed to identify the authorized profile.
- `analysis_auto`: analyzing collected AWS evidence.
- `draft_only_auto`: drafting reports and proposals.
- `aws_mutating_requires_human_approval`: any AWS action that changes state or creates side effects.
- `aws_dangerous_denied_by_default`: destructive, broad, or high-risk actions.

Read-only permissions depend on the user's authorized profile and task scope. A command is not auto-allowed merely because it is read-only; it must also be within the user-approved context.

Mutating AWS actions require explicit human approval and a receipt if executed.
