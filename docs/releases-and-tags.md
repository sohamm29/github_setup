# Releases & Tags

## Versioning

Use [SemVer](https://semver.org): `vMAJOR.MINOR.PATCH`

- `MAJOR` — breaking change
- `MINOR` — new feature, backwards compatible
- `PATCH` — bug fix only
- Pre-releases: `v1.4.0-rc.1`, `v1.4.0-rc.2`, …

## Branch model

```
feature/* ──PR──> dev ──PR──> staging ──PR──> main
                              (tag RCs)       (tag releases)
```

- `dev` — integration branch; all feature/fix PRs target this.
- `staging` — release stabilisation; only bug fixes after cut. Tag `vX.Y.Z-rc.N` here.
- `main` — production; every merge from staging gets a final tag `vX.Y.Z`.
- Hotfixes: branch from `main`, PR to `main`, tag `vX.Y.(Z+1)`, then merge back to `staging`/`dev`.

## Tags

Always **annotated** tags (they store author, date, message; lightweight tags don't):

```bash
git tag -a v1.4.0 -m "Release v1.4.0"
git push origin v1.4.0
```

- Tags are immutable: never delete/re-point a published tag — release a new patch instead.
- Protect tags matching `v*` with a tag ruleset (see [rulesets.md](rulesets.md)).
- Optionally sign: `git tag -s v1.4.0 -m "..."`.

## Cutting a release

1. Merge `dev` → `staging`. Tag `v1.4.0-rc.1`.
2. Test staging. Fixes go to `staging` (cherry-pick back to `dev`), tag `-rc.2`, etc.
3. Merge `staging` → `main`. Tag `v1.4.0`.
4. Create the GitHub Release with generated notes:

```bash
gh release create v1.4.0 --verify-tag --generate-notes           # final
gh release create v1.4.0-rc.1 --verify-tag --generate-notes --prerelease  # RC
```

5. Close the `v1.4.0` milestone, create the next one (see [milestone.md](milestone.md)).

## Release notes

Auto-generated notes group PRs by label if `.github/release.yml` exists. Keep PR titles in Conventional Commits format so notes read well.
