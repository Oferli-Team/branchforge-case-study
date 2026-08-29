# BranchForge — Safe Code Walkthrough Outline

**Target length:** 4–6 minutes  
**Recording environment:** local sanitized demonstration clone only  
**Goal:** demonstrate product depth and engineering quality without exposing credentials, personal information, private repository contents, or machine-specific configuration

## 0:00–0:35 — Project introduction

- Introduce BranchForge as an independent Rust developer tool created before its inclusion in the Oferli portfolio.
- Show the redesigned status workspace using `assets/screenshots/01-status-workspace.png` or the running local demo.
- State the verified product scope: native desktop, local browser, and console interfaces over real Git operations.
- Avoid claims about user count, commercial adoption, performance gains, or production scale.

## 0:35–1:25 — Architecture

Safe and useful areas to show:

- Root `Cargo.toml` — briefly show the workspace members and shared lint policy.
- `docs/architecture/crate_boundaries.md` — explain the ownership of `app_host`, `action_engine`, `job_system`, `state_store`, `git_service`, UI crates, and plugin crates.
- The Mermaid diagram in `README.md` — explain the flow from interface to host, jobs, Git service, repository, and plugin processes.

Key message: all interfaces reuse one runtime, and only `git_service` may execute Git.

## 1:25–2:35 — Git operations and recovery

Safe and useful areas to show:

- `crates/git_service/src/lib.rs` — show only public type/function names and a small, non-sensitive section illustrating centralized command execution or parsed results.
- `crates/job_system/src/lib.rs` — show operation policy, locking, or result/event types at a high level.
- `crates/app_host/src/operations.rs` — show action naming and recovery-related orchestration without revealing any local paths.
- `docs/process/troubleshooting_and_recovery_guide.md` — show the documented recovery concepts.
- Product visuals `02-focused-diff.png`, `05-operation-journal.png`, and `06-compare.png`.

Explain why backup refs, confirmation levels, pre/post snapshots, and journal entries matter for reset/rebase/ref operations. Do not demonstrate a destructive operation against the source repository.

## 2:35–3:30 — Plugin model

Safe and useful areas to show:

- `crates/plugin_api/src/lib.rs` — versioned protocol models and permission metadata.
- `crates/plugin_host/src/lib.rs` — process lifecycle and framed transport at a high level.
- `docs/plugin_marketplace_security.md` — trust states, signature verification, and current process isolation.
- `external_plugins/secure_plugin_template/plugin.json` — manifest structure only, after confirming it contains no local paths.
- Product visual `07-diagnostics-plugins.png`.

State clearly that current plugins are out of process. Do not claim the documented future WASM capability sandbox is implemented.

## 3:30–4:25 — Testing and quality

Safe and useful areas to show:

- `.github/workflows/ci.yml` — dependency guards, formatting, Clippy, and full workspace tests.
- Root `Cargo.toml` — `unsafe_code = "forbid"` and denied `dbg_macro`, `todo`, and `unwrap_used` lints.
- Test directory names under `crates/app_host/tests` and `crates/plugin_host/tests`.
- A terminal showing only the final successful summaries from `cargo test --workspace` and Clippy; hide the shell prompt if it includes a personal path or username.

Describe the verified source-level count of 327 Rust test functions as a count, not a coverage percentage.

## 4:25–5:10 — Release engineering

Safe and useful areas to show:

- `scripts/package-release.sh`, `scripts/sign-artifacts.sh`, and `scripts/verify-beta-package.sh` — filenames and high-level flow only.
- `docs/process/package_verification_v1.0.1.md` and `docs/process/release_regression_matrix_sprint24.md`.
- The public `v1.0.1` GitHub release page, showing package/checksum/signature artifact categories but not local signing configuration.

Explain that the release includes Linux x86_64 packaging and verification artifacts. Do not claim broader platform validation without confirmation.

## 5:10–5:40 — Final result

- Return to the status, compare, and diagnostics visuals.
- Summarize the demonstrated capabilities: Rust product architecture, controlled Git integration, safe advanced operations, plugins, testing, and release automation.
- End with the technical outcome only; leave business outcomes marked as needing confirmation.

## Do not show on screen

- `.env` files or any environment-variable values
- `.cargo/config.toml` until manually reviewed for machine-specific configuration
- `crates/app_host/src/credentials.rs` or credential-store contents
- Provider tokens, OAuth data, keyring entries, private remote URLs, or authenticated API responses
- Private/signing keys, certificate material, or signing commands containing real paths
- Git author email addresses or local Git configuration
- Private repository names or user repository contents
- Absolute personal paths, terminal prompts with usernames, or editor recent-project menus
- `target/`, packaged binaries, crash dumps, or raw logs that have not been reviewed
- `.idea/` and other editor metadata
- The untracked `PROJECT_IMPLEMENTATION_REPORT.md` unless separately reviewed and approved
- Long source-code sections or proprietary code copied into the portfolio repository

## Recording checklist

- Use the sanitized clone at a temporary path and synthetic branches/changes.
- Keep the browser at 100% zoom so the complete desktop interface remains visible.
- Record at the display’s native resolution and export a high-bitrate 1440p or 2160p master if available.
- Use a small desktop-window frame consistent with the published screenshots; do not add resolution/FPS labels.
- Keep cursor movement smooth and purposeful, and click the center of controls after confirming their current position.
- Review every frame for personal paths, email addresses, tokens, repository URLs, and notification popups before publication.
