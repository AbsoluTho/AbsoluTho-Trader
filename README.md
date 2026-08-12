# Absolutho Performance

A personal trading performance dashboard for **Absolutho Trader®**, built as an installable Progressive Web App (PWA). It tracks day trading sessions (SOP era), behavioral scoring, time-of-day analysis, and comparisons against the pre-SOP baseline.

## What's inside

| File | Purpose |
|---|---|
| `index.html` | The full app — dashboard, charts, forms, and logic in a single file |
| `manifest.json` | PWA manifest (name, icons, theme color, standalone display mode) |
| `sw.js` | Service worker — caches assets so the app works offline |
| `icon-192.png` / `icon-512.png` | App icons used on the home screen and app switcher |
| `favicon.png` | Browser tab icon |
| `logo-header.png` | Brand logo shown in the app header |
| `splash-bg.jpg` | Background image shown on the splash screen at launch |

## Features

- **Dashboard** — equity curve, daily P&L, win/loss/breakeven split, behavioral scores per session with a streak view
- **Time-of-day analysis** — accuracy and financial result broken down by 30-minute windows
- **Diagnostics** — causal breakdown of losses opened after 11:00, with a behavioral cycle summary
- **Skill tracking** — five individual competency lines (plan execution, discipline, emotional control, risk management, trade selection) plus a consolidated view
- **Full session history** — sortable table of every recorded session
- **Pre-SOP comparison** — baseline stats from before the SOP protocol was adopted
- **Appendix** — operating philosophy, mantras, and grading criteria
- **Add session** — a form to log a new trading day, with automatic grade calculation from the five behavioral criteria

All data you add through the "Add session" form is stored locally on your device (`localStorage`) — nothing is sent to a server.

## Hosting it

This app is a static site — no backend required. To install it as a real app on Android or iOS, it needs to be served over **HTTPS** (a `file://` link won't trigger full PWA install behavior). Recommended free option: **GitHub Pages**.

1. Create a new public GitHub repository.
2. Upload all files in this folder to the repository root (keep them at the top level, not inside a subfolder).
3. Go to **Settings → Pages**, set the source to your main branch and the `/ (root)` folder, then save.
4. Wait a minute or two, then open the generated `https://<username>.github.io/<repo>` link on your phone.

## Installing on your phone

Open the hosted link in Chrome (Android) or Safari (iOS) and choose **"Add to Home Screen"** (or **"Install app"** if prompted). The app will launch full-screen with its own icon, and will keep working offline after the first load thanks to the service worker.

## Updating

- **New sessions**: use the in-app "Add session" form — saved instantly on that device.
- **Code or asset changes** (new charts, new branding, structural edits): re-upload the changed files to the GitHub repository. The service worker cache version in `sw.js` (`CACHE_NAME`) should be bumped on any asset change so devices pick up the new files instead of serving stale cached ones.

## Notes

- Data entered on one device does not sync to another — each install keeps its own local storage.
- The service worker enables offline use but also means updates won't appear until the cache version is bumped and the app is reopened.
