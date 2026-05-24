# Luvion

A threshold signing protocol focused on post-quantum-ready custody primitives,
with a near-term Sui integration path using threshold Ed25519 / FROST.

## Current state

- **Core protocol:** Rust implementation of a high-threshold (22-of-33)
  signing ceremony with ML-DSA aggregation, Lagrange premultiplication,
  DKG / key generation flows, nonce safety and retry semantics, and an
  authenticated TCP / P2P cluster runtime.
- **Sui integration:** integration framework and architecture level. A
  threshold Ed25519 / FROST adapter targeting Sui's current account signing
  mechanism is the integration surface. Testnet-grade validation is the
  next milestone — **this repository does not represent a Sui testnet
  deployment**.
- **ML-DSA:** retained as the long-term post-quantum security route. Not
  abandoned.
- **Move vault:** referenced as an application-layer asset control module.
  It is not the Sui account signing mechanism.

## What this is not

- Not production custody software.
- Not a Sui testnet deployment.
- Not endorsed by or affiliated with the Sui Foundation.
- Sui does not natively support threshold ML-DSA account auth; the Sui
  near-term path uses threshold Ed25519 / FROST.

## Repository contents

- [`docs/architecture.md`](docs/architecture.md) — short architecture overview
- [`docs/sui-integration-status.md`](docs/sui-integration-status.md) — current Sui integration stage
- [`docs/demo-summary.md`](docs/demo-summary.md) — pointer to existing demo materials
- [`docs/test-summary.md`](docs/test-summary.md) — current test status of the core implementation
- [`docs/audit-scope.md`](docs/audit-scope.md) — audit scope and risk boundaries

## Access to the core implementation

The core protocol implementation is maintained in a private repository.
Access is available to technical reviewers, audit firms, and qualified
partners on request.

## Contact

For access, audit engagement, or technical review requests, contact the
maintainers via the channel listed in the project's internal review pack.

## License

This repository's documentation is released under the
[Apache License 2.0](LICENSE).
