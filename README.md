# AdTech & Marketing Analytics Portfolio

A static portfolio site presenting five sample technical builds in digital advertising measurement: conversion tracking, GA4/GTM instrumentation, BI dashboarding, warehouse analytics (SQL), and marketing automation (Python). Built to demonstrate applied, end-to-end skill across the paid-media data stack, not just tool familiarity.

## **Live portfolio**

**[View the AdTech Portfolio](https://vimeshikashri.github.io/gTech-Ads/) | [View project results](https://vimeshikashri.github.io/gTech-Ads/results.html)**

## **Why this project exists?**

This repository and sites are built to show the *thinking*, not just the tool list:

- How a conversion event is defined, deduplicated, and validated, not just "Setting up a Google Ads tag."
- How an event taxonomy is designed to survive beyond one campaign.
- How a dashboard is built around a decision (weekly budget review), not around "whatever the connector gives you."
- How SQL is used to reconcile session and purchase data at the identifier level, not just to run a `SUM()`.
- How budget pacing is monitored programmatically instead of manually in a spreadsheet.

Each of the five samples maps to one stage of the paid-media data lifecycle: **capture → structure → report → analyze → act.**

---

## **Live Structure**

```
.
├── index.html                              # Landing page — hero, capability grid, 5 project cards
├── results.html                            # Standalone "outcomes" page (linked from index footer)
├── styles.css                              # Single shared stylesheet for both HTML pages
├── 01_google_ads_conversion_tracking.md    # Sample 1 — conversion measurement design doc
├── 02_ga4_gtm_ecommerce.md                 # Sample 2 — GA4/GTM ecommerce event taxonomy
├── 03_looker_marketing_dashboard.md         # Sample 3 — Looker Studio dashboard spec
├── 04_bigquery_marketing_analytics.sql     # Sample 4 — BigQuery/GA4-export SQL model
├── 05_google_ads_budget_pacer.py           # Sample 5 — Google Ads API budget-pacing script
└── README.md
```

No build step. No dependencies to install for the site itself, it is plain HTML/CSS. The `.sql` and `.py` files are reference artifacts, not executable in this repo as-is (see §5).

---

## **Tech Stack**

| Layer | Choice | Notes |
|---|---|---|
| Markup | Semantic HTML5 | No framework — kept deliberately simple/static |
| Styling | Hand-written CSS, custom properties | No Tailwind/Bootstrap; `:root` design tokens in `styles.css` |
| Fonts | Manrope (sans), DM Mono (mono), Georgia (serif accent) | Loaded via Google Fonts CDN |
| Analytics reference stack (documented, not live) | GA4, GTM, Consent Mode v2, Google Ads conversions | Described in samples 1–2 |
| BI reference stack | Looker Studio | Described in sample 3 |
| Data warehouse | BigQuery (GA4 export schema) | Sample 4 |
| Automation | Python 3 + `google-ads` client library | Sample 5 |

---

## **Page-by-page Breakdown**

### `index.html`
- Hero section with a 3-item capability grid (Instrumentation / Analytics / Activation).
- Five `.project` cards, one per sample, each with:
  - A CSS-only illustrative visual (funnel bars, event chips, chart bars, SQL block, pacing bar) — all built with `<div>`s and CSS, not images or charting libraries.
  - A single headline metric (`project-result`) framed as the outcome that kind of build is designed to produce.
- "How I work" section (`#approach`), a 3-step process framing (frame the decision → design the signal → make it usable).

### `results.html`
- Restates the same five outcomes in a denser, tabular-style layout.
- Includes an explicit disclosure banner (`.results-note`) stating the numbers are **illustrative portfolio samples**, not verified client results. This is the correct approach and should not be removed or softened when the site goes live (see §6).

### `styles.css`
- Design tokens defined once in `:root`:
  ```css
  --ink: #10221f;      /* primary text/background (dark mode blocks) */
  --paper: #f5f4ee;    /* page background */
  --acid: #c8f345;     /* accent — green */
  --orange: #ff684a;   /* accent — orange, used for numbers/highlights */
  --muted: #65716c;    /* secondary text */
  --mono: "DM Mono", monospace;
  --sans: "Manrope", sans-serif;
  ```
- Single responsive breakpoint at `800px` — grid layouts collapse from multi-column to single-column, project visuals move below copy instead of beside it.

---

## **The five samples (What each one demostrates?)**

| # | File | Demonstrates | Key technical decision |
|---|---|---|---|
| 1 | `01_google_ads_conversion_tracking.md` | Consent-aware, deduplicated purchase tracking | `transaction_id` used as the dedup key across browser + server events |
| 2 | `02_ga4_gtm_ecommerce.md` | Durable GA4 event taxonomy | Application pushes a clean `dataLayer` object — no DOM-scraping for price/SKU |
| 3 | `03_looker_marketing_dashboard.md` | Decision-first BI dashboard | Every page maps to one media-review question, not "everything available" |
| 4 | `04_bigquery_marketing_analytics.sql` | Session-to-purchase reconciliation in BigQuery | Joins on `user_pseudo_id` + `ga_session_id`, not last-click guesswork |
| 5 | `05_google_ads_budget_pacer.py` | Automated spend-pacing alerts | Calendar-day expected-spend model with a configurable variance threshold (default 8%) |

These are written as **design/spec documents and reference code**, not screenshots of a real client account, intentionally, since client data can not be published. This is disclosed on `results.html` and should also be stated on `index.html` (currently it isn't — see §6).

`04_bigquery_marketing_analytics.sql` and `05_google_ads_budget_pacer.py` require real credentials and a live BigQuery/Google Ads account to run, they are shipped as read/reference artifacts in this repo, not as runnable demos.

---

## **Running locally**

Static site, no build tooling required:

```bash
# from the project root
python3 -m http.server 8000
# then open http://localhost:8000/index.html
```

Or open `index.html` directly in a browser (all asset paths are relative).

---

## **Contact**

_**Vimeshika Shri**_
- GitHub: [@VimeshikaShri](https://github.com/VimeshikaShri)
- <small>Email: vimeshika.balamurali@gmail.com</small>
