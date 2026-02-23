# Croppy – AI assistant instructions

This tiny repo is a **single‑page Progressive Web App** for cropping portrait images to a square. There is no server, build step or framework – all the logic lives in one HTML file and two supporting assets.

## Big picture

* `index.html` is the heart of the project. It contains:
  * inline CSS (`<style>` in `<head>`) for layout and theming
  * vanilla‑JS script near the bottom with sections labelled 1–4 (global events, focus detection, gestures/navigation, workflow).
  * A handful of DOM elements (`#drop-zone`, `#editor`, `canvas`, etc.) whose IDs are referenced directly by the script.
  * A service worker registration snippet at the top of `<head>`.
* `manifest.json` defines the PWA metadata (name, icons, display mode) and is referenced from `<link rel="manifest">`.
* `sw.js` is a minimal service worker that caches `'./'`, `'./index.html'`, and `'./manifest.json'` on install, and serves cached assets on fetch. If you change the cache or asset list, bump `CACHE_NAME` or users may see stale content.
* `README.md` describes usage and now includes PWA information; keep the format and linked line numbers up to date when you modify logic.
* `DEV_NOTES.md` is an agent memory file. Agents may read/write here freely; use it to record decisions, the project commandments, or reminders.

## Workflows & building

* **No build tools**. Modify `index.html` directly and open it in a browser (preferably served over HTTP/HTTPS). For local testing:
  ```bash
  # simple python server
  cd /path/to/croppy && python -m http.server
  # or use any static file server / live‑reload extension
  ```
* PWA features (installable, offline caching) only work when the page is served over http(s); file:// will not register `sw.js`.
* To clear the service worker during development, unregister it via DevTools or increment `CACHE_NAME`.
* There are no tests or CI; regression testing is manual—exercise drag/drop, keyboard shortcuts, HEIC conversion, and offline mode.
* Markdown files (README, DEV_NOTES) are expected to be linted; update them accordingly.

## Project‑specific conventions

* **Line references.** The README links to specific line numbers in `index.html` (for example, drag‑and‑drop logic on line 74 or orientation check on line 209). If you reorganise code, update these references.
* **Cropping logic.** Images are assumed to be portrait; an alert+skip occurs when `img.width >= img.height`. The `detectFocusY` function samples a scaled‑down version of the image to guess the best vertical crop starting point.
* **HEIC support** comes from the CDN script `heic2any@0.0.3`. Conversion happens in `loadCurrent()` if the file type/name indicates HEIC.
* **Navigation gestures/keys.** The gesture code is contained in the commented sections; swiping left/right on touch or pressing arrow keys triggers `skip()`, `undo()`, etc. Keep these helpers together.
* **DOM classes.** The `btn-top`/`btn-bottom` classes are toggled based on crop position inside `render()`; altering them affects button positioning.

## When editing

1. Read sections of `index.html` before changing them; it’s the single source of truth.
2. If you add new files (images, scripts), update `sw.js` and `manifest.json` accordingly.
3. Update `README.md` with any new developer commands, feature notes, or line references.
4. Record any long‑term decisions or custom “commandments” in `DEV_NOTES.md`.
5. Preserve the simple, self‑contained nature of the project; avoid introducing build dependencies unless absolutely necessary, and document the reason clearly.

## External dependencies & integration

* Only external library is `heic2any` served from jsdelivr.
* No backend or API integration exists; the app works entirely in‑browser.
* The PWA icon is currently an external URL in `manifest.json` – changing it to a local asset will require editing `manifest.json` and potentially updating CORS headers if served from a different origin.

---

Feel free to ask the user if anything is unclear or if additional context is needed.
