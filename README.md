# experienceisexpensive.github.io

Source for the **Experience is Expensive** CoRL 2026 workshop website,
served at <https://experienceisexpensive.github.io>.

## Structure

- `index.html` — single-page site
- `style.css` — styles
- `.nojekyll` — tells GitHub Pages to serve files as-is (skip Jekyll processing)

## Local preview

Open `index.html` directly in a browser, or run a local server:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy

Pushing to `main` publishes automatically once GitHub Pages is enabled:

```bash
gh api repos/experienceisexpensive/experienceisexpensive.github.io/pages \
  --method POST \
  -f source='{"branch":"main","path":"/"}'
```

## Editing

All content lives in `index.html` — update the speakers, schedule,
call-for-papers dates, and organizer list (look for the `TBD` /
`Placeholder` markers).

## Switching to Jekyll later

Delete `.nojekyll`, add a `_config.yml` + `Gemfile`, and pick a theme
(e.g. [al-folio](https://github.com/alshedivat/al-folio) or
[minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)).
