# QMTRY-Pophealth-Readmissions
Reproducible, audit-ready demo to predict 30-day readmissions &amp; avoidable admissions with ML, LACE baselines, SHAP, and a Streamlit care-manager dashboard (synthetic data, deployable to client).

# QMTRY Predictive Modeling for Population Health


This repo demonstrates a reproducible pipeline to identify high‑risk members for 30‑day readmission and potentially avoidable admissions (ACSC) using synthetic data. It is designed to be deployed quickly on client data to reduce avoidable utilization and improve Stars.


## Why it matters
- Lower avoidable utilization and total cost of careQmtry Portfolio — Predictive Modeling For Population Health (case Study + Readme + Workflow)
QMTRY-Pophealth-Readmissions

Reproducible, audit-ready demo to predict 30-day readmissions & avoidable admissions with ML, LACE baselines, SHAP, and a Streamlit care-manager dashboard (synthetic data, deployable to client).

QMTRY Predictive Modeling for Population Health

This repo demonstrates a reproducible pipeline to identify high-risk members for 30-day readmission and potentially avoidable admissions (ACSC). It is designed to be deployed quickly on client data to reduce avoidable utilization and improve Stars.

Why it matters

Lower avoidable utilization and total cost of care

Focus care-manager time on members where interventions change outcomes

Provide transparent, audited, and fair predictions with clear next actions

Live demo

Streamlit app: population distributions, outreach worklist, ROI calculator (dark theme)

How to run
python -m venv .venv && source .venv/bin/activate  # (Windows: .venv\Scripts\activate)
pip install -r requirements.txt
python scripts/make_demo_data.py
python scripts/train.py --config configs/train_xgb.yaml
python scripts/score.py --as-of 2024-12-31
streamlit run dashboard/App.py
What’s inside

Baseline clinical scores (LACE) + ML model (GBDT)

Calibration & explainability (SHAP)

Batch scoring with CSV/XLSX export for outreach

Monitoring checks and weekly report

Governance

Model Card: /docs/model_card.md

Data Protection Checklist: /docs/data_protection_checklist.md

Engage QMTRY for a pilot

Data mapping (2–3 weeks)

Model calibration + UAT (2–3 weeks)

Shadow run + readout (3–4 weeks)

Email: sales@qmtry.ai

Compliance highlights

PHI handling & retention

De-identification/destruction

Vendor due diligence (BAA)

42 CFR Part 2 handling, if applicable

License

MIT
- Focus care‑manager time on members where interventions change outcomes
- Provide transparent, audited, and fair predictions with clear next actions


## Live demo
- Streamlit app: population distributions, outreach worklist, ROI calculator (dark theme)


## How to run
```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python scripts/make_demo_data.py
python scripts/train.py --config configs/train_xgb.yaml

What’s inside

Baseline clinical scores (LACE) + ML model (GBDT)

Calibration & explainability (SHAP)

Batch scoring with CSV/XLSX export for outreach

Monitoring checks and weekly report

Governance

Model Card in /docs/model_card.md

Data Protection Checklist in /docs/data_protection_checklist.md

Engage QMTRY for a pilot

Data mapping (2–3 weeks)

Model calibration + UAT (2–3 weeks)

Shadow run + readout (3–4 weeks)

Email: contracts@qmtry.ai

---
- PHI handling & retention
- De‑identification/destruction
- Vendor due diligence (BAA), 42 CFR Part 2 handling if applicable

---


### Appendix B — Outreach Playbook (demo)
- **Tier 1 (very high risk):** RN call within 48h, meds reconciliation, schedule PCP 7‑day visit, transport support.
- **Tier 2 (high):** care navigator call within 72h, PCP visit within 14 days, pharmacy consult if PDC<80%.
- **Tier 3 (moderate):** automated SMS + follow‑up call if symptoms/needs escalate.


---


### Appendix C — Model Card (fields)
- **Model name/version, date, owners**
- **Intended use & users, out‑of‑scope uses**
- **Training data & time horizon**
- **Performance (overall and subgroups)**
- **Calibration diagnostics**
- **Limitations/guardrails**
- **Update cadence & monitoring plan**


---


### Appendix D — Data Protection Checklist (high level)
- Data residency & VPC
- Access control & audit
- PHI handling & retention
- De‑identification/destruction
- Vendor due diligence (BAA), 42 CFR Part 2 handling if applicable

---

# QMTRY-Pophealth-Readmissions


Reproducible, audit-ready demo to predict 30-day readmissions & avoidable admissions with ML, LACE baselines, SHAP, and a Streamlit care‑manager dashboard (synthetic data, deployable to client).


### Quickstart
```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python scripts/make_demo_data.py
python scripts/train.py --config configs/train_xgb.yaml




---


# **README.md — QMTRY Predictive Modeling for Population Health**


