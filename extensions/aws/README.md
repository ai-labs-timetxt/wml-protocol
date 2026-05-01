# WML AWS Extension

The AWS extension explains how to apply WML core to AWS troubleshooting, review, and operational investigation tasks.

AWS is a good fit for WML because resources, configurations, policies, logs, events, and CLI/API responses are structured enough to become entities, state, evidence, hypotheses, action proposals, and receipts.

AWS is not the scope of WML core. It is one domain extension built on top of the shared protocol.

## Documents

- [concepts.md](concepts.md): AWS concepts mapped to WML.
- [permission-classes.md](permission-classes.md): AWS-specific permission classes.
- [resource-entity-mapping.md](resource-entity-mapping.md): how to model AWS resources as entities.
- [aws-cli-capabilities.md](aws-cli-capabilities.md): how to represent AWS CLI/API calls as capabilities.

## Profile Usage

AWS runs should use only the profile authorized by the user. Profiles are normally configured through:

```text
~/.aws/config
~/.aws/credentials
```

The agent should document the chosen profile and avoid printing credentials or secrets.
