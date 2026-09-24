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

`assets/demo/pool-master-counter-demo.mp4` predates the League system — it covers everything before that. Re-recording it (new scenes + updated narration) needs live screen capture via browser automation.

`assets/demo/league-play-walkthrough.mp4` covers League Play specifically: an ~87-second Ken-Burns-style tour built from the real `league-*.jpg` screenshots (zoom/pan via ffmpeg `zoompan`), assembled per-scene and concatenated with ffmpeg. It exists as a screenshot-based video rather than a live screen recording because this environment had no authorized `avfoundation` screen-capture device for ffmpeg (macOS Screen Recording permission wasn't granted) — if that's available in a future session, a live-capture re-record of both videos together would be the better long-term version.

**Narration**: uses [`edge-tts`](https://github.com/rany2/edge-tts) (`pip install edge-tts`, free, no API key — pulls Microsoft Edge's neural voices) with `en-GB-RyanNeural` at `--rate=-4%`, not the macOS `say` command — an earlier pass used `say -v Daniel` and it sounded noticeably robotic; edge-tts's neural voices are far more natural. Run `edge-tts --list-voices` for the full catalog if a different voice/accent is ever wanted. The build script lived in `/tmp/pmc-capture/video/build_scene.sh` (scratch, not committed); recreate it from this description if regenerating.
