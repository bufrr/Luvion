# Audit readiness — public summary

This page is the public, sanitized summary of audit readiness state per
in-scope module. The full readiness summary, internal review reports,
and module-level findings logs are shared with audit firms during
scoping.

The scope and risk boundaries are in [`audit-scope.md`](audit-scope.md).

## Readiness state by module

| Module | Implementation state | Internal-review state | Notes |
|---|---|---|---|
| ML-DSA threshold aggregation | Implemented | Multiple internal review rounds completed; remediations landed | Reference threshold size 22-of-33 |
| Lagrange premultiplication | Implemented | Internal review completed; remediations landed | Performance-critical hot path |
| DKG / secure key generation | Implemented (testnet-grade) | Internal review completed; production gate is audited DKG | Controlled key ceremony acceptable only for testnet validation |
| Nonce safety and retry semantics | Implemented | Internal review completed; threat tests in place | Covers per-session nonce lifecycle, persistent replay guard, fresh nonce on retry |
| Sui Ed25519 / FROST adapter | **Planned — next milestone** | Not yet implemented | First validation step is the 30–45 day plan; see [Sui integration status](sui-integration-status.md) |
| TCP / P2P cluster stability | Implemented | Internal review completed; remediations landed | Covers idle / cache TTL, retry, view-change, replay |

## Internal review depth

The internal review process is multi-round and explicitly seeks
regressions in fix code. Each round produces a written report with
file:line findings, severity, status (fixed / design-closed), and
verification evidence. Audit firms see the round-by-round reports
during scoping.

## What external review is most valuable for

- **ML-DSA threshold aggregation** — independent verification of the
  protocol's correctness under adversarial committee subsets and of
  the rejection / retry path under partial-corruption scenarios.
- **DKG / secure key generation** — independent verification of the
  production-gate ceremony (audited DKG or independently reviewed
  secure key ceremony) before any production-custody claim is made.
- **Nonce safety and retry semantics** — independent verification of
  the persistent replay guard, the fresh-nonce-on-retry invariant, and
  the request-id lifecycle under crash / restart scenarios.
- **FROST aggregate signature output** — once implemented, independent
  verification against Sui fastcrypto ZIP215 test vectors and against
  the cofactored Ed25519 verification equation.

## Out of scope for cryptographic-core audit

- Application-layer Move vault logic (covered separately by
  application-level review).
- Operator deployment configuration: key custody hardware, HSM
  integration, operator runbook, key-rotation operational procedure.
- Network operations: peering configuration, firewall policy,
  monitoring / alerting stack.

## Access to internal review pack

The full readiness summary, the round-by-round internal review
reports, the threat-test transcripts, and the per-module findings logs
are shared with audit firms during scoping. To initiate, open an issue
on this repository or contact the maintainers through the project's
private review process.

## Disclaimers

- This page is not an external audit report.
- This page does not represent an audit completion.
- "Internal review completed" means an internal review round closed
  with no open findings, not that external audit has been performed.
