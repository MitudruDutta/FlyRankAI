# Week 6: Validation and Research Claim Audit (ML-09)

## Overview
This directory contains the completed and executed deliverables for **Week 6: Build+ (ML-09)** in the FlyRank AI/ML Internship track.

- **Primary Notebook**: [`work/notebooks/w06_validation_audit.ipynb`](./work/notebooks/w06_validation_audit.ipynb)
- **Audit Metrics Receipts**: [`work/outputs/audit_metrics.json`](./work/outputs/audit_metrics.json)

---

## 1. Methodology Critique of Published Research Paper Findings

### Finding 1: "The Content Performance Curve" (Finding #2, Page 7)
- **Published Claim**: Content peaks at 61–90 days, declines after 270 days, with a secondary stability window at 121–180 days.
- **Methodology Questions**:
  1. *Survivorship Bias in Outcome Window*: Evaluated as a cross-sectional snapshot across age cohorts. Pages surviving beyond 270 days represent an unpruned survivor cohort. A true lifecycle test requires longitudinal panel tracking within individual URLs.
  2. *Domain Authority Confounding*: Older articles may be concentrated in enterprise domains with higher baseline authority, confounding chronological aging with domain equity.

### Finding 2: "The Freshness Multiplier & Freshness Paradox" (Finding #4 & Myth #7, Pages 9 & 24)
- **Published Claim**: The 31–90 day window is the strongest stable freshness band, and freshness amplifies quality rather than replacing it.
- **Methodology Questions**:
  1. *CMS Timestamp vs Editorial Revision*: `days_since_last_update` often reflects automated CMS touch events rather than substantive content revisions.
  2. *The Freshness Paradox*: Empirical audit reveals content aged 181+ days has a lower decay rate (47.1%) than 91–180 days (61.1%) due to stable evergreen URLs remaining untouched.

---

## 2. Before / After Split Design Audit (Memorization Gap)

| Split Design | Test Population | Base Rate | Precision@20 | Precision@50 | ROC-AUC | PR-AUC |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **BEFORE: Naive Random Split** | All 32 Clients (Shared) | 0.540 | 0.900 | 0.900 | **0.708** | **0.718** |
| **AFTER: Honest Client-Grouped Split** | 7 Unseen Client Domains | 0.511 | 0.950 | 0.900 | **0.626** | **0.630** |
| **MEMORIZATION GAP (Before - After)** | N/A | -0.029 | -0.050 | 0.000 | **+0.082** (Inflation) | **+0.088** (Inflation) |

*Finding*: Random train/test splitting inflates ROC-AUC by **+0.082** by allowing the model to memorize client-level domain authority and catalog impression baselines. Client-grouped evaluation reflects honest out-of-domain decision-support generalization.

---

## 3. Leakage Confession Test & Blacklist Audit

| Pipeline Configuration | Precision@50 | ROC-AUC | PR-AUC | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Deliberately Leaky (+ trend_pct)** | **1.000** | **1.000** | **1.000** | CONFESSED LEAK (Trivial Cheat) |
| **Honest Pre-Decision Features** | **0.900** | **0.626** | **0.630** | CLEAN PRE-DECISION TELEMETRY |

- **Blacklist Verification**: Verified zero presence of forbidden outcome columns (`trend_pct`, `trend_direction`, `is_declining_label`, `impressions_last_30d`) in the production feature frame.

---

## 4. Claim Rewrite & Public-Safe Language Standards

- **Overstated / Banned Draft**: *"Our Random Forest model accurately predicts Google's ranking drops and proves that content freshness and CTR deficits directly cause traffic loss."*
- **Rewritten Claim (Safe, Defensible, Decision-Support)**:
  > *"Across an out-of-domain evaluation on 7 unseen client websites (6,163 candidate URLs), a calibrated Random Forest model achieved an observed **90.0% Precision@50** (45/50 truly declining URLs) in identifying content experiencing organic performance decay, representing a **2.65x lift** over a heuristic baseline rule (34.0% P@50). While these pre-decision signals provide actionable decision support for prioritizing editorial revision sprints, observed historical associations do not establish causal recovery without controlled interventional testing."*
