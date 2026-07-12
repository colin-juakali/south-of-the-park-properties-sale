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

- `docs/index.html` — landing page listing all three parcels ("Plot A/B/C") as entries linking to their detail pages.
- `docs/farm.html`, `docs/riverside.html`, `docs/roadside.html` — one detail page per parcel (Plot A/B/C respectively).
- `docs/location.html` — shared location/access page (embedded Google Maps iframe + landmark list) linked from each detail page.
- `docs/style.css` — single shared stylesheet for all pages, driven by CSS custom properties defined in `:root` (`--ink`, `--paper`, `--forest`, `--rust`, `--river`, etc.) plus three font-family tokens (`--serif` Fraunces, `--sans` Work Sans, `--mono` IBM Plex Mono). Change the design by editing tokens here rather than hardcoding colors/fonts in HTML.

Every page repeats the same structural pattern — copy an existing page rather than building one from scratch:
- `.masthead` — site header with title and contact line (email + phone), identical on every page.
- Index page only: `.hero` intro blurb, then `.ledger` containing one `.entry` per parcel (plot number, inline hand-drawn SVG sketch in `.sketch-box`, description, stats line, link to detail page).
- Detail pages: `.detail` wrapper with `.back-link` back to index, `.detail-header` (same SVG sketch as the index card + title/loc/status-row), `.detail-body` two-column layout (land/location/infrastructure copy on the left, `.sidebar-box` "at a glance" summary + `.enquire` contact box on the right), and a `.photo-note` placeholder where real photos will eventually replace the Flickr links.
- `footer` — identical contact/tagline strip on every page.

Each parcel's hand-drawn SVG sketch (property outline + distinguishing feature: SGR embankment for the farm, river bend + park label for the riverside plot, road line for the roadside plot) is duplicated between the index card and that parcel's detail-page header — keep both copies in sync if a sketch changes.

## Content notes

- Contact details (`tuala.farm.sale@gmail.com`, `+254 795 916 278`) are repeated verbatim in the masthead, `mailto:`/`tel:` links, and footer of every page — update all occurrences together.
- Prices are listed as "POA" (price on application) throughout; there are no numeric prices in the content.
- Photos aren't hosted in this repo yet — pages currently link out to Flickr albums or show a `.photo-note` placeholder. If adding real images, use the existing `img.field-photo` class in `style.css`.
