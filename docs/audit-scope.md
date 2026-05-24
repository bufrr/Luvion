# Audit scope

This page summarises the modules expected to fall inside an external
security audit and lists the readiness artifacts available to audit
firms on request.

## In-scope modules

- ML-DSA threshold aggregation
- Lagrange premultiplication
- DKG / secure key generation
- Nonce safety and retry semantics
- Sui Ed25519 / FROST adapter
- TCP / P2P cluster stability

## Risk boundaries

- Application-layer Move vault logic is outside the cryptographic core
  audit scope; it is covered separately by application-level review.
- Operator deployment configuration (key custody hardware, HSM
  integration, operator runbook) is outside the protocol audit scope.

## Readiness artifacts

The following artifacts are maintained in the project's internal review
pack and are shared with audit firms during scoping.

| Artifact | Format | Subject |
|---|---|---|
| Security Audit Readiness Summary | PDF | Current readiness state for each in-scope module, identified risk areas, and modules where external review is most valuable |
| Architecture pack (system boundary, sequences, state machines, interface contracts, SLO and capacity, integration plan) | Markdown set | Detailed engineering documentation underlying the audit scope |
| Internal review reports | Markdown | Iterative internal findings and remediation status for each in-scope module |

Specific commit identifiers and dates are stamped on each artifact and
shared at scoping time.

## Engagement model

Audit firms can request access to the private core repository for the
duration of the engagement. To initiate scoping, open an issue on this
repository or contact the maintainers through the project's private
review process. The README has the same routing.
