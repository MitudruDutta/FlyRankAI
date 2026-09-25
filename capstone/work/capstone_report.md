# Capstone Executive Report: Decision-Support Refresh Opportunity Scoring

## 1. Abstract
Content teams face finite revision capacity and cannot rewrite every aging URL. We formulate search content refresh prioritization as a ranking problem on FlyRank search intelligence data. Using non-leaking pre-decision features and client-grouped cross-validation, a calibrated Random Forest model achieves **72.0% Precision@50 on unseen clients**, outperforming the hand-crafted editorial baseline of **38.0%** (an **89.5% relative lift**). Ranked recommendations are paired with transparent reason codes and specific remedial content actions to support editorial decision-making.

## 2. Core Problem & Unit of Analysis
- **Decision Supported**: Prioritizing editorial revision capacity across thousands of indexed URLs.
- **Unit of Analysis**: One row = One indexed page URL over a 90-day decision observation window.
- **Evaluation Metric**: Precision@50 (identifying true performance decay within the top 50 prioritized URLs on unseen client domains).

## 3. Methodology & Leakage Prevention
- **Feature Set**: Five strictly pre-decision signals:
  1. `days_since_refresh`: Temporal staleness at decision time.
  2. `prior_quarter_impressions`: Historical traffic scale (log-scaled).
  3. `avg_position`: Mean organic SERP ranking.
  4. `ctr_deficit`: Position-relative click-through rate shortfall.
  5. `striking_distance`: Indicator for positions 4.0 through 15.0.
- **Deliberate Leakage Safeguard**: Outcome-derived labels (`trend_pct`, `trend_direction`) produce trivial 1.000 accuracy and were completely excluded from training.
- **Client-Grouped Split**: 80% train clients, 20% holdout clients (strictly no domain contamination).

## 4. Empirical Evaluation
- Baseline Rule Top-50: 19 true decay cases out of 50 (Precision@50 = 38.0%).
- Random Forest Top-50: 36 true decay cases out of 50 (Precision@50 = 72.0%).
- Lift: **+34.0 percentage points (1.89x)**.

## 5. Deployed Artifacts
- **Interactive Web Research Paper**: [https://mitudrudutta.github.io/FlyRankAI/](https://mitudrudutta.github.io/FlyRankAI/)
- **Visual Evidence**: `docs/capstone_results_chart.png`
- **Jupyter Notebook**: `capstone/work/notebooks/capstone.ipynb`
