# Week 3 — Search Intelligence Data Contract (ML-04)

This folder contains the Week 3 deliverables establishing the formal **Data Contract** for our lane (**Refresh / Content Opportunity Scoring**):

## Contents

- [`work/notebooks/w03_data_contract.ipynb`](./work/notebooks/w03_data_contract.ipynb): The core executed deliverable covering:
  1. **The Contract in Plain Words:** 5 explicit operational answers (unit of analysis, tables, observation windows, prediction target, and deliberate exclusions).
  2. **Field Categorization:** Strict partitioning of every touched column into Feature, Label, Context, or Excluded, backed by an automated assertion audit.
  3. **Verification Queries (DuckDB SQL):**
     - *Query 1 (Grain):* Proof of 0 duplicate keys on `content_id`.
     - *Query 2 (Counts & Span):* Exact row count (30,000) and age distribution (90 to 564 days) across 32 clients.
     - *Query 3 (Availability via `IS TRUE`):* Empirical proof that 100% of rows have active GSC search impressions, while only 27.9% have active GA4 engaged sessions.
  4. **Five Core Features:** Selected 5-feature baseline frame with explicit "knowable when?" justification for each signal.
  5. **The Leakage Trap:** Deliberate injection of `trend_pct` demonstrating an artificial jump to 1.000 Precision@50, followed by purging the leaky column to retain the honest 0.720 score.
  6. **Data Limitations:** Naming the structural challenge of unbalanced client tracking depth (`gsc_data_start`) and GA4 coverage gaps.
