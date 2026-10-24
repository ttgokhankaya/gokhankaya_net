# Gökhan Kaya — Kod × Saha

Personal portfolio at **https://gokhankaya.net**, connecting software engineering, AI-assisted development and volleyball.

## Contents

- Professional introduction, existing profile photo and downloadable CV
- SportPlatform and VolleyReplay project concepts with detailed background
- Engineering notes on agent behavior contracts, regression replay and courtside product design
- Career, education, volleyball story and contact links
- Turkish/English language switch, light/dark theme and responsive navigation

Project visuals are conceptual illustrations. VolleyReplay is described as an MVP design; its latency target is an unverified hypothesis.

## Structure

- `index.html`: complete main page with inline CSS and JavaScript; no build step or dependencies to install
- `img/gokhanKaya.jpeg`: existing profile photo
- `cv/Gokhan-Kaya-CV.pdf`: existing CV
- `voleybol/index.html`: redesigned Turkish/English volleyball story with shared theme/language preferences and an interactive player/coach perspective
- `CNAME`: GitHub Pages custom domain

## Preview

Run `python3 -m http.server 8000` from the repository root and open `http://localhost:8000`.

## Publishing

GitHub Pages publishes the `main` branch to `gokhankaya.net`. Changes in a feature branch become live on that domain after merge. Keep `CNAME` on the published branch. The separate Sites-hosted edition uses its own origin for canonical and Open Graph URLs.

## Validation

The redesign was checked in a desktop browser and a 390px mobile-width frame, including language/theme switching, mobile menu, project/note dialogs, Escape dismissal, internal references and JavaScript syntax. Theme and language preferences are stored only in the browser. Contact links open the visitor's mail client; no form backend is required.

## Branches and backup

- `main`: GitHub Pages production source
- `ai-communication`: Codex / Claude Code review requests and responses
- `ops`: publishing, release evidence and rollback runbook
- `backup/pre-kod-saha-2026-10-25`: complete pre-redesign source snapshot at `d6f3047032227200ec156d34c1ce65c7c6434abc`

Read `CLAUDE.md` for working conventions and how to inspect the handoff branches. Communication files are an asynchronous handoff, not an automatic Claude Code integration.
