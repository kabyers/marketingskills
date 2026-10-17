# About this mirror

This repo is an automatically synced mirror of
[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills)
by Corey Haines, used under its MIT license (see `LICENSE`). All skill content
is his; `README.md` is his original.

## What syncs

A GitHub Actions workflow (`.github/workflows/sync-upstream.yml`) runs daily at
09:17 UTC. It copies these paths from upstream and commits only when something
changed:

- `skills/` — the 50+ skills
- `tools/` — integration guides the README links to
- `.claude-plugin/` — the Claude Code plugin and marketplace manifests
- `LICENSE`, `README.md`, `VERSIONS.md`

Upstream's workflows, tests and scripts are not copied, so none of them run here.

To sync immediately: **Actions → Sync from upstream → Run workflow**, or
`gh workflow run sync-upstream.yml -R kabyers/marketingskills`.

Anything you add inside the synced paths is overwritten on the next sync. Keep
your own additions in other folders.

## Using it with Claude Code

Install once at user scope, and the skills are available in every repo:

```
claude plugin marketplace add kabyers/marketingskills
claude plugin install marketing-skills@marketingskills --scope user
```

Pull in the latest synced version:

```
claude plugin marketplace update marketingskills
claude plugin update marketing-skills@marketingskills
```

Then restart Claude Code. Skills appear as `marketing-skills:<name>`, for
example `marketing-skills:seo-audit`.

## If syncing stops

GitHub pauses scheduled workflows in a public repo after 60 days with no
activity. The sync's own commits count as activity, so this only happens if
upstream goes quiet for two months. Re-enable it under
**Actions → Sync from upstream**.
