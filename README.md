# github_setup

Language-agnostic guidelines and pre-built templates for setting up a GitHub repository well: branching, releases, milestones, issues, and rulesets.

## Docs

| Doc | Covers |
|---|---|
| [docs/releases-and-tags.md](docs/releases-and-tags.md) | SemVer, `dev` → `staging` → `main` flow, release candidates, cutting releases, tag rules |
| [docs/milestone.md](docs/milestone.md) | One milestone per release tag, triage workflow, CLI commands |
| [docs/issues.md](docs/issues.md) | Issue conventions, labels, triage, linking PRs |
| [docs/rulesets.md](docs/rulesets.md) | Branch and tag rulesets for `main` / `staging` / `dev` |

## Templates (`.github/`)

- [`PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md) — Conventional Commits title, checklist, issue linking
- [`ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE) — minimal bug report and feature request forms

## Usage

Copy what you need into your repo — everything here is language-agnostic. `.github/` contents work as-is; docs describe the conventions they assume.
