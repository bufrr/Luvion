# Test summary

The core protocol implementation lives in a private repository. This
page is a traceable snapshot of the test state on the date listed
below.

## Snapshot

| Field | Value |
|---|---|
| Snapshot date | 2026-05-26 |
| Toolchain | `rustc 1.93.1` / `cargo 1.93.1` |
| Internal commit identifier | This snapshot corresponds to the latest private-core commit at access-grant time; the exact commit hash is shared with reviewers when access is granted |
| Test execution environment | Linux x86_64, single-host 33-node cluster |
| Library suite result on snapshot date | `cargo test --lib -- --test-threads=1` reports `test result: ok. 228 passed; 0 failed; 0 ignored` |
| Known failures | None as of the snapshot date |
| Last open blocker | Closed prior to the snapshot date |

## Coverage by category

| Category | Status | Representative tests in the private core repo |
|---|---|---|
| TCP cluster end-to-end | passing | `int_cluster_sign_tcp`, `int_ceremony_22_of_33`, `int_cluster_scripts` |
| Node connectivity / stdio framing | passing | `int_node_stdio_round12`, `int_node_stdio_ping` |
| Network probe / ping-pong | passing | `int_node_stdio_ping::ping_pong_round_trip` |
| `t0` prefetch path | passing | Covered inside `int_ceremony_22_of_33` and `int_cluster_sign_tcp` |
| Idle connection handling / cache TTL | passing | `int_node_cache_ttl::round2_after_ttl_rejected` |
| Round1 / Round2 framing happy path | passing | `int_node_stdio_round12::round1_then_round2_succeeds` |
| Retry / timeout semantics | passing | `int_resilience_integration::partitioned_round_dispatch_marks_unreachable_nodes_and_triggers_view_change` |
| View-change / coordinator failover | passing | `int_resilience_integration::authenticated_view_change_routes_quorum_and_rejects_stale_epoch`, `int_resilience_integration::incremental_reshare_rejects_stale_epoch_and_finalizes_joiner_state` |
| DKG end-to-end | passing | `int_dkg_e2e`, `int_gen_shares_e2e` |
| Proactive reshare | passing | `int_proactive_reshare_e2e::proactive_reshare_rotates_committee_and_preserves_signing_key` |
| Replay / nonce safety (threat) | passing | `threat_node_replay_rejected`, `threat_node_bad_participants`, `threat_share_distribution_adversarial` |
| Libp2p runtime path | passing | `libp2p_runtime::*` module tests (feature-gated) |
| Coordinator integration | passing | `int_coordinator_integration` |

## Test commands (run in the private core repo)

```
# Library tests (covers signing core, p2p, view-change, network router, replay)
cargo test --lib -- --test-threads=1

# Libp2p runtime feature
cargo test --features libp2p-runtime --lib libp2p_runtime:: -- --test-threads=1

# Binary tests (node + share generation)
cargo test --bin node -- --test-threads=1
cargo test --bin gen_shares -- --test-threads=1

# TCP cluster end-to-end
cargo test --test int_cluster_sign_tcp -- --test-threads=1
cargo test --test int_ceremony_22_of_33 -- --test-threads=1
cargo test --test int_cluster_scripts -- --test-threads=1

# Node connectivity / framing / probe
cargo test --test int_node_stdio_ping -- --test-threads=1
cargo test --test int_node_stdio_round12 -- --test-threads=1

# Idle / cache TTL
cargo test --test int_node_cache_ttl -- --test-threads=1

# Retry / timeout / view-change / resilience
cargo test --test int_resilience_integration -- --test-threads=1

# DKG / share distribution / reshare
cargo test --test int_dkg_e2e -- --test-threads=1
cargo test --test int_gen_shares_e2e -- --test-threads=1
cargo test --test int_proactive_reshare_e2e -- --test-threads=1

# Threshold signing integration + threat suite
cargo test --test int_threshold_signing_integration -- --test-threads=1
cargo test --test threat_node_replay_rejected -- --test-threads=1
cargo test --test threat_node_bad_participants -- --test-threads=1
cargo test --test threat_share_distribution_adversarial -- --test-threads=1

# Property tests
cargo test --test prop_protocol_properties -- --test-threads=1
cargo test --test prop_ntt_identity -- --test-threads=1

# Lint and format
cargo clippy --all-targets -- -D warnings
cargo fmt --check
```

Specific numerical pass counts are intentionally omitted to avoid
implying a fixed completion measure. Reviewers with core-repo access
see the full per-test output.

## What this page does not claim

- It does not claim audit completion.
- It does not claim production custody readiness.
- It does not claim Sui testnet deployment.
- The Sui adapter is not exercised in any of the tests listed above;
  the adapter is planned for the next validation milestone — see the
  [Sui integration status](sui-integration-status.md).
