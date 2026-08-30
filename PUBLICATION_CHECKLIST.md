# BranchForge — Publication, Security, and Privacy Review

## Review status

- The case-study text is based on the repository structure, source, documentation, configuration, tests, release files, and Git history.
- The portfolio repository contains documentation and sanitized screenshots only; it does not contain a copy of the BranchForge source.
- Screenshots were captured from a temporary local clone with synthetic branch names, changes, and a demonstration commit.
- A filename/content-pattern scan did not identify a literal credential value in the reviewed tracked source. It did identify credential-handling and configuration files that should remain off screen.
- Mikhail confirmed his role as creator and sole developer; repository history independently attributes all 106 commits to one contributor.
- Mikhail confirmed testing on macOS and Debian 12/13.
- Linking to the public `galetaa/BranchForge` source repository is approved.

## Safe to publish

- Project name and high-level description.
- Independent-product framing and the statement that the work predates its Oferli portfolio entry.
- Developer-tool/Git-client category.
- High-level architecture and crate responsibilities.
- The fact that native desktop, local browser, and console interfaces share one runtime.
- The central `git_service` boundary and documented dependency rules.
- Implemented feature categories: status, staging, diff, history, branches, tags, compare, advanced Git operations, plugins, diagnostics, recovery, and release tooling.
- High-level safety model: confirmations, journal, reference snapshots, backup refs, and recovery actions.
- Process-isolated plugin architecture, manifest compatibility, permissions/risk metadata, and signature verification.
- Rust 2024, eframe/egui, HTML/CSS, Serde, Git CLI, OpenSSL, and GitHub Actions.
- CI steps visible in the public workflow: dependency guards, rustfmt, Clippy, and workspace tests.
- Workspace lint policy forbidding unsafe Rust and denying selected debug/placeholder/unwrap usage.
- Source-level count of 327 Rust test functions, clearly labeled as a count rather than test coverage.
- Public tags `v0.1.0-mvp` and `v1.0.1`.
- Public `v1.0.1` Linux x86_64 artifact and verification-file categories.
- Sanitized screenshots in `assets/screenshots/`.
- High-level code-walkthrough areas listed in `VIDEO_WALKTHROUGH.md` after a final frame-by-frame review.

## Do not publish / verify first

- **Any `.env` file** — none is included in this case-study repository; never add one.
- **Credentials and tokens** — provider tokens, OAuth data, Git credential values, keyring entries, and authenticated response payloads must remain private.
- **`crates/app_host/src/credentials.rs`** — credential-handling source; do not show in a public walkthrough even though the original repository is public.
- **`.cargo/config.toml`** — configuration file; verify manually for machine-specific or sensitive values before it appears on screen.
- **Signing material** — never publish private keys, certificate secrets, key-generation output, or local signing paths. Public verification keys and checksums may be shown only when they are already intended for release verification.
- **Private URLs and remotes** — do not show private Git remotes, provider endpoints, authenticated pull-request URLs, or internal mirrors.
- **Absolute personal paths** — terminal prompts, editor tabs, recent-project menus, logs, and screenshots must not show usernames or home-directory paths.
- **Git author emails** — the original history includes personal author metadata; use the filtered sanitized history screenshot and do not display email-bearing history views.
- **User repository contents** — demonstrations must use the isolated clone and synthetic changes, never a private customer or employer repository.
- **`target/` and packaged binaries** — generated output is not needed in the portfolio and may contain machine-specific paths or metadata.
- **`.idea/` or other editor state** — exclude editor metadata, workspace state, and recent-file information.
- **`PROJECT_IMPLEMENTATION_REPORT.md`** — currently an untracked local analysis file; do not copy or publish without a separate review and explicit approval.
- **Raw logs and crash reports** — verify for paths, repository data, command arguments, and environment information before showing.
- **Provider integration details** — describe GitHub/GitLab-oriented support at a high level; verify any live account or API demonstration before publishing.
- **Plugin registry contents** — verify registry URLs, package paths, signatures, and publisher identity before showing a non-synthetic registry.
- **Future sandbox claims** — documentation mentions a future WASM capability model; do not describe it as implemented.
- **Cross-platform support claims** — macOS and Debian 12/13 were confirmed as tested. The public packaged artifact verified during review is Linux x86_64; do not claim validation on other systems.
- **Business metrics** — commercial and measurable business outcomes are not disclosed and should remain outside the case study.
- **License presentation** — Cargo metadata declares MIT, but no root `LICENSE` file was found. Confirm and add the intended license file to the source repository before making a strong public licensing claim.

## Visual assets checklist

| Asset | What it demonstrates | Publication status |
|---|---|---|
| `01-status-workspace.png` | Redesigned desktop hierarchy, repository status, staging, navigation, and capability-aware controls | Ready; synthetic local data |
| `02-focused-diff.png` | Focused diff inspection and hunk/line workflow | Ready; synthetic change |
| `03-history.png` | History filtering and commit controls | Ready after confirming only the synthetic author is visible |
| `04-branch-management.png` | Branch creation, checkout, rename/delete controls, and collapsed advanced refs | Ready; synthetic branches |
| `05-operation-journal.png` | Successful operation record, runtime snapshot, and local recovery-oriented visibility | Ready; temporary paths only |
| `06-compare.png` | Ahead/behind calculation, synthetic commit, and combined ref diff | Ready; synthetic commit/change |
| `07-diagnostics-plugins.png` | Capability checks, plugin controls, runtime operations, and disabled LFS state | Ready; no installed private plugins |
| Architecture diagram | Shared runtime, central Git boundary, plugin processes, and safety layers | Ready; high level only |
| Product GIF/video | Open → status → diff → compare → journal flow | Not yet recorded; follow `VIDEO_WALKTHROUGH.md` |

## Final publication actions

- [x] Confirm the developer role as Creator and the complete personal implementation scope.
- [x] Confirm that the original public source repository and GitHub handle may be linked.
- [x] Confirm macOS and Debian 12/13 as tested systems.
- [x] Keep commercial and measurable business outcomes undisclosed.
- [ ] Confirm plugin usage outside the sample/bundled set.
- [ ] Resolve the missing root license file in the source repository or soften license wording.
- [ ] Review every screenshot at full resolution for names, emails, paths, URLs, and notifications.
- [ ] Record and review the optional 3–7 minute walkthrough.
- [ ] Replace the portfolio-card placeholder with the final Oferli case-study URL.
- [ ] Keep the case-study repository private until all confirmation items are resolved.

## Questions for Mikhail before publication

1. Was external-plugin installation used beyond the included sample/template?
2. Should the source repository receive a root MIT license file before wider promotion?
