# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single-page static website for the "Experience is Expensive" workshop at CoRL 2026.
No framework, no build step — plain `index.html` + `style.css` + `assets/`. The site is
intentionally raw HTML/CSS so it can be edited and previewed instantly. `.nojekyll`
tells GitHub Pages to serve files as-is rather than running them through Jekyll.

## Develop

The repo pins Node via `mise` and exposes a live-reload dev server as a mise task:

```bash
mise run serve   # runs `npx live-server`, opens a browser, reloads on every save
```

There is no test/lint/build step — editing the HTML/CSS is the entire workflow.

## Deploy

Hosted on GitHub Pages from the `main` branch, root path. **Pushing to `main`
publishes automatically** (live at https://experienceisexpensive.github.io, ~1 min lag;
hard-refresh to bust the CDN cache). There is no CI and no deploy script — the push *is*
the deploy. The repo name `experienceisexpensive.github.io` is what makes the bare-domain
URL work, so it must not be renamed.

Commits in this repo must disable GPG signing (the user's global setting stalls on a key
prompt): `git -c commit.gpgsign=false commit -m "…"`.

## Layout & conventions

The page is a fixed dark sidebar (`.sidebar`, left) + scrolling content (`.content`, right);
on narrow screens the sidebar collapses to a full-width header on top (breakpoint `48em`).

- **Single-page nav.** Sidebar links are in-page anchors to `<section>` ids. A small
  vanilla-JS block at the bottom of `index.html` handles two things that must stay in
  sync: (1) clicking a nav item scrolls the target section to the *center* of the
  viewport, and (2) a scroll-spy bolds the nav link for the section crossing the viewport
  center. Both key off the viewport center deliberately — if you change one, change the
  other or the highlighted link won't match the centered section. Top/bottom overrides
  keep the first/last sections highlighted at the scroll extremes.
- **Accent color** is coral `#c75d59` (darkened from the CoRL Austin logo's coral). It's
  repeated literally in `style.css` (links, schedule/date highlights) — grep and replace
  all occurrences to recolor.
- **People grids** (speakers, organizers) use `.people` / `.person` with circular avatars
  (`border-radius: 50%` + `object-fit: cover`, so source images need not be pre-cropped
  round). All currently point at the shared placeholder `assets/avatar-placeholder.svg`;
  swap each `src` for a real headshot later.
- **Content is placeholder.** Body copy is lorem ipsum and dates are `TBD` pending real
  content. The workshop title and the "2026 Workshop" logo caption are real branding, not
  placeholders.
