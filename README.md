# FlyRank AI & ML Internship

Repository containing weekly assignments, exploratory data analysis, machine learning models, and capstone research for the FlyRank AI/ML Internship.

## Repository Structure

- [`Week 1/`](./Week%201/): Setup, initial data exploration, and first interpretable models:
  - [`Week 1/notebooks/01_first_look_and_discovery.ipynb`](./Week%201/notebooks/01_first_look_and_discovery.ipynb): Full pipeline execution on anonymized search data, baseline vs random forest comparison (demonstrating ~3x Precision@50 improvement), and original data discoveries on active search volume, position CTR drop-offs by content type, and content age vs page trends.
  - [`Week 1/notebooks/02_your_first_readable_model.ipynb`](./Week%201/notebooks/02_your_first_readable_model.ipynb): Hand-crafted `stale x visible` heuristic vs human-interpretable Decision Tree, data leakage demonstration via `trend_pct`, depth-3 model exploration, engagement rate feature substitution, and honest 20% client-holdout validation.
  - [`Week 1/scripts/`](./Week%201/scripts/): Reference 5-step ML pipeline.
  - [`Week 1/outputs/`](./Week%201/outputs/): Generated model metrics, queue rankings, charts, and PDF report.
  - [`Week 1/work/`](./Week%201/work/): Workspace for research questions, contracts, audits, and capstone work.

## Setup & Environment

Python 3.12 environment:
```bash
source ~/python/bin/activate
pip install -r "Week 1/requirements.txt"
```
