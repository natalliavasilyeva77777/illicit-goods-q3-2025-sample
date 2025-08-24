# Changelog — Darknet KYC Vendors & Fraud Tools

## Q3 2025 (2025-08-13)
**Initial public release**

- **Dataset size:** 10,187 rows (unique `url` and `proof_id`).
- **Evidence:** 100% rows have screenshots; 84 flagged as `low_evidence_screenshot` (<20 KB).
- **Core subsets:**
  - Core KYC & Fraud — 6,606
  - Illicit Goods (Drugs + Weapons) — 3,348
  - Adult — 205
  - All-in-One — 10,187
- **Taxonomy:** `kyc_bypass, fake_id, fullz, fraud_tools, hacking_services, account_sales, synthetic_identities, drugs, weapons, adult_content, other`.
- **Columns:** `README.md` and `SCHEMA.md` added (English).
- **Screenshots CDN:** `https://darknet-osint-cdn.b-cdn.net/…` via `screenshot_url` column.
- **Known limitations:** Some `.onion` sources are unstable; 291 seeds remained unreachable at build time.
- **Quality tags:** `low_evidence_screenshot`, `low_quality_text`, `maybe_legit` where applicable.

### Notes for buyers
- Evidence links (`screenshot_url`) are live over HTTPS (no TOR needed).
- Reproducible build: source fields retained to allow audits and future updates.

