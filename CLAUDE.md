# CLAUDE.md

This file guides Claude Code and other coding agents working in this repository.

## Workflow rule (always)

No matter what the request is, **always present a plan and get explicit approval before
making any code changes.** Outline the intended steps first, wait for the user to approve,
and only then edit files / commit / push. Do not start modifying code without that approval.
Existing explicit user authorization for the current task applies; do not ask for the same
authorization again.

## Project

Gökhan Kaya's personal portfolio, **Kod × Saha**, connects software engineering,
AI-assisted development and volleyball. GitHub Pages publishes `main` at
`https://gokhankaya.net`. The separate Sites-hosted edition has its own origin and
owner-private access. A GitHub Pages merge does not update Sites automatically.

## Structure

- `index.html`: complete homepage, with inline CSS and JavaScript.
- `voleybol/index.html`: bilingual volleyball story, with inline CSS and JavaScript.
- `img/`: existing profile assets.
- `cv/Gokhan-Kaya-CV.pdf`: existing CV; do not regenerate it as part of a design edit.
- `CNAME`: `gokhankaya.net`; keep it on the published branch.
- No framework, package manager, build step or test suite is required.
- Fonts are CDN-loaded DM Sans and DM Mono, with local system fallbacks.

## UI and content conventions

- Warm off-white, navy and orange; large editorial typography and responsive layouts.
- CSS variables on `:root` and `[data-theme="dark"]`; update both themes for new colors.
- Theme preference: `gk-theme`; language preference: `gk-lang`.
- Static Turkish content is present in the HTML. `data-en` carries the English version.
  Both pages share the preferences, so navigation should preserve them.
- Homepage projects and notes open native `<dialog>` elements with keyboard dismissal.
- Volleyball page includes a player/coach perspective switch. Its court is illustrative.
- Keep factual claims grounded. Do not invent clubs, awards, results, testimonials,
  qualifications or launched capabilities.
- SportPlatform is in development; VolleyReplay is at MVP design stage.
  Replay latency is a hypothesis, not a measured result.

## AI communication and operations branches

The user requested these long-lived branches:

- `ai-communication`: agent handoffs, review requests, decisions and responses.
- `ops`: deployment records, backup references and rollback instructions.
- `backup/pre-kod-saha-2026-10-25`: preserved pre-redesign snapshot.
  Do not commit new work to or repoint the backup branch.

Before resuming work, fetch those branches and inspect:
`git show origin/ai-communication:AI_COMMUNICATION.md` and
`git show origin/ops:RUNBOOK.md`.

Respond to review requests on `ai-communication` with your actual identity, reviewed
commit SHA, findings and verification evidence. A handoff file does not launch another
agent automatically and does not prove that a review happened. Never attribute a response
to another agent without receiving it. Put implementation changes on a feature branch and
open a PR to `main`; do not merge the whole communication or operations branch into production.

## Preview and validation

Run `python3 -m http.server 8000` in a local checkout and open
`http://localhost:8000`. Check both pages at desktop and mobile widths, Turkish/English,
light/dark themes, keyboard navigation, dialogs, perspective switch, CV and local links.
Use JavaScript syntax and internal-reference checks when editing scripts or navigation.

## Publishing and rollback

GitHub Pages serves `main`; a branch alone is not a production deployment.
Preserve `CNAME`, CV and existing assets. Confirm the Pages deployment and both pages
after release. For a rollback, use a new branch and restore the changed files from the
documented backup, then deploy through a PR. Do not rewrite `main` history.
The detailed procedure and release evidence live on `ops`.
