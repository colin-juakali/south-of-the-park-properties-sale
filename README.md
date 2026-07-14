# Tuala/Kitengela land sale site

A static marketing site listing three freehold land parcels for sale near
Tuala/Kitengela, Kajiado County, Kenya, on the southern border of Nairobi
National Park. No build step, no server, no JS framework — just hand-written
HTML and one shared CSS file.

**Live site:** https://south-nnp-properties-sale.github.io

## Quick start

Open any file in `docs/` directly in a browser, or serve the folder locally:

```
python3 -m http.server -d docs 8000
```

Then visit `http://localhost:8000`.

## How the site is put together

Everything lives in `docs/` because GitHub Pages can only serve from the repo
root or a `/docs` folder — this repo uses `/docs` on `main`.

| File | Purpose |
|---|---|
| `docs/index.html` | Landing page — intro blurb + a "ledger" of all three parcels (Plot A/B/C), each linking to its detail page. |
| `docs/farm.html` | Plot A — the farm plot (near the SGR embankment). |
| `docs/river-frontage.html` | Plot B — the river frontage plot (borders the park). |
| `docs/roadside.html` | Plot C — the roadside plot (fronts the main road; pitched for commercial use too). |
| `docs/location.html` | Shared location/access page — embedded Google Map + landmark list, linked from every detail page. |
| `docs/style.css` | One shared stylesheet. All colors/fonts are CSS custom properties in `:root` (`--ink`, `--paper`, `--forest`, `--rust`, `--river`, plus `--serif`/`--sans`/`--mono` font tokens) — change the look by editing these tokens, not by hardcoding values in HTML. |
| `docs/photos/` | Real photos and galleries used on the site. |
| `docs/favicon*`, `docs/apple-touch-icon.png` | Browser/tab icons. |

Every page repeats the same building blocks — when adding a page, copy an
existing one rather than starting from scratch:

- **`.masthead`** — header with site title and contact line, identical on
  every page.
- **`.hero` / `.ledger`** (index page only) — intro text, then one `.entry`
  per parcel: plot number, a small hand-drawn SVG sketch, description, stats
  line, and a link to the detail page.
- **`.detail`** (detail pages) — a `.back-link` to the index, a
  `.detail-header` (the *same* SVG sketch as the index card, plus
  title/location/status), a two-column `.detail-body` (land/location/
  infrastructure copy on the left, an "at a glance" `.sidebar-box` + contact
  box on the right).
- **`footer`** — identical contact/tagline strip on every page.

Each parcel has a small hand-drawn SVG sketch (property outline plus one
distinguishing feature — SGR embankment for the farm, river bend for the
river frontage plot, road line for the roadside plot). The **same sketch
appears twice**: once on the index card, once on that parcel's detail page
header. If you redraw one, update both copies.

## Content that's duplicated on purpose

- **Contact details** — `tuala.farm.sale@gmail.com`, `+254 795 916 278`, and
  the WhatsApp link (`wa.me/254795916278`) appear in the masthead, as
  `mailto:`/`tel:`/`wa.me` links, and in the footer, on *every* page. There's
  no shared include (no build step), so if contact info changes, update it
  everywhere — a quick way to find every occurrence:
  ```
  grep -rn "tuala.farm.sale@gmail.com\|795 916 278" docs/
  ```
- **Prices** are shown as "POA" (price on application) throughout — there are
  no numeric prices anywhere in the content.

## Where things stand / what's next

`NOTES.md` in the repo root is a running list of marketing and follow-up
ideas (QR-code signage, Open Graph tags, cross-listing on other property
sites, etc.) — check there before starting new work.

`working/` is a git-ignored scratch folder for raw/unprocessed photos before
they're cropped and dropped into `docs/photos/`.

## For Claude Code

`CLAUDE.md` has the same architecture notes aimed at an AI coding agent. Keep
the two in sync if the structure changes — this README is the version for
humans, CLAUDE.md is tuned for how Claude Code should behave when editing
this repo.
