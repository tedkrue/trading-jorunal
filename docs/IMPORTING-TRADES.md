# Importing trades

## CSV format

The importer expects a header row and at least one closed-trade row with:

- A date or close time
- A symbol, contract, instrument, or product
- A realized P&L value

Header spelling can vary. The importer recognizes common date/time, symbol/contract, and P&L names. If the report includes both buy and sell fill IDs, these are used to recognize previously imported rows.

The importer reads comma-separated CSV text and handles quoted fields. It does not support arbitrary spreadsheet layouts, Excel workbooks, or exports that only contain unpaired orders/fills without realized P&L.

## Import steps

1. Export a report from Tradovate that contains closed-position results and realized P&L.
2. Open the journal and click **Import trades**.
3. Select the CSV file.
4. Review the detected trade count, win/loss/breakeven counts, sample rows, and duplicate count.
5. Confirm only if the values match the broker report.
6. Open a trade's edit control to add reasoning, setup details, rule adherence, or a screenshot.

Existing trade notes and screenshots are not overwritten by importing. Trades with matching broker fill identifiers are skipped. Rows without fill identifiers are compared by date, symbol, and P&L to avoid common duplicates.

## If a CSV does not import

- Make sure it is a CSV file, not an Excel workbook renamed to `.csv`.
- Choose a report with realized P&L for closed positions. A raw orders/fills export may not provide enough information to calculate trade results safely.
- Open the CSV in a text editor or spreadsheet and confirm it has a header row plus data rows.
- If the importer cannot find date, symbol, or P&L columns, the file may use a report format the importer does not recognize.
- Compare the pre-import counts and sample with the source report before confirming. The journal cannot independently verify that the broker export includes every account trade.

## Privacy and backups

The import runs in your browser. The CSV is read locally and is not uploaded to GitHub Pages. Imported trades and any screenshots are stored in that browser's IndexedDB. Export a JSON backup to move data to another browser or device.
