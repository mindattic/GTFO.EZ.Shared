---
codex: 1
project: GTFO.EZ.Shared
code: GES
layer: stories
status: living
updated: 2026-10-20
---
<!-- GENERATED from MindAttic.Tickets/data/Tickets.db by `tickets db render`. Do not edit: this file is rewritten from the database; change stories and tickets with the tickets CLI. -->

# GTFO.EZ.Shared — User Stories
> ✅ done (shipped & tested) · 🟡 partial · ⬜ planned. Every ✅ cites the test.

## Priority backlog
_Nothing recorded yet._

## Tickets
> Permanent log of every change and fix — this repo's ticket system. Rows are append-only: never
> delete or reword one; only move its Status (open → closed / wont-do) and fill in Ref. Status is
> a word, not a glyph, so tickets don't count toward the story index. Keep this section last.

| ID | Date | Type | Status | Summary | Ref |
|---|---|---|---|---|---|
| GES-T1 | 2026-10-20 | docs | closed | Start the permanent ticket log in the workflow database | — |
| GES-T2 | 2026-10-20 | docs | open | Publish GTFO.EZ.Shared docs to GitHub Pages via the shared Agency DocFX pipeline: run adopt-docs-site.ps1 (README.md as home page, docs/*.md as articles, API reference only where the code builds in CI), enable Pages with build_type=workflow, set the repo homepage URL, retire tools/build-readme.ps1 and README.htm, confirm the docs Actions run is green and https://mindattic.github.io/GTFO.EZ.Shared/ returns 200. Depends on MAT-T8. | — |
| GES-T3 | 2026-10-20 | chore | open | Bug hunt: run an exhaustive /bughunt over the whole repo and fix every real bug found (each fix under its own fix ticket), then hunt again; close this only when a full pass finds nothing | user request 2026-10-20: approved repo sweep gap-fill |
| GES-T4 | 2026-10-21 | chore | closed | Add docs | — |
| GES-T5 | 2026-10-24 | docs | closed | Update USER_STORIES.md | — |
