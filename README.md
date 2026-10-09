# Trading Journal

A simple, browser-based trading journal for importing Tradovate Performance CSV files, reviewing individual trades, adding notes and screenshots, and tracking account-level performance.

The application is split across `index.html`, `style.css`, and `app.js`.

## Run locally

Open `index.html` in a modern browser. Journal records and screenshots are saved in that browser's local IndexedDB storage. Use **Export backup** regularly to keep a separate copy.

## Publish with GitHub Pages

1. Create a GitHub repository named `trading-journal`.
2. Push the files in this folder to the repository's `main` branch.
3. In the repository, open **Settings → Pages** and set the source to **Deploy from a branch**, branch **main**, folder **/(root)**.
4. Save. GitHub Pages will publish `index.html` and `style.css` together.

Trade records and screenshots are stored in the visitor's browser and are not uploaded to GitHub Pages.
