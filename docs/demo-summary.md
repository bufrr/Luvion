# Demo summary

The existing demos exercise the Rust high-threshold signing core in a
controlled environment and report local-network and WAN-scale timing
metrics. This page is the public summary of what the demos cover. The
full report and the demo videos are shared under a private-access
process so that operator and reviewer identities, exact infrastructure
addresses, and specific numerical results stay out of the public record.

## What the demos cover

### Demo A — local 33-node cluster

- All 33 Luvion node processes run on a single host with isolated
  per-node working directories, TCP ports, and identity material.
- A 22-of-33 threshold ML-DSA signing ceremony is driven end-to-end:
  share generation, node start, round1 commitment, round2 partial
  signature exchange, aggregate signature verification.
- Round1 / round2 dispatch retry, idle-connection / cache TTL handling,
  and per-session replay protection are exercised on the production
  TCP cluster runtime, not on a mock transport.
- Output: aggregated signature byte string and a local Ed25519 / ML-DSA
  verification result.

### Demo B — WAN-scale 33-node cluster

- The same 22-of-33 threshold ML-DSA ceremony is driven across
  geographically distributed nodes.
- Round-trip latencies are measured under realistic network
  conditions; aggregate signing time is reported relative to single-host
  baseline.
- View-change / coordinator-failover paths are exercised under
  WAN-scale jitter to confirm they recover from real network partitions
  rather than just simulated ones.

## What the demos do not cover

- The Sui adapter and the threshold Ed25519 / FROST backend are **not**
  exercised in either demo; they are planned for the next validation
  milestone (see [Sui integration status](sui-integration-status.md)).
- The DKG ceremony used in the demo is a controlled key generation
  flow; it is not an audited DKG. Production custody requires an
  audited DKG or independently reviewed secure key ceremony.
- Demo execution is in a controlled environment, not a production
  custody deployment.

## Artifacts available under private access

| Artifact | Format | Subject |
|---|---|---|
| Luvion Demo Report | PDF | The 22-of-33 ceremony execution log, with per-phase timing tables and aggregate verification result |
| Demo video — local cluster | Screen capture | Demo A, full ceremony |
| Demo video — WAN scenario | Screen capture | Demo B, full ceremony with WAN measurements |

## Access path

Open an issue on this repository describing the review context
(technical evaluation, audit scoping, integration partnership) or
contact the maintainers through the project's private review process.
The artifacts above are not redistributed publicly to keep operator and
reviewer identification out of the public record.

## Disclaimers

- The demos are not an audit completion.
- The demos are not a Sui testnet deployment.
- The demos are not evidence of production custody readiness.
