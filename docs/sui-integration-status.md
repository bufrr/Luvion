# Sui integration status

## Current stage

**Integration framework and architecture.** The threshold signing core
is in place. A threshold Ed25519 / FROST adapter targeting Sui's current
account signing mechanism is the integration surface.

This is **not** a Sui testnet deployment. It is **not** a production
custody system. There is **no official Sui Foundation affiliation**.

## Near-term path

Sui's current account signing uses Ed25519. Luvion's near-term Sui
integration uses threshold Ed25519 / FROST to remain compatible with
that mechanism. ML-DSA is retained as Luvion's long-term post-quantum
route and is not the Sui account signing mechanism. Sui does not
natively support threshold ML-DSA account auth.

## Next milestone

Testnet-grade validation. Engineering scope includes:

- Sui signing message test vectors
- Ed25519 / FROST threshold signing backend
- Sui adapter
- Transaction simulation
- Testnet submission path
- Transaction result listening
- Audit logging
- Error attribution

A detailed near-term plan covering these areas is maintained internally
and shared with audit firms and qualified partners on request.

## Key generation

For testnet-grade validation, a controlled key generation flow is
acceptable. Production custody requires an audited DKG or audited
secure key generation flow. This boundary is the same one external
audit work will need to verify.

## Source document

- [Sui Integration Technical Architecture](assets/sui-integration-technical-architecture.pdf)
