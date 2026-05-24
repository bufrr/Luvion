# Test summary

The core protocol implementation lives in a private repository. The
following categories pass on the current core-repo branch.

## Categories

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

- `cargo test --lib -- --test-threads=1`
- `cargo test --features libp2p-runtime --lib libp2p_runtime::`
- `cargo clippy --all-targets -- -D warnings`
- `cargo fmt --check`

These commands are listed for reviewers who get access to the private
repo. Specific numerical counts are intentionally omitted to avoid
implying a fixed completion measure.

## What this page does not claim

- It does not claim audit completion.
- It does not claim production custody readiness.
- It does not claim Sui testnet deployment.
