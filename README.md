# Caffeniate

Keep your device awake with a tiny, static web page. Caffeniate uses the
native Wake Lock API when available and falls back to a lightweight
`sleep.js` shim when it is not.

## What this is for
- Prevents screen sleep while a single browser tab stays open in the
  foreground.
- Useful for focus sessions, timers, presentations, or kiosk-style pages.

## Features
- Native Wake Lock API support with automatic release handling.
- Fallback `sleep.js` mode that keeps a hidden video playing.
- Clear status messages for activation, errors, and release reasons.
- Zero build steps; just static files.

## How it works
1. Click the button to request a wake lock.
2. If the browser supports the Wake Lock API, it uses that.
3. Otherwise it enables `sleep.js`, which plays a tiny hidden video to
   keep the device awake.

The wake lock is released if:
- The tab is no longer visible.
- You scroll away from the top of the page.
- You manually deactivate it.

## Quick start
Option 1: Open the file directly
- Double-click `index.html` in your browser.

Option 2: Serve locally (recommended for consistent behavior)
```bash
python3 -m http.server 8080
```
Then open `http://localhost:8080`.

## Project structure
- `index.html` - Page layout and Vue mount point.
- `styles.css` - Visual styling.
- `script.js` - Wake lock logic and UI behavior.
- `sleep.js` - Fallback wake prevention logic.

## Notes
- Wake Lock requires a user gesture and a visible, foreground tab.
- Some mobile browsers are stricter about auto-play; the button click is
  required to activate the fallback.
- This page is static and can be hosted anywhere (Cloudflare, Netlify,
  GitHub Pages, etc.).
