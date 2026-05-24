# Demo summary

The existing demos exercise the Rust high-threshold signing core in a
controlled environment and report local-network and WAN-scale timing
metrics. They are referenced here rather than reproduced.

## Available artifacts

The following artifacts exist in the project's internal review pack.
They are shared with technical reviewers, audit firms, and qualified
partners under a private-access request.

| Artifact | Format | Subject |
|---|---|---|
| Luvion Demo Report | PDF | 22-of-33 signing ceremony end-to-end execution, with local and WAN-scale timing tables |
| Demo video — local cluster | Screen capture | 22-of-33 signing ceremony executed on a single host with 33 node processes |
| Demo video — WAN scenario | Screen capture | Same ceremony executed across geographically distributed nodes, with round-trip and total-signing-time measurements |

## Access path

Open an issue on this repository or contact the maintainers through the
project's private review process to request access. The artifacts above
are not redistributed publicly to keep operator and reviewer
identification out of the public record.

## What the demo shows

- Rust high-threshold signing core executes end-to-end in a controlled
  environment.
- Local-network and WAN-scale timing measurements were captured.

## What the demo does not show

- It is not an audit completion.
- It is not a Sui testnet deployment.
- It is not evidence of production custody readiness.
- The Sui adapter is not exercised in these demos; that is the next
  milestone (see [Sui integration status](sui-integration-status.md)).
