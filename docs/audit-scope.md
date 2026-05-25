# Audit scope

This page lists the modules expected to fall inside an external security
audit. The public readiness summary is in
[`audit-readiness.md`](audit-readiness.md); the full readiness pack and
module-level findings logs are shared under a private-access process.

## In-scope modules

- ML-DSA threshold aggregation
- Lagrange premultiplication
- DKG / secure key generation
- Nonce safety and retry semantics
- Sui Ed25519 / FROST adapter (planned for the next validation milestone)
- TCP / P2P cluster stability

## Risk boundaries

- Application-layer Move vault logic is outside the cryptographic core
  audit scope; it is covered separately by application-level review.
- Operator deployment configuration (key custody hardware, HSM
  integration, operator runbook) is outside the protocol audit scope.

## Public materials

- [Audit readiness — public summary](audit-readiness.md) — sanitized
  module-by-module readiness state, internal review depth, and the
  areas where external review is most valuable.
- [Sui integration — technical architecture detail](sui-architecture-detail.md)
  — public, sanitized version of the Sui adapter design.
- [Test summary](test-summary.md) — traceable snapshot of the core
  repository test state.

## Private materials available to audit firms

The following artifacts are maintained in the project's internal review
pack and are shared with audit firms during scoping. Each carries its
own commit identifier and date. The PDFs themselves are not hosted in
this public repository — they are released under the private review
access process described below to keep internal maintenance metadata,
operator identities, and module-level findings out of the public
record. The
[`audit-readiness.md`](audit-readiness.md) document is the public,
sanitized derivative of the Security Audit Readiness Summary.

| Artifact | Format | Subject |
|---|---|---|
| Security Audit Readiness Summary | PDF (under private access) | Module-by-module readiness, identified risk areas, modules where external review is most valuable |
| Architecture pack (system boundary, sequences, state machines, interface contracts, SLO and capacity) | Markdown set (under private access) | Detailed engineering documentation underlying the audit scope |
| Internal review reports | Markdown (under private access) | Round-by-round internal findings and remediation status for each in-scope module |
| Threat-test transcripts | Markdown (under private access) | Per-test results for adversarial / replay / bad-participant scenarios |

## Engagement model

Audit firms can request access to the private core repository for the
duration of the engagement. To initiate scoping, open an issue on this
repository or contact the maintainers through the project's private
review process. The [README](../README.md) carries the same routing.
