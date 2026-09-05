# Trade Process Journal — iPad/iPhone PWA

A local-first trading journal designed around the supplied lecturer framework:

1. Setup data
2. Drawdown data
3. Context data
4. Execution data

It also separates:
- Model quality
- Execution quality
- Psychology
- Outcome
- Weekly review

## What is included

- Pre-trade process gate
- CLS Model 1 starter checklist: range, liquidity, manipulation, displacement, confirmation
- Entry / stop / target / planned R:R
- Context fields: pair, session, day, HTF bias/location, premium/discount, market condition, news/volatility
- Before-trade psychology
- Before and after screenshots
- Post-trade execution audit
- Outcome in R
- Learning fields
- Setup / execution / psychology scores
- Dashboard
- Win rate, expectancy, R:R, drawdown and streak calculations
- Filters and trade log
- Saturday weekly review
- JSON backup/restore
- CSV export
- Offline cache / PWA shell

## Important design choice

The app does not invent a risk percentage or daily loss limit from the lecturer material. Those are configurable in Settings and start with conservative placeholders only where needed by the form.

## Data privacy

This build is local-first. Records are stored in the browser's localStorage. No server is required for the core journal.

Because browser storage is not a backup, use **Export JSON backup** regularly.

## Run locally

Any static web server can serve this folder. For example, from a computer:

    python -m http.server 8000

Then open the displayed address in Safari.

Opening `index.html` directly also works for the journal itself, but the offline PWA service worker requires HTTPS or localhost.

## iPad installation

After hosting the folder on GitHub Pages or another HTTPS static host:

1. Open the URL in Safari on iPad/iPhone.
2. Share.
3. Add to Home Screen.
4. Open it from the Home Screen.

## GitHub Pages

Create a new repository and upload the files in this folder to its root. Enable GitHub Pages from the repository's Pages settings and choose the main branch/root as the source.

Do NOT put sensitive journal records or exported backups into a public repository.

## Next engineering stage

The V1 is intentionally local-first and dependency-free. A later V2 can add a private cloud database/authentication layer while keeping the same UI and export format.
