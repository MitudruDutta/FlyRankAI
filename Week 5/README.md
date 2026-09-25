# Week 5: Modeling Lane (ML-08) — Content Refresh Opportunity Scoring

## Overview
This directory contains the completed and executed deliverables for **Week 5: Build (ML-08)** in the FlyRank AI/ML Internship track.

- **Primary Notebook**: [`work/notebooks/w05_model.ipynb`](./work/notebooks/w05_model.ipynb)
- **Evaluation Receipts**: [`work/outputs/model_comparison.json`](./work/outputs/model_comparison.json)

---

## 1. Method Choice & Task Formulation
- **Lane**: Content Refresh / Organic Decay Opportunity Scoring.
- **Unit of Analysis**: One indexed URL over a trailing 90-day observation window (`content_id` $\times$ `client_id` $\times$ 90d window).
- **Core Decision**: Allocating finite human editorial capacity toward high-leverage URLs suffering organic performance decay.
- **Task Type**: **Probability-Based Ranking/Scoring**, evaluated by **Precision@20** and **Precision@50**, along with global ROC-AUC and Average Precision (PR-AUC).
- **Evaluated Models**:
  - Baseline Heuristic Rule (from Week 4)
  - Logistic Regression (linear baseline)
  - Interpretable Decision Tree (`max_depth=3`)
  - Random Forest Ensemble (`n_estimators=100, max_depth=6`)

---

## 2. Split Design: Client-Grouped Validation
- **Partition**: `GroupShuffleSplit` on `client_id` (test_size = 0.20, `random_state=42`).
- **Train Set**: 23,837 rows across 25 client domains (target base rate: 55.01%).
- **Test Set**: 6,163 rows across 7 unseen client domains (target base rate: 51.10%).
- **Zero Client Contamination**: 0 overlapping clients. Evaluating strictly on unseen domains prevents domain memorization and models the real-world deployment of FlyRank onto new client sites.

---

## 3. Model Comparison Table (Client Holdout Split: 7 Unseen Clients)

| Model / Strategy | Precision@20 | Precision@50 | ROC-AUC | PR-AUC | Lift vs Baseline (P@50) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Catalog Base Rate (Random)** | 0.511 | 0.511 | 0.500 | 0.511 | 1.00x |
| **Baseline Rule (Week 4)** | 0.250 (5/20) | 0.340 (17/50) | 0.500 | 0.506 | 1.00x (ref) |
| **Logistic Regression** | 0.250 (5/20) | 0.420 (21/50) | 0.560 | 0.546 | 1.24x |
| **Decision Tree (depth=3)** | 0.750 (15/20) | 0.600 (30/50) | 0.607 | 0.577 | 1.76x |
| **Random Forest (100 trees, depth=6)** | **0.950 (19/20)** | **0.900 (45/50)** | **0.626** | **0.630** | **2.65x** |

---

## 4. Key Interpretations & Error Analysis
1. **Rule Vulnerability on Unseen Clients**: The hand-crafted baseline achieved 34.0% Precision@50 on unseen clients (below catalog base rate of 51.1%) because it heavily relied on raw unscaled impression volume, which fails when transferring to new domain traffic distributions.
2. **Non-Linear Interactions**: The shallow Decision Tree and Random Forest dramatically outperformed linear baselines by learning non-linear split thresholds between CTR deficit and organic rank.
3. **Top Features**: Permutation and Gini importance show the model leans most heavily on `log_impressions_90d` and `avg_position`, followed by `days_since_last_update` and `ctr_deficit`.
4. **False Positive & Negative Dynamics**:
   - **False Positives**: Prime-ranking pages with low CTR due to rich snippet SERP feature competition that held traffic steady.
   - **False Negatives**: Low-exposure pages (1–3 lifetime impressions) that mathematically declined but represent negligible recoverable value to editors.
