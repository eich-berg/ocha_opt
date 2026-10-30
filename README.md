# Health, Demolition, and Displacement in the West Bank

A single-page visualisation of UN OCHA oPt demolition and displacement data. The page reads `incidents.csv` directly in the browser, so there is nothing to build and no server.

## Files

| File | What it is |
|---|---|
| `index.html` | The visualisation. Never needs editing for a data update. |
| `incidents.csv` | The data. This is the only file you replace when updating. |
| `ocha_scraper.ipynb` | Google Colab notebook that downloads fresh data and writes `incidents.csv`. |

## Updating the data (every few days or weekly)

1. Open `ocha_scraper.ipynb` in Google Colab (colab.research.google.com > Upload).
2. Runtime > Run all. It takes a minute or two. `incidents.csv` downloads to your computer.
3. Read the last lines of the output. **OK** means the file looks complete. If it says **DO NOT UPLOAD**, do not use the file and try again later.
4. On GitHub, open your repository, click **Add file > Upload files**, drag in the new `incidents.csv` (same name, replaces the old one), and click **Commit changes**.
5. Wait a minute or two and reload the site. A hard refresh (Ctrl/Cmd + Shift + R) helps if you still see old numbers.

## Publishing on GitHub Pages (once)

Repository **Settings > Pages > Build and deployment**: Source "Deploy from a branch", Branch `main`, folder `/ (root)`. No GitHub Actions are needed.

## Notes

- The statistical model is fitted in your browser each time the page loads (a few seconds). Charts that depend on it show "Fitting the statistical model" until it finishes.
- If the CSV is missing columns the page needs, the page says which ones instead of drawing wrong charts.
- Opening `index.html` straight from a folder (double-click) cannot fetch the CSV, so the page offers a "Choose incidents.csv" button instead.
- If the scraper ever stops working, the dashboard's connection details may have changed. The five constants at the top of the scraper cell (`HOST`, `RESOURCE_KEY`, `DATASET_ID`, `REPORT_ID`, `MODEL_ID`) come from the public report's network requests.

Data: [UN OCHA oPt demolition data](https://www.ochaopt.org/data/demolition). Inspired by Danya M. Qato, [Public Health and the Promise of Palestine](https://www.palestine-studies.org/en/node/1650618).
