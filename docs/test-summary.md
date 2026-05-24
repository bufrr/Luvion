# Test summary

The core protocol implementation lives in a private repository. This
page is a traceable snapshot of the test state on the date listed
below.

## Snapshot

| Field | Value |
|---|---|
| Snapshot date | 2026-05-24 |
| Toolchain | `rustc 1.93.1` / `cargo 1.93.1` |
| Internal commit identifier | shared with reviewers at access-grant time |
| Test execution environment | Linux x86_64, single-host 33-node cluster |
| Known failures | None as of the snapshot date |
| Last open blocker | Closed prior to the snapshot date |

## Categories (status: passing on the snapshot)

| Category | Status |
|---|---|
| TCP cluster | passing |
| Node connectivity | passing |
| Network probe | passing |
| `t0` prefetch | passing |
| Idle-connection handling | passing |
| Retry / timeout semantics | passing |
| Libp2p runtime path | passing |
| View-change / coordinator failover | passing |
| Replay / nonce safety | passing |

## Test commands (run in the private core repo)

```
cargo test --lib -- --test-threads=1
cargo test --features libp2p-runtime --lib libp2p_runtime:: -- --test-threads=1
cargo test --bin node -- --test-threads=1
cargo test --bin gen_shares -- --test-threads=1
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
