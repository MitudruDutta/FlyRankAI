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

- [`Week 3/`](./Week%203/): Search Intelligence Data Contract (ML-04):
  - [`Week 3/work/notebooks/w03_data_contract.ipynb`](./Week%203/work/notebooks/w03_data_contract.ipynb): 5 plain-words contract answers, 3 DuckDB verification queries (Grain, Counts/Span, Availability via `IS TRUE`), 5 core features with decision-moment availability rationales, deliberate leakage trap experiment (jumping to 1.000 and restored to 0.720), and named data limitations.

- [`Week 4/`](./Week%204/): Baseline Action Score and Top-20 Review (ML-07):
  - [`Week 4/work/notebooks/w04_baseline_score.ipynb`](./Week%204/work/notebooks/w04_baseline_score.ipynb): Two signal audits (Freshness Tier: MIXED/OPPOSITE, CTR Deficit: CONFIRMED), transparent rule score with reason codes, ranked queue export, skeptical top-10 review with failure modes, and committed metrics receipts in `work/outputs/baseline_metrics.json`.

- [`Week 5/`](./Week%205/): Modeling Lane (ML-08):
  - [`Week 5/work/notebooks/w05_model.ipynb`](./Week%205/work/notebooks/w05_model.ipynb): Full modeling comparison on identical client holdout split (7 unseen clients). Baseline Rule vs Logistic Regression vs Decision Tree (depth=3) vs Random Forest (depth=6). Random Forest achieves **90.0% Precision@50 (2.65x lift)** and **95.0% Precision@20**. Includes permutation importance and qualitative error audits of concrete failure cases.
  - [`Week 5/work/outputs/model_comparison.json`](./Week%205/work/outputs/model_comparison.json): Recorded model comparison metrics.

- [`Week 6/`](./Week%206/): Validation and Research Claim Audit (ML-09):
  - [`Week 6/work/notebooks/w06_validation_audit.ipynb`](./Week%206/work/notebooks/w06_validation_audit.ipynb): Methodological audit of FlyRank's published research paper findings, before/after split comparison demonstrating the domain memorization gap (+0.082 ROC inflation under random split), deliberate leakage confession test (jumping to 1.000), strict feature blacklist assertion, and claim rewrites into defensible decision-support language.
  - [`Week 6/work/outputs/audit_metrics.json`](./Week%206/work/outputs/audit_metrics.json): Recorded validation audit metrics.

- [`capstone/`](./capstone/): Final Capstone Project — Decision-Support Refresh Opportunity Scoring:
  - **Deployed Research Paper**: [https://mitudrudutta.github.io/FlyRankAI/](https://mitudrudutta.github.io/FlyRankAI/)
  - [`capstone/work/notebooks/capstone.ipynb`](./capstone/work/notebooks/capstone.ipynb): Executed end-to-end capstone notebook (client-holdout validation, Random Forest vs Baseline 72% vs 38% P@50, Action Playbook, reason codes).
  - [`capstone/submission/paper_url.txt`](./capstone/submission/paper_url.txt): Verified deployed paper URL.
  - [`capstone/work/capstone_report.md`](./capstone/work/capstone_report.md): Executive research report.
  - [`docs/index.html`](./docs/index.html): Deployed GitHub Pages paper source code.
  - [`docs/capstone_results_chart.png`](./docs/capstone_results_chart.png): Research paper evaluation charts.

## Setup & Environment

Python 3.12 environment:
```bash
source ~/python/bin/activate
pip install -r "Week 1/requirements.txt"
```
