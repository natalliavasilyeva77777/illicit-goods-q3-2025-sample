# SCHEMA — Darknet KYC Vendors & Fraud Tools (Q3 2025)

This file describes the columns of `final_dataset.csv` and the subset CSVs.  
All rows represent evidence-backed pages (with a screenshot) collected from public darknet (.onion) sources.

## Conventions
- Encoding: UTF-8.
- Delimiter: comma.
- Header row: present.
- Booleans: `"True"` / `"False"`.
- Timestamps: UTC, ISO-8601 (e.g., `2025-08-13T12:34:11Z`).
- Identifiers: `proof_id` = SHA-256 of the normalized URL.

## Columns

- **link_id**
  - Short internal ID from the seed file if available.
  - Type: string. May be empty.

- **url**
  - Normalized page URL (`http(s)://…`, `.onion` supported).
  - Type: string. Unique across the file.

- **title**
  - Page title at collection time.
  - Type: string.

- **text_snippet**
  - Cleaned text snippet from HTML; trimmed for length.
  - Type: string.

- **relevant**
  - Always `"Да"` for included records (Russian “Yes”). Kept for lineage.
  - Type: string.

- **category**
  - Normalized taxonomy (one of):
    - `kyc_bypass`, `fake_id`, `fullz`, `fraud_tools`, `hacking_services`,
      `account_sales`, `synthetic_identities`,
      `drugs`, `weapons`, `adult_content`, `other`.
  - Type: string.

- **product_type**
  - Human-readable subtype aligned to category:
    - `kyc bypass`, `fake id`, `fullz bundle`, `fraud tool`,
      `hacking services`, `account sales`,
      `synthetic identities`, `drugs`, `weapons`, `adult content`, `other`.
  - Type: string.

- **vendor_name**
  - Best-effort vendor or page label (heuristic).
  - Type: string. May be empty.

- **platform**
  - Detected platform:
    - `Onion Marketplace`, `Forum`, `Website`, `Telegram` (if evident).
  - Type: string.

- **price_range**
  - Min–max numeric range inferred from text (no currency), e.g., `300-30000`.
  - Type: string. May be empty.

- **contacts**
  - First contact extracted by priority:
    - Matrix > Email > XMPP/Jabber > Telegram > Onion.
  - Type: string (e.g., `@handle`, `name@domain.tld`).

- **contact_type**
  - One of: `matrix`, `email`, `xmpp`, `telegram`, `onion`, or empty.
  - Type: string.

- **suspicious**
  - Semicolon-separated flags. Examples:
    - `low_evidence_screenshot` (screenshot < 20 KB),
    - `maybe_legit` (white-list heuristics like EFF SSD),
    - `low_quality_text` (very short snippet).
  - Type: string. May be empty.

- **confidence_score**
  - Heuristic confidence in [0.50 … 0.99].
  - Factors: contacts present, pricing hints, taxonomy match, screenshot size.
  - Type: string (decimal with 2 digits).

- **verified**
  - `"True"` for core KYC/Fraud categories; else `"False"`.
  - Type: string.

- **verification_notes**
  - Free-text notes, e.g., `screenshot<20KB`.
  - Type: string. May be empty.

- **timestamp_utc**
  - Collection timestamp (UTC).
  - Type: string ISO-8601.

- **sensitive_content**
  - `"True"` for `drugs`, `weapons`, `adult_content`; else `"False"`.
  - Type: string.

- **proof_id**
  - Stable ID = SHA-256 of normalized URL.
  - Type: string. Unique across the file.

- **price**
  - First numeric price found.
  - Type: string/decimal. May be empty.

- **currency**
  - One of: `USD`, `EUR`, `GBP`, `BTC`, `XMR` (or empty if unknown).
  - Type: string.

- **screenshot**
  - Local relative path used during build (kept for lineage).
  - Type: string.

- **source_hash**
  - 16-char prefix of SHA-256(hostname), used for grouping sources.
  - Type: string.

- **screenshot_url**
  - Public CDN URL to the evidence image, e.g.:
    - `https://darknet-osint-cdn.b-cdn.net/screenshots/<filename>.png`
  - Type: string (HTTP URL).

## Quality & integrity
- `url` and `proof_id` are unique.
- 100% rows have screenshots; a small subset is flagged as low-evidence.
- Evidence hosted via CDN for click-through review.

## Subsets
- `subsets/core_kyc_fraud.csv` — KYC & Fraud focus.
- `subsets/illicit_goods.csv` — drugs + weapons.
- `subsets/adult.csv` — adult content.
- `subsets/all_in_one.csv` — full dataset.

## Versioning
- Release tag: **Q3 2025**; snapshot timestamp embedded in the repo snapshot.
- Changelog maintained in `CHANGELOG.md` (optional).
