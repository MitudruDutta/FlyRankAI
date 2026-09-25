# FlyRank AI & ML Internship

Repository containing weekly assignments, exploratory data analysis, machine learning models, and capstone research for the FlyRank AI/ML Internship.

## Repository Structure

- [`Week 1/`](./Week%201/): Setup, initial data exploration, first interpretable models, and research question framing:
  - [`Week 1/notebooks/01_first_look_and_discovery.ipynb`](./Week%201/notebooks/01_first_look_and_discovery.ipynb): Pipeline run, baseline vs Random Forest, and live discoveries.
  - [`Week 1/notebooks/02_your_first_readable_model.ipynb`](./Week%201/notebooks/02_your_first_readable_model.ipynb): Hand-crafted heuristic vs decision tree, data leakage demo, and client-holdout validation.
  - [`Week 1/work/notebooks/w01_research_question.ipynb`](./Week%201/work/notebooks/w01_research_question.ipynb): Research question and provisional lane framing backed by real numbers.
  - [`Week 1/scripts/`](./Week%201/scripts/): Reference 5-step ML pipeline.
  - [`Week 1/outputs/`](./Week%201/outputs/): Generated model metrics, queue rankings, charts, and PDF report.
  - [`Week 1/work/`](./Week%201/work/): Workspace for research questions, contracts, audits, and capstone work.

- [`Week 2/`](./Week%202/): Machine Learning Task Formulation and Loop Mapping:
  - [`Week 2/work/notebooks/w02_ml_task_framing.ipynb`](./Week%202/work/notebooks/w02_ml_task_framing.ipynb): Comprehensive task mapping for the Refresh Opportunity Scoring lane (Task type: Ranking/Scoring, Target: Observed performance decay, Metric: Precision@50, Unit of analysis: Page $\times$ 90d window, and empirical proof of why ML beats static heuristics).

## Setup & Environment

Python 3.12 environment:
```bash
source ~/python/bin/activate
pip install -r "Week 1/requirements.txt"
```
