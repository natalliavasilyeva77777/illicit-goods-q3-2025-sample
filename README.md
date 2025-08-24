# Darknet KYC Vendors & Fraud Tools — Q3 2025

**Version:** Q3 2025 (collection completed 2025-08-13)  
**Size:** 10,187 records with screenshot evidence  
**Subsets included:**  
- Core KYC & Fraud — 6,606  
- Illicit Goods (Drugs + Weapons) — 3,348  
- Adult — 205  
- All-in-One — 10,187

## What this is
A commercial OSINT dataset covering darknet (.onion) vendors and tools: KYC bypass, fake IDs, fullz, fraud tools, hacking services, account sales, plus sensitive segments (drugs, weapons, adult).  
Each record has a stable `proof_id` and a **screenshot as evidence**.

## Package contents
- `final_dataset.csv` — the main file (includes `screenshot_url` for every row).  
- `subsets/` — ready-to-sell slices:
  - `core_kyc_fraud.csv`
  - `illicit_goods.csv`
  - `adult.csv`
  - `all_in_one.csv`
- Evidence screenshots are served via CDN through `screenshot_url`. (Enterprise option: offline bundle with all images.)

## CSV schema (columns)
`link_id, url, title, text_snippet, relevant, category, product_type, vendor_name, platform, price_range, contacts, contact_type, suspicious, confidence_score, verified, verification_notes, timestamp_utc, sensitive_content, proof_id, price, currency, screenshot, source_hash, screenshot_url`

### Key fields (short)
- **category / product_type** — normalized taxonomy: `kyc_bypass, fake_id, fullz, fraud_tools, hacking_services, account_sales, synthetic_identities, drugs, weapons, adult_content, other`.  
- **proof_id** — SHA-256 of the normalized URL (stable identifier).  
- **screenshot_url** — direct CDN link to the page screenshot.  
- **confidence_score** — heuristic quality score (0.50–0.99).  
- **suspicious** — quality flags (e.g., `low_evidence_screenshot`).

## Evidence & quality notes
- 100% of rows have screenshots; **84** are small (<20 KB) and explicitly flagged (`low_evidence_screenshot`) for transparency.  
- No duplicates: both `url` and `proof_id` are unique across the dataset.  
- Reproducible: hashes and scripts allow rebuilding selections.

## How to use
- Open `final_dataset.csv` in Excel/Sheets/BI.  
- Filter by `category` / `product_type`.  
- Click `screenshot_url` to open the evidence image.  
- Programmatic use: load the CSV and fetch `screenshot_url` via HTTP.

## Licensing & disclaimer
All data was collected from publicly accessible sources (.onion) for research/OSINT purposes. The author does not endorse illegal activity. Buyers must use the dataset in compliance with applicable laws and platform policies.

## Contact
For licensing, custom exports, updates (Q4 2025), or the upcoming SaaS panel, please get in touch.
