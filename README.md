# World Cup 2026 Simulator · Macro Markets

Interactive, static, zero-build simulator for the **FIFA World Cup 2026**.

Use it to fill group-stage scores, watch standings update live, project the best third-place teams, simulate the knockout bracket, reveal a champion path, and share the full scenario by URL or PNG.

**Live site:** https://macro-markets.github.io/world-cup-2026-simulator/

## Highlights

- **Full 2026 tournament flow** — group stage, best third-place ranking, Round of 32, Round of 16, quarterfinals, semifinals, and final.
- **Live standings engine** — tables update as scores change, including FIFA-style tie-break rules implemented in pure JavaScript.
- **Official third-place mapping** — the bracket adjusts according to the qualified third-place groups.
- **Shareable scenarios** — predictions are serialized into the URL hash (`#s=...`) and restored on open.
- **PNG share card** — generate a 1200×630 tournament card with the projected champion and mini bracket.
- **Responsive bracket UI** — connected desktop bracket and mobile-friendly phase tabs.
- **Light/dark theme** — follows system preference and persists user choice in `localStorage`.
- **Multilingual UI** — Portuguese, English, and Spanish strings are bundled client-side.
- **No backend / no build** — deploys as plain static files.

## Quick start

Clone and serve the repository root with any static server:

```bash
git clone https://github.com/Macro-Markets/world-cup-2026-simulator.git
cd world-cup-2026-simulator
python3 -m http.server 8080
```

Open:

```text
http://localhost:8080/
```

Because the app uses ES modules, open it through a local HTTP server instead of `file://`.

## How to use

1. Fill group-stage scores manually, or use the winner radio button for a quick 1×0.
2. Review each group table and the ranking of best third-place teams.
3. Simulate knockout matches. If a match is tied, choose the winner explicitly.
4. Once the final is decided, the champion panel shows the projected winner and title path.
5. Use **Copy link** or **Share** to preserve and send the scenario.

## Project structure

```text
index.html                 # Static app shell
styles/
  tokens.css               # Theme tokens for dark/light mode
  base.css                 # Base layout and typography
  components.css           # Reusable UI components
  sections.css             # Page sections and responsive layouts
scripts/
  data/                    # Teams, fixtures, bracket template, third-place map
  engine/                  # Pure tournament logic: standings, tie-breaks, qualifiers, bracket
  i18n/                    # PT/EN/ES translations and venue labels
  state/                   # Store, URL serialization, localStorage persistence
  ui/                      # Rendering modules for hero, groups, bracket, champion, sharing
  utils/                   # DOM, keyboard, and theme helpers
assets/                    # Favicon and static visual assets
group-schedule.json        # Source fixture schedule
third-place-map.json       # Source third-place mapping
```

## Technical notes

- The app is intentionally framework-free: HTML, CSS, and modern JavaScript modules.
- Tournament calculations live under `scripts/engine/` and avoid DOM coupling.
- State is persisted both in `localStorage` and in the URL hash for sharing.
- UI rendering is split by section so the simulator can re-render after score/theme/language changes.
- Static hosting works from repository root; no package manager is required to run the site.

## GitHub Pages deployment

This repository is published from the `master` branch root through GitHub Pages:

```text
Source: Deploy from branch
Branch: master
Folder: /
```

Expected production URL:

```text
https://macro-markets.github.io/world-cup-2026-simulator/
```

If you change static assets or scripts, commit to `master` and GitHub Pages will rebuild automatically.

## Repository

Macro Markets destination:

```text
https://github.com/Macro-Markets/world-cup-2026-simulator
```

## License

No license file is currently included. Add one before reusing or distributing outside Macro Markets-controlled properties.
