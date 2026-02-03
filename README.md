# Reliability-Aware LLM-Assisted Incident Coding for UAS Safety

This repository provides code and data processing scripts supporting the paper:

**“LLM-Assisted Incident Coding for UAS Safety: Reliability-Aware Human-Factor Extraction and Operational Risk Analytics”**

The project focuses on automated extraction and analysis of safety factors from aviation and UAS incident narratives using large language models (LLMs), with an emphasis on reliability auditing, evidence grounding, and operational risk analytics.

---

## Overview

Unmanned Aircraft Systems (UAS) and aviation safety analysis rely heavily on free-text incident narratives, which are difficult to process at scale due to their unstructured nature and subjectivity.  
This repository implements a reliability-aware pipeline that:

- Processes incident narratives from ASRS-style datasets;
- Performs automated safety factor extraction using constrained LLM prompting;
- Evaluates extraction reliability via self-consistency and evidence stability;
- Provides baseline comparisons using classical NLP methods (TF–IDF + One-vs-Rest);
- Supports downstream risk-weighted analytics.

The code is designed for **research reproducibility** and **methodological transparency**, rather than production deployment.

---

## Repository Structure

─ data/
│ ├── asrs_narratives_clean.csv # Cleaned ASRS-style narratives
│ ├── asrs_paper_dataset.csv # Full dataset used in experiments
│ └── asrs_paper_dataset_sample.csv # Sample subset for quick testing
│
├── notebooks/
│ └── Untitled60.ipynb # Main experimental notebook
│
├── results/
│ └── metrics.csv # Evaluation metrics (if generated)
│
└── README.md


---

## Dataset Description

Each incident record includes:

- `incident_id`: Unique identifier  
- `narrative`: Free-text incident description  
- `labels`: Safety factor annotations (when available or derived)

All narratives are anonymized and originate from publicly available aviation safety reporting systems.  
Records with empty or incomplete narratives were removed during preprocessing.

⚠️ **Note**: This repository does not redistribute proprietary or restricted datasets. Users are responsible for ensuring compliance with the original data source’s usage policies.

---

## Methods Implemented

### 1. Baseline Incident Coding
- Rule-based substring matching (for comparison only)
- TF–IDF + One-vs-Rest linear classifier (SGD)

### 2. LLM-Assisted Extraction (Conceptual)
- Constrained prompting using a predefined safety factor taxonomy
- Evidence span extraction from original narratives
- Multiple decoding runs per incident (for robustness analysis)

### 3. Reliability and Consistency Analysis
- Self-consistency across repeated LLM runs
- Token-level overlap for evidence stability
- Comparison with expert annotations (when available)

---

## Running the Experiments

### Requirements

- Python ≥ 3.8
- Common scientific Python stack:
  - `numpy`
  - `pandas`
  - `scikit-learn`
  - `matplotlib`

(Optional) For LLM-based experiments:
- Access to an external LLM API or locally hosted model

### Quick Start

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-name>


Open the main notebook:

jupyter notebook notebooks/Untitled60.ipynb


Follow the notebook cells to:

Load and inspect the dataset

Train baseline models

Compute evaluation metrics

The sample dataset (asrs_paper_dataset_sample.csv) can be used for fast experimentation.

Reproducibility Notes

Random seeds are fixed where applicable for baseline models.

Evaluation metrics reported in the paper correspond to the test split described in the notebook.

LLM-based results may vary depending on model choice, decoding parameters, and API versions.

Use of Generative AI

Generative AI tools were used to assist with language polishing, code structuring, and LaTeX formatting during manuscript preparation.
All scientific content, experimental design, analysis, and interpretations were conducted and verified by the author, who assumes full responsibility for the work.

Citation

If you use this code or build upon this work, please cite the associated paper.

@article{yang2026uas_llm,
  title   = {LLM-Assisted Incident Coding for UAS Safety: Reliability-Aware Human-Factor Extraction and Operational Risk Analytics},
  author  = {Yang, Youla},
  journal = {Drones},
  year    = {2026}
}

License

This repository is provided for academic and research purposes only.
Please consult the original data sources for their respective licensing terms.
