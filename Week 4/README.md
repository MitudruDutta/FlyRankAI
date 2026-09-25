# Week 4 — Baseline Action Score and Top-20 Review (ML-07)

This folder contains the Week 4 deliverables establishing the **transparent rule-based baseline** for our lane (**Refresh / Content Opportunity Scoring**):

## Contents

- [`work/notebooks/w04_baseline_score.ipynb`](./work/notebooks/w04_baseline_score.ipynb): The core executed deliverable covering:
  1. **Two Signal Audits:**
     - *Signal 1 (Freshness Tier / Staleness):* Tested decline rates across 4 tiers ($n=20,480; 175; 9,171; 174$). Verdict: **MIXED / OPPOSITE** (proves peak decay is at 91–180 days with 61.1%, while 181+ days drops to 47.1%).
     - *Signal 2 (CTR Deficit vs. Position Tier Benchmark):* Tested CTR vs tier median on visible content ($n=22,006$). Verdict: **CONFIRMED** (proves pages with below-median CTR suffer a +11.6pp higher decay rate: 65.95% vs 54.32%).
  2. **Rule Formulation & Ranked Queue:**
     - Transparent multiplicative score with single reason codes (`page1_striking_ctr_deficit`, `high_exposure_aging_page`, `low_priority_or_not_eligible`) and operational action labels (`refresh_metadata_and_intent`, `update_content_and_facts`, `monitor`).
     - Generates the ranked queue to `work/outputs/baseline_action_score.csv` with Precision@20 = 0.600 and Precision@50 = 0.400.
  3. **Top-10 Skeptical Review:**
     - Line-by-line breakdown of the top 10 queued URLs with explicit *"what would make it wrong"* considerations for each.
  4. **Weak Picks & Leakage Audit:**
     - Exposed single-client monopolization (8 of top 10 from one enterprise domain) and false positives on zero-click informational SERPs.
     - Confirmed zero target leakage columns.
- [`work/outputs/baseline_metrics.json`](./work/outputs/baseline_metrics.json): Committed receipts containing baseline Precision@20 (0.600), Precision@50 (0.400), catalog base rate (0.542), and signal verdicts.
