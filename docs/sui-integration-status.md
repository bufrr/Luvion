# Sui integration status

## Current stage

**Integration framework and architecture.** The threshold signing core
is in place. A threshold Ed25519 / FROST adapter targeting Sui's current
account signing mechanism is the integration surface.

This is **not** a Sui testnet deployment. It is **not** a production
custody system. There is **no official Sui Foundation affiliation**.

## Near-term path

Sui supports multiple account-signature schemes (Ed25519, Secp256k1,
Secp256r1, multisig, zkLogin, passkey — see
[Sui transaction-auth signatures](https://docs.sui.io/concepts/cryptography/transaction-auth/signatures)).
This validation plan targets Sui's **Ed25519 account-signature path**.
Luvion uses threshold Ed25519 / FROST to produce a standard Ed25519
signature accepted by Sui under that scheme, while ML-DSA remains
Luvion's long-term post-quantum route. ML-DSA is not the Sui account
signing mechanism, and Sui does not natively support threshold ML-DSA
account auth.

## 30–45 day validation plan

The next milestone is testnet-grade validation. The plan is organised
into three two-week phases. No deliverable is gated on a completion
percentage; each row lists a deliverable, the verification command or
artifact, and the exit criterion that ends the phase.

### Weeks 1–2 — Signing-backend correctness

| Deliverable | Verification | Exit criterion |
|---|---|---|
| Sui signing message test vectors | Compare against Sui SDK reference vectors (`@mysten/sui` typescript SDK and `fastcrypto` Rust reference) | Byte-exact match for the supported transaction shapes |
| Ed25519 / FROST threshold signing backend | 22-of-33 ceremony produces a 64-byte Ed25519 signature; verify against Sui ZIP215 verifier | Verifier accepts every signature produced by the ceremony in the local cluster |
| Aggregate-key handling | Round-trip aggregate public key through DKG ceremony output → wire format → on-chain address derivation | Derived Sui address is reproducible across ceremony reruns from the same DKG transcript |

### Weeks 3–4 — Sui adapter and dry-run

| Deliverable | Verification | Exit criterion |
|---|---|---|
| Sui adapter | Build a `TransactionData` for representative flows (gas-only transfer, object move-call), sign with the FROST backend | Adapter produces a Sui transaction envelope that passes local `fastcrypto` verification |
| Transaction simulation | Run `sui_dryRunTransactionBlock` against a local Sui dev node | Dry-run returns success status for the representative flows |
| Object / gas resolution | Resolve owned-object and gas-coin references through the Sui SDK before signing | Adapter refuses to sign when object versions are stale; signs and dry-runs succeed when fresh |

### Weeks 5–6 — Testnet submission and observability

| Deliverable | Verification | Exit criterion |
|---|---|---|
| Testnet submission path | Submit a signed transaction via `sui_executeTransactionBlock` to Sui testnet | Transaction lands and shows up in a checkpoint |
| Transaction result listening | Subscribe to effects / events for submitted transactions | Adapter surfaces effect status and emitted events back to the calling layer |
| Audit logging | Each Sui submission produces a structured log entry covering request id, FROST ceremony id, transaction digest, dry-run result, submit result, effect status | Logs are sufficient to reconstruct any submission end-to-end without consulting node memory |
| Error attribution | Classify failures into: ceremony failure, dry-run rejection, network error, on-chain rejection | Each failure class has a dedicated log code and a documented remediation step |

### Out of scope for this 30–45 day window

- Production-grade DKG ceremony hardening (separate audit-driven workstream).
- Multi-region operator runbook.
- HSM / hardware-custody integration.

## Key generation

For testnet-grade validation, a controlled key generation flow is
acceptable. Production custody requires an audited DKG or audited
secure key generation flow. This boundary is the same one external
audit work will need to verify.
