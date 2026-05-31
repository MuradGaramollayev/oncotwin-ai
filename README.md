# OncoTwin-AI

**AI-powered digital twin system for personalised glioblastoma clinical decision support**

[![TRL](https://img.shields.io/badge/TRL-4-blue)](https://en.wikipedia.org/wiki/Technology_readiness_level)
[![Dataset](https://img.shields.io/badge/Dataset-TCGA--GBM-orange)](https://www.cancer.gov/ccg/research/genome-sequencing/tcga)
[![Model](https://img.shields.io/badge/Model-Cox%20%2B%20XGBoost-green)](https://xgboost.readthedocs.io)
[![License](https://img.shields.io/badge/License-MIT-lightgrey)](LICENSE)
[![TEKNOFEST](https://img.shields.io/badge/TEKNOFEST-2026%20Semifinalist-red)](https://www.teknofest.org)

---

## Overview

OncoTwin-AI is an interactive clinical decision support prototype for glioblastoma multiforme (GBM). It integrates multimodal patient data — MRI radiomics, genetic/epigenetic biomarkers, and clinical parameters — into a single AI pipeline that generates personalised risk predictions, treatment simulations, and explainable prognostic outputs.

The system is designed around one principle: move GBM management from reactive to proactive. Rather than waiting for progression to appear on imaging, OncoTwin-AI predicts it before it becomes clinically apparent — giving oncologists the window to act.

> Built for the **TEKNOFEST 2026 Oncology 3T Competition** — Team KHAZAR, Application ID 5014245.

---

## Live Demo

The prototype runs entirely in the browser as a standalone HTML file. No installation, no backend, no dependencies to install.

**[Download index.html → open in Chrome](index.html)**

1. Open `index.html` in any modern browser
2. Click **▶ Run Analysis** (top right or top of Patient data panel)
3. Navigate through the 10 panels using the left sidebar

---

## Key Features

### Core Pipeline
| Panel | Description |
|---|---|
| 1. Patient data | Input form: demographics, MRI radiomics, genetic markers, treatment history, concomitant medications |
| 2. Feature extraction | 107 radiomic features per IBSI standards, genetic encoding, combined 130–150-dimensional phenotype matrix |
| 3. AI model + MRI | Cox PH + XGBoost hybrid, Kaplan-Meier survival curve, AI-reconstructed MRI visualisation, histopathology H&E slide, WHO 2021 grade assessment |
| 4. Digital twin | Tumour progression timeline, volume response chart, longitudinal survival modelling |
| 5. Risk output | Risk score (0–100), PFS prediction, 6-month and 12-month survival probability, clinical recommendations with evidence links |

### Advanced Features
| Panel | Description |
|---|---|
| 6. Explainable AI | SHAP value waterfall chart, positive/negative feature contributions, top drivers and protective factors |
| 7. Treatment simulator | 8 protocols across newly diagnosed and recurrent GBM categories, per-protocol risk scores, cost/affordability estimates, drug-drug interaction checker, evidence-linked recommendations |
| 8. Longitudinal monitoring | Baseline/Month 3/Month 6 comparison, risk trend chart, monitoring schedule |
| 9. 3D Visualisation | Real-time interactive Three.js brain model with tumour, necrosis, oedema; drag/zoom/rotate; progression timeline slider |
| 10. Clinical report | Printable summary with all AI outputs, prognostic timeline, recommendations, disclaimer |

### Clinical Safety Modules
- **Pseudoprogression assessment** — RANO criteria checklist, probability gauge, follow-up imaging protocol
- **Model confidence calibration** — population fit score, validation status, honest uncertainty reporting
- **Drug-drug interaction checker** — real-time check of concomitant medications against selected protocol (warfarin, valproate, phenytoin, LMWH, DOACs, CYP3A4 inhibitors vs TMZ/bevacizumab/lomustine)
- **Evidence links** — every recommendation cites the source trial (Stupp 2005, AVAglio, EF-14, CeTeG, RANO, etc.)

---

## Treatment Protocols Covered

**Newly Diagnosed GBM**
- Standard of Care (Stupp protocol)
- SOC + Bevacizumab
- SOC + Tumour Treating Fields (Optune)
- SOC + Bevacizumab + TTF (triple combination)

**Recurrent GBM**
- Lomustine (CCNU) monotherapy
- Bevacizumab monotherapy
- Bevacizumab + Lomustine (BELOB)
- Re-Irradiation + Systemic Therapy

---

## Technical Architecture
Patient Input
│
├── MRI Radiomics (107 features, PyRadiomics/IBSI)
├── Molecular Profile (MGMT, IDH, EGFR, TERT, 1p/19q)
└── Clinical Parameters (age, KPS, surgery, treatment)
│
▼
Phenotype Matrix [130–150 dim]
│
├── Cox Proportional Hazards → PFS / OS curves
└── XGBoost Classifier → Risk stratification (low/intermediate/high)
│
├── SHAP → Feature attribution
├── Digital Twin Simulation → What-if treatment scenarios
└── Clinical Interface → Dashboard output
**Validation target:** C-index ≥ 0.75 on TCGA-GBM (n=262)
**Synthetic cohort:** 500 records, KS-tested against TCGA-GBM distributions

---

## Technology Stack

| Layer | Libraries |
|---|---|
| Data processing | pandas, numpy |
| Radiomics | PyRadiomics 3.0 (IBSI-compliant) |
| Survival modelling | lifelines (Cox PH) |
| Classification | XGBoost 2.0 |
| Explainability | SHAP 0.43 |
| Simulation | scipy.stats (Weibull), Monte Carlo perturbation |
| Visualisation | Chart.js 4.4, Three.js r128, matplotlib, plotly |
| Interface | Streamlit (planned) / standalone HTML (current prototype) |

All libraries are open source. Zero licensing costs.

---

## Dataset

**TCGA-GBM** — The Cancer Genome Atlas, Glioblastoma Multiforme
262 patients with matched MRI imaging, genomic profiles (IDH, MGMT, 1p/19q), clinical metadata, and survival outcomes.

- MRI data: [TCIA TCGA-GBM Collection](https://www.cancerimagingarchive.net/collection/tcga-gbm/)
- Genomic data: [cBioPortal GBM (TCGA, PanCancer Atlas)](https://www.cbioportal.org/study/summary?id=gbm_tcga_pan_can_atlas_2018)

---

## TRL Status

| Stage | Status | Description |
|---|---|---|
| TRL 1 | Complete | Basic principles observed |
| TRL 2 | Complete | Technology concept formulated |
| TRL 3 | In progress | Analytical proof-of-function |
| TRL 4 | Target | Laboratory prototype on TCGA-GBM |
| TRL 5–6 | Planned | Pilot studies in AZ/TR oncology clinics |

---

## Roadmap

**Short term (0–12 months)**
- Full validation on TCGA-GBM
- Academic publication preparation
- Streamlit web prototype

**Medium term (1–3 years)**
- Retrospective pilot: oncology clinics in Azerbaijan and Turkey (IRB approval)
- CE mark / MDR regulatory preparation
- Fine-tuning on local patient cohorts

**Long term (3–5 years)**
- PACS / HIS integration
- SaaS subscription model
- Expansion to other high-grade gliomas

---

## Ethical Framework

**Explainability** — Every prediction includes a SHAP breakdown. The system never makes a final decision. The treating physician always has the last word.

**Privacy** — Patient data processed anonymously per GDPR and KVKK. Local deployment option available — nothing leaves the hospital network.

**Fairness** — Model performance monitored across age, sex, and ethnic groups. Fairness audits repeated as the dataset grows.

**Regulatory pathway** — OncoTwin-AI is classified as Clinical Decision Support Software (CDSS). Applicable frameworks: FDA SaMD, EU MDR 2017/745, Turkish Ministry of Health regulations.

> **Disclaimer:** This prototype is for research and demonstration purposes only. It does not constitute medical advice and must not be used as the sole basis for clinical decisions.

---

## Team

**Team KHAZAR** — TEKNOFEST 2026, Oncology 3T Competition
Application ID: 5014245 | Team ID: 757459

---

## Key References

1. Stupp et al. (2005). RT + TMZ for glioblastoma. *NEJM* 352:987–996.
2. Hegi et al. (2005). MGMT gene silencing and TMZ benefit. *NEJM* 352:997–1003.
3. Kickingereder et al. (2016). Radiomic profiling of GBM. *Radiology* 280:880–889.
4. Stupp et al. (2017). TTFields + TMZ (EF-14 trial). *JAMA* 318:2306–2316.
5. Herrlinger et al. (2019). Lomustine-TMZ in MGMT-methylated GBM (CeTeG). *Lancet* 393:678–688.
6. Wen et al. (2010). RANO criteria for high-grade glioma. *JCO* 28:1963–1972.
7. Lundberg & Lee (2017). SHAP: unified approach to model interpretation. *NIPS*.

---

*OncoTwin-AI — From population statistics to patient-specific prediction.*
