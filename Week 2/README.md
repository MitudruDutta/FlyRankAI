# Week 2 — Frame Your Lane as an ML Task

This folder contains the Week 2 deliverables mapping our chosen lane (**Refresh / Content Opportunity Scoring**) onto the ML workflow:

## Contents

- [`work/notebooks/w02_ml_task_framing.ipynb`](./work/notebooks/w02_ml_task_framing.ipynb): The core executed deliverable covering:
  1. **ML Task Type Formulation:** Framing the problem as **Ranking / Priority Scoring** to optimize constrained editorial sprint capacity ($K=50$) rather than unranked binary classification.
  2. **Target & Proxy Definition:** The observed empirical ground truth target $\text{is\_declining\_label} = \mathbb{I}(\text{trend\_direction} == \text{'down'})$ with strict feature blacklisting to prevent target leakage (`trend_direction`, `trend_pct`).
  3. **Defensible Success Metric:** **Precision@50**, directly evaluating human editorial throughput and proving a target of $\ge 0.650$ (demonstrated $0.720$ on decision trees, a ~2x to 3x lift over naive baselines).
  4. **Unit of Analysis:** Verified grain of exactly 1 row per unique published content item (`content_id` $\times$ trailing-90-day observation window) with representative tabular slice.
  5. **Why ML Beats Fixed Rules:** Quantitative demonstration of non-linear interaction boundaries, resolution of the "tie-breaking pathology", and discovery of the non-monotonic freshness paradox.
