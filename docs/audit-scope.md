# Audit scope

This page summarises the modules expected to fall inside an external
security audit. The full readiness material is available to audit firms
on request.

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

## External review needed

The cryptographic core (the six items above) is the target of external
audit. The internal readiness summary — covering current state,
identified risk areas, and modules where external review is most
valuable — is available to audit firms on request alongside core-repo
access.

## Engagement model

Audit firms can request access to the private core repository for the
duration of the engagement. Contact information is in the
[README](../README.md).
