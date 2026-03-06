# Fresh Cash Leads Dashboard

A static front-end web application for browsing and managing real estate property leads from Williamson County, Tennessee. Built for property managers and real estate investors who need quick access to fresh cash sale leads from public records.

## Live Demo

Start a local server and open `http://localhost:5020` in your browser (see [Getting Started](#getting-started)).

## Features

### Dashboard (`index.html`)
- **Dynamic Data Loading** — Fetches and parses lead data from CSV files at runtime
- **Sortable Columns** — Click any column header (Owner Name, Address, Price, Sold Date) to sort ascending/descending
- **Search** — Real-time text search across all fields (owner name, address, price, date)
- **Price Filtering** — Dropdown filter with preset ranges: $0–$100K, $100K–$500K, $500K–$1M, $1M+
- **CSV Export** — Export the current filtered/sorted view as a downloadable CSV file
- **Call Agent** — One-click "Call Agent" button for leads with phone numbers
- **Alternating Row Colors** — Zebra-striped rows for readability
- **SOLD Badges** — Visual indicators on properties with recorded sale dates

### Pricing Page (`pricing.html`)
- Single subscription plan: **$79/month** for Williamson County leads
- Feature breakdown (daily updates, CSV export, search, contact lookup, etc.)
- FAQ section covering data sources, update frequency, cancellation, trials, and payment methods
- Mock checkout modal with demo billing form (no real payment processing)

### Browse Counties (`counties.html`)
- County selection interface with card-based layout
- Currently active: **Williamson County, TN** (Franklin)
- Beta pricing display ($79/mo, crossed-out $99/mo with "Save 20%" badge)
- Trust bar with feature highlights
- Mock purchase flow that redirects to pricing page

## Data Files

All CSV files contain Williamson County, TN property sales data with the following columns:

| Column | Description |
|--------|-------------|
| Owner Name | Property buyer name (individual, LLC, or Trust) |
| Address | Full property address in Williamson County, TN |
| Price | Sale price (formatted as currency, e.g. `$36,000`) |
| Sold Date | Date of recorded sale |
| Agent Phone | Agent contact number (currently `N/A` for all records) |

### CSV Variants

- **`nashville_cash_leads_clean.csv`** — Primary dataset (500+ records). Uses abbreviated street types (DR, LN, CIR) and `M/D/YYYY` date format. Contains multi-line quoted owner names for joint ownership.
- **`nashville_cash_leads_clean_expanded.csv`** — Expanded cleaned dataset (44 records). Uses full street names (Drive, Lane, Circle) and `YYYY-MM-DD` date format.
- **`nashville_cash_leads_clean_sample.csv`** — Small sample dataset (14 records). Same clean format as the expanded file. Useful for testing.

## Tech Stack

- **HTML5** — Semantic markup
- **CSS3** — Custom styles with gradient themes, hover effects, responsive layout
- **JavaScript (Vanilla)** — CSV parsing, sorting, filtering, search, and export logic
- **Bootstrap 5.3** — Grid system, navbar, modals, buttons, form controls (loaded via CDN)
- **No build tools** — Pure static site, no bundler/transpiler/framework required

## Project Structure

```
Property-Managers--Front-End/
├── index.html                              # Main dashboard with leads table
├── pricing.html                            # Subscription pricing and FAQ
├── counties.html                           # County browsing and selection
├── nashville_cash_leads_clean.csv          # Primary lead dataset (500+ rows)
├── nashville_cash_leads_clean_expanded.csv # Expanded cleaned dataset (44 rows)
├── nashville_cash_leads_clean_sample.csv   # Sample dataset (14 rows)
├── .gitignore                              # Ignores .env, node_modules, dist, build
└── README.md                               # This file
```

## Getting Started

### Prerequisites

- A web browser (Chrome, Firefox, Edge, Safari)
- Any local HTTP server (the site uses `fetch()` so it must be served over HTTP, not opened as a file)

### Running Locally

**Option 1: Python (built-in)**
```bash
cd Property-Managers--Front-End
python -m http.server 5020
```

**Option 2: Node.js**
```bash
npx serve -l 5020
```

**Option 3: VS Code**
- Install the "Live Server" extension
- Right-click `index.html` > "Open with Live Server"

Then open [http://localhost:5020](http://localhost:5020) in your browser.

## Navigation

The site includes a consistent navbar across all pages:

| Link | Page | Description |
|------|------|-------------|
| Dashboard | `index.html` | Main leads table with search, sort, filter, and export |
| Pricing | `pricing.html` | Subscription details, features, FAQ, and mock checkout |
| Browse Counties | `counties.html` | County selection with availability status |

## CSV Parsing

The dashboard includes a custom CSV parser (`parseCSVRow`) that handles:
- Standard comma-separated values
- Quoted fields containing commas (e.g. `"1005 SCRAMBLERS KNOB, Unincorporated, TN"`)
- Escaped quotes within quoted fields (`""`)
- Multi-line owner names in the primary dataset

## Notes

- **Mock checkout only** — No real payment processing is implemented. Purchase buttons trigger demo alerts.
- **Agent phone data** — All records currently show `N/A` for agent phone numbers.
- **Data source** — Leads are sourced from Williamson County, TN public records (Register of Deeds).
- **No authentication** — The site is fully static with no login or access control.
- **No backend** — All data is loaded client-side from CSV files. There is no server-side API.

## License

This project is proprietary. All rights reserved.
