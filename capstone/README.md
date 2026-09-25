# FlyRank AI Capstone: Decision-Support Refresh Opportunity Scoring

## Overview
This directory contains the final Capstone project for the FlyRank AI/ML Internship. It formulates, trains, validates, and deploys a decision-support machine learning ranking system for identifying high-leverage search content refresh opportunities.

- **Deployed Research Paper**: [https://mitudrudutta.github.io/FlyRankAI/](https://mitudrudutta.github.io/FlyRankAI/)
- **Submission URL Receipt**: [`submission/paper_url.txt`](./submission/paper_url.txt)
- **Primary Executed Notebook**: [`work/notebooks/capstone.ipynb`](./work/notebooks/capstone.ipynb)
- **Results Chart**: [`docs/capstone_results_chart.png`](./docs/capstone_results_chart.png)
- **Web Paper Source**: [`docs/index.html`](./docs/index.html)

---

## Key Results Summary

| Model / Approach | Evaluation Split | Precision@50 | Lift over Baseline |
| :--- | :--- | :--- | :--- |
| **Heuristic Baseline Rule** | Unseen Client Holdout (20%) | **38.0%** (19/50) | 1.00x |
| **Calibrated Random Forest Ensemble** | Unseen Client Holdout (20%) | **72.0%** (36/50) | **1.89x** (+34.0 pp) |

### Key Findings
1. **Freshness Paradox Resolved**: Static editorial rules relying solely on chronological publication age fail because old evergreen content (181+ days) actually decays slower (47.1%) than mid-lifecycle content (91–180 days, 61.1% decay).
2. **CTR Deficit as High-Leverage Indicator**: Striking-distance query performance and position-relative CTR deficits were the strongest predictors of reclaimable traffic.
3. **Leakage & Generalization Safeguards**: Outcome-derived columns (`trend_pct`, `trend_direction`) were strictly excluded. Evaluation was strictly performed across client holdout boundaries to prevent memorization of domain-specific traffic volume.
