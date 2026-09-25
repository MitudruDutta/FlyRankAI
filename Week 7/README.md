# Week 7: Content Action Playbook (ML-10)

## Overview
This directory contains the completed and executed deliverables for **Week 7: Build+ (ML-10)** in the FlyRank AI/ML Internship track.

- **Primary Notebook**: [`work/notebooks/w07_action_playbook.ipynb`](./work/notebooks/w07_action_playbook.ipynb)
- **Publication Figure**: [`work/figures/playbook_action_distribution.png`](./work/figures/playbook_action_distribution.png)
- **Playbook Metrics Receipts**: [`work/outputs/playbook_summary.json`](./work/outputs/playbook_summary.json)
- **Ranked Action Queue**: `work/outputs/ranked_action_playbook_queue.csv` (dynamically generated; excluded from git per CI leak-guard)

---

## 1. Archetype $\rightarrow$ Action Mapping Framework

| Reason Code | Diagnostic Archetype | Prescribed Action | Typical Effort | Strategic Leverage |
| :--- | :--- | :--- | :--- | :--- |
| **`page1_ctr_deficit`** | Prime rank (1.0–3.5), visible impressions, CTR below tier benchmark. | `optimize_serp_snippet_and_intent`: Rewrite `<title>`, craft compelling meta description, insert structured schema (FAQ/Product). | 1–2 hours | **Immediate Click Recovery**: High SERP exposure delivers instant traffic lift without backlink building. |
| **`striking_distance_decay`** | Striking rank (3.5–15.0), high predicted decay ($P \ge 0.60$). | `deep_content_expansion_and_internal_links`: Update outdated subtopics, add missing query sections, build internal links from authority pillars. | 3–5 hours | **Page 1 Transition**: Pushing striking queries into ranks 1–3 provides the highest non-linear traffic multiplier. |
| **`freshness_aging_risk`** | Aged content ($\ge 90$ days), moderate rank, decay probability $\ge 0.50$. | `update_factual_data_and_timestamps`: Refresh outdated statistics, replace dead external links, update publish dates. | 1–2 hours | **Preventive Defense**: Stabilizes rankings before search engines relegate stale content below page 1. |
| **`general_decay_risk`** | General decay probability $\ge 0.50$, rank $> 15.0$ or mixed metrics. | `review_intent_and_refresh_content`: Re-evaluate keyword relevance, consolidate cannibalizing articles, or conduct targeted refresh. | 2–3 hours | **Catalog Health**: Prevents long-tail decay and improves crawl budget allocation. |
| **`monitor_evergreen`** | Predicted decay $< 0.50$, stable CTR and rank. | `hold_and_monitor`: Do not alter. Preserve existing search equity. | 0 hours | **Resource Conservation**: Protects high-performing evergreen pages from unnecessary editorial disruption. |

---

## 2. Intended Use and Operational Boundaries
- **Intended Use**: Bi-weekly editorial refresh sprints across large catalog websites ($\ge 90$ days of search history).
- **Out of Scope**:
  - Newly published URLs ($< 30$ days old).
  - Diagnosing manual algorithmic penalties, server errors, or technical indexation blocks.
  - Queries where search engines deploy full-screen zero-click AI Overviews or knowledge graphs.
  - Immediate post-migration site re-architecture periods.

---

## 3. Human Review & The Strict No-Go List
- **Mandatory Checks**:
  1. Live SERP visual check in incognito mode (inspect SERP feature layout).
  2. Search intent shift verification (informational vs transactional).
  3. Brand safety and regulatory compliance.
- **Strict No-Go List (Never Automate)**:
  - ❌ **No automated LLM body rewrites pushed directly to CMS without human review**.
  - ❌ **No automated URL deletions or 301 redirects**.
  - ❌ **No automated edits to high-converting commercial landing pages**.

---

## 4. Cost / Value Economics & Performance
- **Evaluation on Unseen Clients (7 Holdout Clients, 6,163 Rows)**:
  - **Precision@20**: **95.0%** (19 of 20 truly declining URLs correctly identified)
  - **Precision@50**: **90.0%** (45 of 50 truly declining URLs correctly identified)
- **Top 50 Sprint Profile**:
  - 33 Quick-Win Metadata/Snippet Refreshes (1–2 hrs each)
  - 13 Striking Distance Expansions (3–5 hrs each)
  - Estimated Total Sprint Effort: ~101.5 writer hours
  - Estimated Return: Reclaiming 30–50 visits/month per URL on high-exposure keywords yields an estimated **9:1 ROI** compared to random editorial guessing (51.1% base rate).
