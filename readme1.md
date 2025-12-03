# LOGINTEL – AI-Enabled Threat Log Analyzer

*A semantics-aware, adversarially-robust webserver log anomaly detection system*

---

## Table of Contents

* [Overview](#overview)
* [Key Capabilities](#key-capabilities)
* [System Architecture](#system-architecture)

  * [Feature Engineering Layer](#feature-engineering-layer)
  * [Adversarial Defense Layer](#adversarial-defense-layer)
  * [Sequence Classification Layer](#sequence-classification-layer)
  * [Webserver Threat Analysis Flow](#webserver-threat-analysis-flow)
* [Technology Stack](#technology-stack)
* [Project Structure](#project-structure)

  * [Main Pipeline](#main-pipeline)
  * [Experiments](#experiments)
* [Dataset & Preprocessing](#dataset--preprocessing)
* [Usage](#usage)
* [Results](#results)
* [Extending the Project](#extending-the-project)
* [Future Improvements](#future-improvements)
* [Contributors](#contributors)

---

## Overview

**LogIntel** automates cyber-threat detection from **webserver logs** using statistical, semantic, and temporal behavior learning.
It integrates:

✔ SBERT-based embeddings
✔ Topic models (LDA)
✔ Sequential learning via **BiGRU / GRU**
✔ Explainability through **SHAP**
✔ **Adversarial log generation** to improve model robustness

The project serves as a foundation for **production-level** Information Security Monitoring Systems.

---

## Key Capabilities

| Module                     | Purpose                                                      |
| -------------------------- | ------------------------------------------------------------ |
| Semantic Log Understanding | Transformer-based embeddings (SBERT, DistilRoBERTa, ELECTRA) |
| Threat Behaviour Modeling  | Time+Geo patterns, response anomalies, burst scanning        |
| Robust Detection           | Adversarial log training                                     |
| Explainability             | SHAP visualization of harmful features                       |
| UI Deployment              | Streamlit-based real-time inference system                   |

---

## System Architecture

```
Raw Webserver Logs
       │
       ▼
Feature Engineering (Semantic + Statistical + Topic Models)
       │
       ▼
Adversarial Training (Defense Model Ensemble)
       │
       ▼
GRU/BiGRU Threat Classifier
       │
       ▼
Threat Labelling, Explainability, UI Deployment
```

### Feature Engineering Layer

* SBERT sentence embeddings
* Request frequency patterns
* Geolocation from IP
* Topic modeling (LDA)

### Adversarial Defense Layer

* Synthetic malicious traffic variants
* Robust ensemble training

### Sequence Classification Layer

* GRU for sequential event understanding
* BiGRU for improved long-range context

### Webserver Threat Analysis Flow

1. Parse Apache/Nginx logs
2. Extract numerical + semantic features
3. Classify threats (anomaly vs benign)
4. Visualize explainability
5. Optionally deploy as a security assistant UI

---

## Technology Stack

| Category       | Technology                                   |
| -------------- | -------------------------------------------- |
| Language       | Python 3.8+                                  |
| ML             | PyTorch, Scikit-learn, Sentence-Transformers |
| Explainability | SHAP                                         |
| Visualization  | Matplotlib, Streamlit UI                     |
| Deployment     | Streamlit / PyCharm                          |
| Data Handling  | Pandas, NumPy                                |

---

## Project Structure

```
LOGINTEL/
├─ main/
│  ├─ Feature Eng.py
│  ├─ Adversarial Training.py
│  └─ GRU Classification.py
│
├─ Experiments/
│  ├─ distilroberta.py
│  ├─ electra_2_0.py
│  ├─ knowledge_graph_embedding.py
│  ├─ Topic_modelling_lda features.py
│  ├─ week_3.py
│  ├─ week3_1.py
│  ├─ week4.py
│  ├─ week5(shap).py
│  ├─ week5_(semantic_features_loganamoly).py
│  ├─ week5_1.py
│  │
│  └─ Webserver Log Experiments/
│     ├─ Initial Work/
│     │  ├─ Feature Extraction.ipynb
│     │  └─ Webserver(distilRoBERTa).ipynb
│     │
│     └─ main pipeline/
│        ├─ Main Feature Engineering.ipynb
│        ├─ GRU_Webserver.ipynb
│        ├─ BiGRU Threat Classification.ipynb
│        ├─ GRU Streamlit Deployment.ipynb
│        ├─ streamlit_deployment.py
│        └─ KBs/
│
├─ requirements.txt
└─ README.md (this file)
```

> *This structure matches the current state shown in your uploaded files.*

---

## Dataset & Preprocessing

* Apache/Nginx style web logs — access records
* Parsed into structured request fields:

  * IP Address → Geo lookup
  * Method, URL, Response Code
  * Timestamps → Request burst analysis
* Noise removal, token normalization, lowercasing

✔ Serialized features stored as `results/features.pkl`

---

## Usage

### Run Full Pipeline

```bash
python "main/Feature Eng.py"
python "main/Adversarial Training.py"
python "main/GRU Classification.py"
```

### Run Individual Experiments

```bash
python "Experiments/distilroberta.py" --data results/features.pkl
```

### Launch Threat Detection UI

```bash
streamlit run Experiments/main\ pipeline/streamlit_deployment.py
```

---

## Results

| Model                  | Accuracy                       | F1    | AUC   |
| ---------------------- | ------------------------------ | ----- | ----- |
| DistilRoBERTa baseline | ~0.85                          | ~0.84 | ~0.89 |
| GRU classifier         | ↑ improved temporal modeling   |       |       |
| BiGRU classifier       | ↑ best performance, stable AUC |       |       |

*SHAP* reveals:

* Suspicious URL entities
* High-frequency anomalous scanning
* Hostile IP geo-patterns

---

## Extending the Project

| Feature                        | How to add                    |
| ------------------------------ | ----------------------------- |
| New log sources                | Update parsing pipeline       |
| NER-based threat understanding | Add security entity extractor |
| Real-time deployment           | Dockerize Streamlit app       |
| SIEM compatibility             | Create JSON export handlers   |

---

## Future Improvements

🚀 Threat cohort clustering
🔐 Integration with production SIEM tools
⚡ GPU-optimized inference pipelines
🛰 Active monitoring with periodic retraining

---

## Contributors
**Gourab Mahato**
📧 [gourabmahato09@gmail.com](mailto:gourabmahato09@gmail.com)
