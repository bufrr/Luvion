# Architecture overview

This document summarises the major components and their boundaries. Full
detail lives in the linked source documents.

## Layers

| Layer | Responsibility |
|---|---|
| Cluster runtime | Authenticated TCP / P2P transport for committee-scale (22-of-33 reference configuration) signing ceremonies |
| Signing core | ML-DSA threshold aggregation with Lagrange premultiplication |
| DKG / key generation | Distributed key generation; controlled-environment flow is acceptable for testnet-grade validation, audited DKG is a prerequisite for production custody |
| Sui adapter | Threshold Ed25519 / FROST backend producing Sui-compatible signatures |
| Application layer | Move vault and similar asset-control modules (sits above account auth, not inside it) |

## Source documents

- [Sui Integration Technical Architecture](assets/sui-integration-technical-architecture.pdf)
- [Luvion Technical Summary](assets/luvion-technical-summary.pdf)

## Boundaries

- The Sui adapter is the near-term integration surface. ML-DSA remains
  the long-term post-quantum route and is not the Sui account signing
  mechanism.
- The Move vault is an application-layer module; it sits above account
  auth, not inside it.
- The signing core and DKG flow are common to both the ML-DSA long-term
  path and the threshold Ed25519 / FROST Sui near-term path; the adapter
  layer is what differs between them.