> 🧠🏥 **Predict high‑risk members. Reduce avoidable admissions. Show your work.**
> This repository is a **reproducible, audit‑ready demo** that pairs a transparent ML model with a care‑manager workflow and an executive ROI view. Built on **synthetic data (no PHI)**, it’s ready to map to client data for a pilot.


<p align="center">
<img alt="QMTRY Predictive Modeling" src="docs/hero_tile.png" width="520"/>
</p>


---


## 🧭 Table of Contents
- [Why this exists](#-why-this-exists)
- [What you get](#-what-you-get)
- [Quickstart (5‑minute demo)](#-quickstart-5minute-demo)
- [Data & Schemas](#-data--schemas)
- [Feature Engineering](#-feature-engineering)
- [Models, Baselines & Explainability](#-models-baselines--explainability)
- [Evaluation & Calibration](#-evaluation--calibration)
- [Care‑Manager Workflow](#-caremanager-workflow)
- [Dashboard (Streamlit)](#-dashboard-streamlit)
- [ROI Calculator](#-roi-calculator)
- [Architecture](#-architecture)
- [Repo Layout](#-repo-layout)
- [Governance & Compliance](#-governance--compliance)
- [Pilot with QMTRY](#-pilot-with-qmtry)
- [FAQ](#-faq)
- [Roadmap](#-roadmap)
- [License](#-license)
- [Contact](#-contact)


---


## 🎯 Why this exists
Healthcare teams drown in readmissions and preventable admits that **could** be averted with timely outreach. Models exist—but they’re often black boxes or not integrated into daily work. This repo shows **the whole path**:


- A **transparent model** (with calibration + SHAP) that beats clinical baselines (e.g., **LACE**).
- An **operational worklist** sized to care‑team **capacity** (Top‑K) with clear **next‑best actions**.
- An **executive ROI view** that translates lift → dollars.
- A **privacy‑safe demo** built entirely on **Synthea** + synthetic SDOH/Rx signals.


---


## 📦 What you get
- **Streamlit app (dark theme)**: Population insights, **Outreach Queue**, Executive ROI.
- **Reproducible pipeline**: feature store (Parquet), training, calibration, SHAP, evaluation.
- **Baselines**: LACE/LACE+ for benchmarking.
- **Batch scoring** + optional **FastAPI** endpoint.
- **Monitoring**: drift/performance checks with a weekly report artifact.
- **Model Card** & **Data Protection Checklist** templates, already filled for the demo.


> Bonus: If you’re already building **CMS Stars** dashboards, this plugs in cleanly—exportable outreach queues, PDC distributions, **SUPD/PDC** signals, and provider attribution hooks.


---


## 🚀 Quickstart (5‑minute demo)
```bash
python -m venv .venv && source .venv/bin/activate # (Windows: .venv\Scripts\activate)
pip install -U pip wheel
pip install -r requirements.txt


# Build synthetic demo data (Synthea‑derived + SDOH/Rx enrich)
python scripts/make_demo_data.py


# Train baseline + ML (XGBoost) and calibrate
python scripts/train.py --config configs/train_xgb.yaml


# Score a cohort as of a date
python scripts/score.py --as-of 2024-12-31


# Launch dashboard (dark mode)
streamlit run dashboard/App.py

🗂️ Data & Schemas

This demo ships with synthetic tables in data_demo/. For client pilots, map your sources to our canonical schemas.

Canonical tables (silver):

member (id, dob, sex, payer, dual_status_proxy)

encounter (id, member_id, admit, discharge, los, ms_drg, admit_type, disposition)

diagnosis, procedure (ICD/PCS/SNOMED/CDM)

rx_fill (ndc, fill_date, qty, days_supply)

lab (loinc, value, normal_flag, collected_at)

vital (type, value, collected_at)

sdoh_geo (svi_theme1..4, deprivation_proxy, rural_urban)

Labels

readmit_30d: unplanned readmission within 30 days of index discharge

acsc_flag: potentially avoidable (ACSC/PQI lens) for avoidable admission analyses

Minimal client columns are listed in /schema/ with FHIR Bulk $export and 837/835 mapping notes.

🧪 Feature Engineering

Utilization: prior 12m/6m ED/IP counts, obs stays, time‑since‑last‑discharge

Clinical burden: Charlson/Elixhauser flags; CHF/COPD/DM/CKD clusters; recent abnormal labs

Discharge context: LOS, weekend discharge, disposition, polypharmacy

Adherence: PDC buckets (RASA, statins, diabetes), regimen complexity

Access: last PCP visit, open referrals, distance to care (proxy)

SDOH: SVI themes, deprivation proxy, rural/urban

Temporal: month/season, epidemic wave proxies

Features are materialized to a versioned Parquet feature store with as_of_date windows.

🤖 Models, Baselines & Explainability

Baselines: LACE/LACE+ (transparent clinical risk scores)

ML: Gradient boosting (XGBoost/LightGBM) vs. logistic regression

Calibration: Platt or isotonic; report Brier, intercept, slope

Explainability: Global SHAP bars/summary; local waterfalls for case review

Thresholding:

Top‑K (e.g., top 10%) to match care‑team capacity

Cost‑sensitive threshold using expected utility (savings − outreach cost)

See docs/model_card.md for intended use, limitations, and subgroup performance.

📈 Evaluation & Calibration

Metrics are saved in artifacts/metrics/ and visualized in the dashboard.

Discrimination: AUROC, AUPRC

Calibration: reliability plot, Brier, intercept/slope

Ranking utility: Recall/Precision @ K (worklist sized to team capacity)

Clinical utility: decision curves + ROI sensitivity

Robustness: temporal validation (rolling origin), ablation tests

🧑‍⚕️ Care‑Manager Workflow

Daily batch scores discharges in the prior 24–48h

Outreach Queue includes:

Risk score + reason codes (top SHAP features)

Suggested next‑best actions (7‑day visit, meds reconciliation, transport)

Export to CSV/XLSX for dialers/CRM

Feedback loop → monitoring & model refinement

Optional: tie in SUPD/PDC and provider attribution for Stars‑oriented outreach.

🖥️ Dashboard (Streamlit)

Population: filters, risk histogram, calibration, top features

Outreach Queue: member list with actions, export buttons

Executive: KPI tiles, ROI calculator, threshold simulator

Screenshots: add to docs/screens/ and embed here.

💸 ROI Calculator
Inputs: discharges/yr, baseline readmit %, expected reduction %, average readmit cost, outreach cost/member, capacity (Top‑K)
Outputs: gross savings, outreach cost, net savings, breakeven threshold
Example: 5,000 discharges × (14% → 12%) × $15,200 ≈ $1.52M gross/year.
Use the Executive tab to run sensitivity (±0.5%).

🏗️ Architecture
flowchart TB
A[Data Ingest] -->|FHIR Bulk $export| B[/landing/fhir/]
A -->|X12 837/835| C[/landing/claims/]
A -->|SDOH| D[/landing/sdoh/]
B & C & D --> E[Bronze: raw parquet]
E --> F[Silver: canonical tables]
F --> G[Feature Store: labels + windows]
G --> H[Training: CV + Calibration + SHAP]
H --> I[Model Registry]
G --> J[Batch Scoring]
J --> K[Streamlit App]
J --> L[Monitoring: drift & perf]

Security: Secrets in env/KeyVault, IAM least‑privilege, encryption in transit/at rest, audit logs.

🧭 Repo Layout
.
├─ README.md
├─ data_demo/
├─ schema/
├─ notebooks/
├─ src/
│ ├─ features/ ├─ labeling/ ├─ models/ ├─ eval/ ├─ explain/ ├─ scoring/ └─ monitoring/
├─ dashboard/
├─ api/
├─ ops/ (docker, github_actions, terraform)
└─ docs/ (model_card.md, data_protection_checklist.md, demo_script.md, faq.md)

🛡️ Governance & Compliance

Data: Repository uses synthetic data only; client PHI lives in client VPC.

HIPAA: Safe Harbor de‑identification path documented; access logged; least privilege.

42 CFR Part 2: Segregate SUD data; don’t train without explicit authorization.

Model governance: versioning, change logs, human override, monitoring.

Include your filled Model Card and Data Protection Checklist before any pilot.

🤝 Pilot with QMTRY

Timeline (8–10 weeks)

Data mapping & cohort definition

Feature build + baselines + early calibration

ML + explainability; care‑manager UAT

Batch scoring + shadow period

Results readout + ROI + production plan

Success metrics: ↓ readmissions, ↑ 7/14‑day follow‑ups, net savings, adoption.

❓ FAQ

Q: Can we run this on our data?
Yes—map to /schema/ and run the training/score jobs. We’ll help with FHIR $export or claims (837/835) pipelines.

Q: Is it a black box?
No—calibration plots + SHAP make decisions auditable. Baselines (LACE) included.

Q: Will it improve Stars?
It targets avoidable utilization and follow‑up care; pair with SUPD/PDC work to influence adherence metrics.

Q: Hosting model?
Local demo in this repo; client pilots in your cloud (VPC), with CI/CD and monitoring.

🗺️ Roadmap

Add ED revisit model

Expand SDOH joins (PLACES/ACS) and provider access measures

Online scoring via FastAPI with JWT

Snowflake/Databricks adapters and MLflow registry

📜 License

MIT — see LICENSE.

📫 Contact

QMTRY · sales@qmtry.ai · https://qmtry.ai
Partners & pilots welcome.

python scripts/score.py --as-of 2024-12-31
streamlit run dashboard/App.py
