# Agent Guidelines for Enroute

## Rules

- Read the minimal local context required for the task.
- Keep changes scoped and avoid unrelated refactors.
- When writing comments or documentation, strictly follow the Google Developer Documentation Style Guide (https://developers.google.com/style), and strongly prefer Simplified Technical English (ASD-STE100) over any existing language register.
- Keep comments extremely brief. Explain WHY, never WHAT. If it just restates the code or narrates history, it's not needed.

## Tuist

`tuist.toml` connects this workspace to the public [enroute/enroute](https://tuist.dev/enroute/enroute) project. Use a Tuist CLI build that includes `tuist cargo` and the Rust version in `rust-toolchain.toml`.

- Build and report compilation and cache metrics: `tuist cargo build --workspace --locked`.
- Run tests and report test results: `tuist cargo nextest run --workspace --locked`. Install `cargo-nextest` first.
- Sign in locally with `tuist auth login`. Do not commit tokens.
- For GitHub Actions, connect the repository in Tuist and grant the job `id-token: write` to use OIDC without a stored token.

The experimental compiler cache is automatic. It supports eligible registry leaf libraries, not all Rust compilations. Local runs can read the remote cache and write the local cache. Remote uploads require a push to a protected GitHub branch. A warm Cargo target directory can skip compilation without consulting Tuist's cache.
