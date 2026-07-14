# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A static, no-build marketing site listing three freehold land parcels for sale near Tuala/Kitengela, Kajiado County, Kenya. There is no server, no package manager, no JS, and no test suite — just hand-written HTML and one shared CSS file in `docs/`.

The site is hosted on GitHub Pages, serving from the `/docs` folder on `main` — hence the folder name (GitHub Pages only supports serving from repo root or `/docs`).

## Running / previewing

There is no build step. Open the HTML files directly in a browser, or serve the `docs/` directory with any static server, e.g.:

```
python3 -m http.server -d docs 8000
```

## Architecture

`docs/` holds one page per parcel (`farm.html`, `river-frontage.html`, `roadside.html` — Plot A/B/C respectively), an `index.html` landing page linking to all three, a shared `location.html`, and one shared `style.css`. Check `docs/` directly for the current file list rather than trusting an inventory here — it drifts (see `README.md` for a human-oriented listing, kept alongside this file).

`style.css` is driven by CSS custom properties in `:root` (ink/paper/forest/rust/river color tokens, plus serif/sans/mono font tokens) — change the design by editing tokens there, not by hardcoding colors/fonts in HTML.

Every page repeats the same structural pattern — copy an existing page rather than building one from scratch, since there's no templating to share markup across files:
- `.masthead` — site header with title and contact line, identical on every page.
- Index page only: `.hero` intro blurb, then `.ledger` containing one `.entry` per parcel (plot number, inline hand-drawn SVG sketch in `.sketch-box`, description, stats line, link to detail page).
- Detail pages: `.detail` wrapper with `.back-link` back to index, `.detail-header` (same SVG sketch as the index card + title/loc/status-row), `.detail-body` two-column layout (land/location/infrastructure copy on the left, `.sidebar-box` "at a glance" summary + `.enquire` contact box on the right).
- `footer` — identical contact/tagline strip on every page.

Each parcel's hand-drawn SVG sketch (property outline + distinguishing feature: SGR embankment for the farm, river bend + park label for the river frontage plot, road line for the roadside plot) is duplicated between the index card and that parcel's detail-page header — keep both copies in sync if a sketch changes.

## Also see

`README.md` covers the same ground for a human reader, including a current file listing. Keep both in sync if the structure changes.

## Content notes

- Contact details (`tuala.farm.sale@gmail.com`, `+254 795 916 278`) are repeated verbatim in the masthead, `mailto:`/`tel:`/WhatsApp (`wa.me/254795916278`) links, and footer of every page — update all occurrences together.
- Prices are listed as "POA" (price on application) throughout; there are no numeric prices in the content.
- Real photos live in `docs/photos/` and are wired up via the `img.field-photo` / `.carousel` markup and classes in `style.css`. `farm.html` also keeps one extra outbound link to a fuller Flickr album — don't assume that pattern applies to the other pages without checking.
