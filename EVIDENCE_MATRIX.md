# BranchForge — Evidence Matrix

This matrix records the repository evidence behind public claims. It is an editorial aid, not a source-code extract.

| Public claim | Repository evidence | Confidence / publication note |
|---|---|---|
| BranchForge is a Rust workspace | Root `Cargo.toml`, workspace member manifests | Confirmed |
| Workspace version is `1.0.1` and uses Rust 2024 | Root `Cargo.toml` workspace package metadata | Confirmed |
| The product has native desktop, browser, and console interfaces | `crates/app_desktop`, `crates/app_gui`, `crates/app_host/src/console_runner.rs`, runtime-usage docs | Confirmed |
| All interfaces share the host/runtime model | `app_host` wiring, `app_gui` runtime usage, `app_desktop` runtime adapter, architecture docs | Confirmed |
| Only `git_service` may execute the Git CLI | `docs/architecture/crate_boundaries.md`, dependency guard, workspace instructions, source references | Confirmed architectural rule |
| Git operations are real rather than mocked | `crates/git_service`, Git fixture/integration tests, locally exercised sanitized repository | Confirmed |
| Status, staging, commit, history, branches, tags, and compare exist | Bundled plugin crates, action catalog, UI forms, app-host smoke/e2e tests | Confirmed |
| Advanced reset/rebase/merge/conflict/recovery workflows exist | App-host operations, job-system policies, advanced-operation smoke/regression tests, recovery docs | Confirmed as implemented surface; avoid claiming every edge case is production-proven |
| Stash, worktree, submodule, and LFS actions exist | Action catalog, GUI forms, advanced-feature tests, capability checks | Confirmed; Git LFS is optional and was unavailable in the screenshot environment |
| The product uses an operation journal and backup refs | Job/operation models, safety regression tests, recovery documentation, GUI journal view | Confirmed |
| Plugins run out of process | `plugin_host`, runtime handshake/contract tests, plugin security documentation | Confirmed |
| Plugin protocol, compatibility, permissions, and signing are modeled | `plugin_api`, `plugin_sdk`, plugin manifests, compatibility/security docs, signature-verification paths | Confirmed |
| A future WASM sandbox is not implemented | `docs/plugin_marketplace_security.md` labels it future work | Confirmed limitation; must remain explicit |
| CI runs dependency guards, rustfmt, Clippy, and tests | `.github/workflows/ci.yml` | Confirmed |
| Unsafe Rust is forbidden and selected Clippy patterns are denied | Root `Cargo.toml` lint configuration | Confirmed |
| Repository contains 327 Rust test functions | Source-level count of `#[test]` and `#[tokio::test]` attributes under crates/plugins | Confirmed count at analysis time; not coverage |
| Release packaging, signing, checksums, and verification are included | `scripts/package-release.sh`, `scripts/sign-artifacts.sh`, verification scripts, release docs | Confirmed repository capability |
| Public release tags include MVP and `v1.0.1` | Git tags and public GitHub release page | Confirmed |
| `v1.0.1` includes Linux x86_64 release artifacts | Public release asset listing and package-verification docs | Confirmed; do not generalize to all platforms |
| Mikhail is the creator and sole developer | Direct developer confirmation; `git rev-list --count HEAD`; `git shortlog` | Confirmed |
| Project is independent rather than client work | Direct developer confirmation and public source ownership | Confirmed |
| The original goal was to make day-to-day Git work more convenient | Direct developer confirmation | Confirmed |
| The project was tested on macOS and Debian 12/13 | Direct developer confirmation | Confirmed; public packaged release verified separately as Linux x86_64 |
| No application database/cache/broker was found | Workspace manifests, crate structure, configuration inventory | Confirmed for reviewed repository |
| OS credential storage and provider-oriented PR support exist | `app_host` credential/provider modules and action surfaces | Confirmed; do not show live credentials/accounts |
| Cargo declares MIT | Root `Cargo.toml` | Confirmed metadata; a root license file was not found, so verify before public licensing claims |
| Commercial or measurable business outcomes | Not disclosed | Do not claim |

## Claim-writing rule

Use a claim as a fact only when the matrix marks it confirmed. Keep limitations attached to the claim. Treat unverified motivations, plugin usage beyond the included examples, broader platform validation, and business outcomes as inferences or omissions.
