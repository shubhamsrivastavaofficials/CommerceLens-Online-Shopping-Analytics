# CommerceLens

**Project 29 · Online Shopping Intelligence Dashboard**

CommerceLens is a browser-based final-year project prototype for descriptive online-shopping analytics. It presents sales, product, channel, RFM customer, and basket views in one responsive application. The project includes a reproducible illustrative dataset, analysis workbook, academic report, and presentation.

## Open the application

Open `index.html` in a recent browser. No installation, sign-in, database, or build step is required. The dashboard loads its bundled demonstration data. Use **Import CSV** to explore a compatible dataset; imported rows stay in browser memory for the current session.

## Project files

| File | Purpose |
|---|---|
| `index.html` | Complete interactive dashboard source and application |
| `CommerceLens_Final_Year_Report.docx` | Structured academic report with methodology, results, limitations, references, and appendices |
| `CommerceLens_Project_Presentation.pptx` | 12-slide project presentation with editable slide elements and presenter notes |
| `CommerceLens_Sample_Dataset.xlsx` | Summary, charts, RFM results, channels, transaction lines, and data dictionary |
| `sample_dataset.csv` | Import-ready, one-row-per-product-line sample records |
| `PROJECT_GUIDE.md` | Synopsis, system modules, methods, data dictionary, scope, and evaluation criteria |
| `GITHUB_VERCEL_DEPLOYMENT.md` | Prepared steps for putting the static site on GitHub and Vercel |
| `SUBMISSION_CHECKLIST.md` | Final personalisation and hand-in checklist |

## Demonstration data

The bundled dataset is generated and illustrative. It contains 2,400 orders, 4,661 item lines, and 632 pseudonymous customer IDs for the period 23 October 2025 to 22 October 2026. Do not present its metrics as observed sales or real customer behaviour. The workbook and report explain the same data boundary.

## CSV columns

Required headers: `date, order_id, customer_id, region, channel, category, product, quantity, unit_price`. Optional headers: `discount_pct, payment_method`. Each row represents a product line. Use one consistent currency; the interface formats monetary values as USD. Dates should be browser-readable, for example `2026-04-15`.

## Analysis and limitations

Line revenue is calculated as `quantity × unit_price × (1 − discount_pct / 100)`. The prototype calculates descriptive summaries, fixed-rule RFM groups, and category co-occurrence. RFM is not a trained prediction model; co-occurrence does not show causation. Taxes, shipping, refunds, and cost of goods are not included. The app has no login, backend, persistent storage, or multi-user features.

## Technology

The dashboard uses HTML, CSS, and vanilla JavaScript. It is a static site with no runtime server dependency or external charting library. Workbook formulas and charts are included in the separate Excel deliverable.
