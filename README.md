# experienceisexpensive.github.io

Source for the **Experience is Expensive** CoRL 2026 workshop website,
served at <https://experienceisexpensive.github.io>.

A single-page static site — plain HTML/CSS, no build step.

## Structure

- `index.html` — the whole page (content + a small scroll-spy script at the bottom)
- `style.css` — styles (Hyde-inspired fixed sidebar + scrolling content)
- `assets/` — logo and placeholder avatar images
- `.nojekyll` — tells GitHub Pages to serve files as-is (skip Jekyll processing)

## Local preview

With [mise](https://mise.jdx.dev) (pins Node, gives live-reload on save):

```bash
mise run serve   # runs live-server, opens a browser, reloads on every change
```

Or without mise, any static server works, e.g.:

```bash
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Deploy

Hosted on GitHub Pages from `main` (root path). **Pushing to `main` publishes
automatically** — there's no CI or deploy script. Allow ~1 minute, then hard-refresh
to bust the CDN cache.

## Editing

All content lives in `index.html`. The copy is currently lorem ipsum with `TBD`
dates — replace it section by section (About, Speakers & Panelists, Schedule, Call
for Papers, Important Dates, Organizers).

- **People photos:** speakers/organizers use circular avatars that share
  `assets/avatar-placeholder.svg`. Drop in a real headshot and point each `src` at it —
  images are clipped to circles via CSS, so they don't need to be pre-cropped round.
- **Accent color:** coral `#c75d59`, repeated in `style.css`; replace all occurrences to
  recolor.

## Switching to Jekyll later

Delete `.nojekyll`, add a `_config.yml` + `Gemfile`, and pick a theme
(e.g. [al-folio](https://github.com/alshedivat/al-folio) or
[minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)).
