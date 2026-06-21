# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Workflow rule (always)

No matter what the request is, **always present a plan and get explicit approval before
making any code changes.** Outline the intended steps first, wait for the user to approve,
and only then edit files / commit / push. Do not start modifying code without that approval.

## What this is

A single-page static personal portfolio site for Gökhan Kaya (Senior Software Engineer),
deployed via **GitHub Pages** at the custom domain **gokhankaya.net**. There is no build
step, no package manager, no test suite, and no framework — it is plain HTML/CSS/JS.

## Architecture

- **`index.html`** — the entire site. All CSS lives in a single `<style>` block in the
  `<head>` and all JS in a single `<script>` block before `</body>`. There are no separate
  `.css` or `.js` files; edit this one file for any content, styling, or behavior change.
- **`img/`** — avatar/profile images referenced with relative paths (e.g. `./img/gokhanKaya.png`).
- **`CNAME`** — contains `gokhankaya.net`; tells GitHub Pages the custom domain.
- External dependencies are all CDN-loaded (no local copies): Google Fonts (Inter, JetBrains
  Mono), Font Awesome 6.5.2, and Google Analytics (gtag, ID `G-1H7JFTG0WS`).

### Key conventions inside `index.html`
- **Theming** is driven by CSS custom properties on `:root` (light) and `[data-theme="dark"]`.
  The toggle persists choice to `localStorage` under key `theme` and falls back to
  `prefers-color-scheme`. To add a color, add the variable to *both* `:root` and the dark block.
- **Sections** follow a repeated pattern: `<section id="...">` → `.container` → `.section-head`
  (with an `h2` and a `.tag` "// label") → content. The sticky nav links to these `id`s.
- **Scroll reveal**: elements with class `reveal` are animated in by an `IntersectionObserver`;
  add `reveal` to new elements you want to fade in.
- Content (experience timeline, skills chips, education) is hand-written HTML — update the
  markup directly; there is no data file or templating.

## Local development

No tooling required. Open `index.html` directly in a browser, or serve the folder:

```bash
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Deployment & custom domain (important)

- The site is published by **GitHub Pages from the `main` branch**. Changes only go live
  after they land on `main`. Feature branches (e.g. `claude/*`) do not affect the live site
  until merged.
- The `CNAME` file must exist on the **published branch (`main`)** for the custom domain to work.
- For `gokhankaya.net` to resolve, DNS at the domain registrar must point to GitHub Pages —
  apex `A` records to `185.199.108.153` / `185.199.109.153` / `185.199.110.153` /
  `185.199.111.153`, and `www` as a `CNAME` to `ttgokhankaya.github.io`. The custom domain must
  also be set under repo **Settings → Pages**. Pointing DNS elsewhere (e.g. a registrar parking
  IP) is the usual cause of the domain "not working" even when the repo is correct.
