# Trading Journal

A lightweight, static trading journal for importing closed trades from a Tradovate CSV report, reviewing each trade, attaching a chart screenshot, and tracking performance and account risk.

The app is designed to run as a static website. It does not need a server, database account, build step, or paid service.

## Features

- Import closed-trade rows from a CSV file and skip trades that appear to have already been imported.
- Add, edit, search, and filter trades by outcome.
- Record the strategy or setup, whether trading rules were followed, written reasoning, and an optional screenshot.
- Review win rate, profit factor, net P&L, progress toward a target, an equity curve, daily P&L, and a trade calendar.
- Configure starting balance, target, daily loss limit, maximum drawdown limit, fees or adjustments, and currency.
- Export a full JSON backup and restore it later.

## Quick start

1. Download or clone this repository.
2. Open `index.html` in a modern browser. For the most consistent behavior, serve the folder using a local static server or publish it with GitHub Pages.
3. Set your account values in **Account settings**.
4. Import a CSV or add trades manually.
5. Use **Export backup** regularly, especially before clearing browser data or changing devices.

The app is plain HTML, CSS, and JavaScript; there is no dependency installation or build command.

## Importing a Tradovate CSV

Choose **Import trades** and select a CSV containing closed-position results. The importer looks for a date/time, symbol or contract, and realized P&L column. It supports common header variations, including Tradovate-style fill identifiers where present. It does not combine raw orders or fills into positions, because doing so could produce incorrect trade results.

Before confirming, the app shows how many wins, losses, and breakeven trades it found, along with a small sample. Check those figures against the broker report. If no valid rows are found, use a closed position/performance report that includes realized P&L; an orders or fills export by itself may not be enough.

See [the CSV import guide](docs/IMPORTING-TRADES.md) for details and troubleshooting.

## Data storage and backups

Trade records, notes, account settings, and screenshots are stored in IndexedDB in the browser profile that opened the site. They are not sent to this repository or to GitHub Pages. The app has no user account or cloud sync, so data does not automatically follow you to another browser, device, or website origin.

Use **Export backup** to download a JSON file. To restore it, open the journal in the browser where you want the data and choose **Restore backup**. Restoring replaces the journal data currently stored in that browser. Keep backup files somewhere private; they can contain your trade history and screenshots.

## Publish with GitHub Pages

1. Push the repository to GitHub.
2. In the repository, open **Settings → Pages**.
3. Choose **Deploy from a branch**, select `main` and the `/(root)` folder, then save.
4. Wait for GitHub Pages to publish the site. Its URL will be shown in the Pages settings.

`index.html` stays in the repository root because GitHub Pages uses it as the site entry point. CSS and JavaScript are in `assets/`; the page links to them with relative paths so they work on a project site as well as locally.

## Project layout

```text
.
├── index.html                 # GitHub Pages entry point and app interface
├── trading-journal.html       # Compatibility redirect to index.html
├── assets/
│   ├── css/style.css          # Layout, colors, and responsive styling
│   └── js/app.js              # Journal behavior, storage, charts, and import
├── docs/
│   └── IMPORTING-TRADES.md    # CSV import notes and troubleshooting
└── README.md
```

## Current limitations

- Import is file-based; the journal does not sign in to Tradovate or connect to a broker API.
- Results are based on imported or manually entered closed-trade P&L. Open positions and firm-specific trailing drawdown rules are not calculated.
- All journal data stays in one browser profile unless you export and restore a backup yourself.
