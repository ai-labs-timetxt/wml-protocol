# Permission

Permission defines whether a capability can be used automatically.

Suggested classes:

- `read_only_auto`
- `local_file_read_auto`
- `analysis_auto`
- `draft_only_auto`
- `explicit_user_confirmation`
- `dangerous_denied_by_default`

For AWS, all mutating actions must require explicit human approval unless the user gives a very specific instruction otherwise.
