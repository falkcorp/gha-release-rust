<!-- file: .github/copilot-instructions.md -->
<!-- version: 2.4.0 -->
<!-- guid: 4d5e6f7a-8b9c-0d1e-2f3a-4b5c6d7e8f9a -->
<!-- last-edited: 2026-06-13 -->

# gha-release-rust — Additional Context

Org-wide coding standards (file headers, language rules, commit format) are at
**https://github.com/falkcorp/.github** and apply automatically to this repo.

For full project context: **CLAUDE.md** at the repo root.

## Project overview

GHA composite action: Rust binary release builds. Consumes a `Cargo.toml`-based
crate and runs format check, clippy, tests, build, and optional crates.io publish
in a single composite step. Language: Shell/YAML.

## Critical constraints

- All GitHub Action `uses:` references must be pinned to a full commit SHA, not
  a tag.
- The `crate-token` input controls publish: empty or `dummy-no-publish` skips it.
- `dry-run: true` is the default — callers must explicitly set `dry-run: false`
  to actually publish.
