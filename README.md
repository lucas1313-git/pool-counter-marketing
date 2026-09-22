# Pool Master Counter — Marketing Site

A single-page investor/marketing overview for [Pool Master Counter](https://github.com/lucas1313-git/Pool-master-counter), the live pool/billiards scoreboard app.

Static HTML/CSS, no build step, no dependencies — matches the main app's own philosophy.

## Running it

- **Locally:** open `index.html` in a browser, or serve the folder (e.g. `python3 -m http.server`) and visit it.
- **Online:** enable GitHub Pages for this repo (Settings → Pages → deploy from the `main` branch).

## Structure

- `index.html` — the entire page (markup, styles, and copy), themed in the app's own **Pearl Lounge** palette (same CSS custom property values as the app's `:root[data-theme="pearl-lounge"]`)
- `business-plan.html` — the full business plan, re-themed to match
- `assets/screenshots/` — real product screenshots, synced from the main app's `docs/screenshots/`
- `assets/icons/` — app icon/favicon, sourced from the main app's `icons/`
- `assets/demo/` — the narrated feature-walkthrough video

## Circled screenshots

A handful of screenshots have a gold circle overlay (`.callout` in `index.html`) pointing at the specific control being described in the adjacent copy — positioned as percentages of the image's own dimensions so it stays aligned at any responsive width. When swapping in a new screenshot, either remove its `.callout` div or re-measure the position against the new image.

## League Play section

The League system (standings, teams, multi-table hosting, and APA/BCA/VNBA/TAP handicapping) has its own showcase section (`#league` in `index.html`), built from real screenshots (`assets/screenshots/league-*.jpg`) captured live from the app itself, seeded with sample data via `localStorage` and shot headlessly (Chrome + `puppeteer-core`, not the Claude-in-Chrome extension — useful if the extension is ever unavailable again). Each screenshot sits in a `.league-shot` frame (same treatment as `.showcase-shot`, just with a taller `max-height` for the tall handicap-modal shots) with a `.callout` circle over the specific control being described.

## Demo video

`assets/demo/pool-master-counter-demo.mp4` predates the League system — it covers everything before that. Re-recording it (new scenes + updated narration) needs live screen capture via browser automation, which wasn't available when the League showcase above was built.
