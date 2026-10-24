# Operations — Kod × Saha

## Branch and release map

| Branch | Purpose |
| --- | --- |
| `main` | GitHub Pages production source |
| `ai-communication` | Agent handoffs and review responses |
| `ops` | This runbook and release evidence |
| `backup/pre-kod-saha-2026-10-25` | Preserved pre-redesign source |

Do not deploy or merge the whole `ops` or communication branch into production.
Do not repoint, force-push or add commits to the backup branch.

## Pre-redesign backup

- Created before merging PR #12.
- Verified branch: `backup/pre-kod-saha-2026-10-25`.
- Commit: `d6f3047032227200ec156d34c1ce65c7c6434abc`.
- Full source tree and history are retained, including homepage, volleyball page,
  CNAME, profile images, CV and previous documentation.
- Verification: remote branch HEAD exactly matched pre-change `main`.

## Release candidate

- PR: https://github.com/ttgokhankaya/gokhankaya_net/pull/12
- Candidate SHA: `25629d025026bda0e9cb8354f383a8b52901c762`
- Public domain: https://gokhankaya.net
- Owner-private Sites edition: https://gokhan-kaya-kod-saha.ttgokhankaya.chatgpt.site
- Claude review request: https://github.com/ttgokhankaya/gokhankaya_net/issues/13
- Release status: pending merge and deployment verification; record actual results below.
- Claude Code review: pending; not a received approval or automated agent run.

## Checks before release

1. Verify the backup branch still points to the documented SHA.
2. Compare the final PR and expected head SHA; confirm it can merge cleanly.
3. Keep `CNAME` set to `gokhankaya.net`.
4. Check homepage and `/voleybol/` at desktop and mobile widths.
5. Exercise TR/EN, both themes, homepage dialogs, player/coach switch, CV and local links.
6. Check GitHub Pages deployment after the merge. Check both live pages. A merged source
   commit by itself is not proof that the hosted content is updated.
7. Publish and verify the separate Sites version when applicable. Keep its audience unchanged.

## Rollback without rewriting history

Use a clean local checkout; preserve any unrelated local changes before switching branches.

```bash
git fetch origin main backup/pre-kod-saha-2026-10-25
git switch -c rollback/pre-kod-saha origin/main
git restore --source=origin/backup/pre-kod-saha-2026-10-25 -- index.html voleybol/index.html README.md CLAUDE.md
git diff --stat
git diff -- CNAME
git add index.html voleybol/index.html README.md CLAUDE.md
git commit -m "Restore pre-Kod-Saha personal site"
git push -u origin rollback/pre-kod-saha
```

Open a PR from the rollback branch to `main`, inspect the diff and merge under the user's
authorization. These four files are the planned redesign scope. If production has changed
since this release, assess those changes before restoring; do not overwrite unrelated work.
CNAME, image assets and CV were not changed by the redesign.

After rollback, verify the Pages deployment and both live pages. Rolling back GitHub Pages
does not roll back the separate Sites edition; deploy its prior saved version separately
if requested. Do not use a history-rewriting reset on `main`.

## Release evidence

Pending execution. Append merge SHA, deployment result, observed live-page checks and any
limitations. Do not record a pending deployment as successful.
