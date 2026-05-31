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
