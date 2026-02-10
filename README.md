# Emotion Detection on hate speech and gender-based violence texts on social media

This repository contains the materials developed during my ISTAT–ENSAI internship, organized as a research-oriented pipeline for **data preparation, experimentation, and reporting**. It accompanies the thesis/internship report and is intended to support transparency and reproducibility.

**Main artifacts included in this repository**

* Full internship report (PDF): `DiDonfrancesco_InternshipReport.pdf` ([GitHub][1])
* Internship presentation (PDF): `internship_presentation-1.pdf` ([GitHub][1])
* Data preparation notebooks: `data_cleaning.ipynb`, `testData_cleaning.ipynb` ([GitHub][1])
* Modeling notebook: `main_models.ipynb` ([GitHub][1])
* Data folders: `Data_Raw/`, `Data_Cleaned/` ([GitHub][1])
* Experiment tracking export: `wandb_logs.csv` ([GitHub][1])

---

## 1. Research Context and Objectives

The internship project is situated at the intersection of:

* **computational social science / NLP**, and
* **statistical learning for social-media text**.

The overall objective is to build a clean, documented workflow supporting:

1. **data ingestion and preprocessing**,
2. **model development and evaluation**, and
3. **research reporting** in a thesis-style format.

For the complete motivation, research questions, and formal problem definition, refer to:

* `DiDonfrancesco_InternshipReport.pdf` ([GitHub][1])

---

## 2. Repository Structure

```
.
├── Data_Raw/                     # raw inputs (as collected / received)
├── Data_Cleaned/                 # processed datasets ready for modeling
├── Documentation/                # auxiliary documentation (notes, assets, references)
├── data_cleaning.ipynb           # main cleaning + preprocessing pipeline
├── testData_cleaning.ipynb       # cleaning of data for the model testing
├── main_models.ipynb             # modeling + evaluation notebook
├── wandb_logs.csv                # experiment logs export (Weights & Biases)
├── DiDonfrancesco_InternshipReport.pdf
└── internship_presentation-1.pdf
```

---

## 3. Data

### 3.1 Data Sources

* The raw data are stored in `Data_Raw/`. ([GitHub][1])
* Processed/cleaned versions used for modeling are stored in `Data_Cleaned/`. ([GitHub][1])

### 3.2 Data Format and Fields

The expected structure, key columns, and any label schema used for learning tasks are documented in:

* `DiDonfrancesco_InternshipReport.pdf` ([GitHub][1])

---

## 4. Methods

The repository implements a standard research pipeline:

### 4.1 Preprocessing and Cleaning

Performed in:

* `data_cleaning.ipynb` ([GitHub][1])
* `testData_cleaning.ipynb` ([GitHub][1])

Typical steps include (see notebooks/report for exact choices):

* text normalization (case, punctuation, whitespace),
* tokenization and optional lemmatization/stemming,
* handling missing values and duplicates,
* train/validation/test preparation (when relevant),
* optional balancing strategies.

### 4.2 Modeling and Experiments

All modeling experiments are centralized in:

* `main_models.ipynb` ([GitHub][1])

The notebook is designed to support:

* baseline and/or stronger supervised models,
* consistent evaluation protocol,
* reproducible training settings.

### 4.3 Experiment Tracking

* `wandb_logs.csv` contains an exported log of experiments (e.g., metrics and hyperparameters). ([GitHub][1])
  This enables:
* comparison across runs,
* reporting of best-performing configurations,
* post-hoc analysis for the thesis write-up.

---

## 5. Results and Thesis-Style Reporting

### 5.1 Where to find the results

Primary results and discussion are in:

* `DiDonfrancesco_InternshipReport.pdf` ([GitHub][1])

A condensed version is in:

* `internship_presentation-1.pdf` ([GitHub][1])

---

## 6. Reproducibility

### 6.1 Environment

This repository is notebook-based (Jupyter). ([GitHub][1])
To reproduce results:

* Use a clean Python environment
* Ensure standard ML/NLP dependencies are installed (e.g., numpy/pandas/scikit-learn + any deep learning stack used in the notebook).

---

## 7. Ethics, Bias, and Limitations

Because the project concerns human language in online settings, careful attention is required for:

* annotation subjectivity (when labels exist),
* representativeness and sampling biases,
* privacy and data governance,
* risk of amplifying harmful content in modeling pipelines.

The report discusses limitations and ethical considerations:

* `DiDonfrancesco_InternshipReport.pdf` ([GitHub][1])

---


## 8. Acknowledgements

This project was developed in the context of an internship involving ISTAT and ENSAI.
Acknowledgements and institutional context are detailed in:

* `DiDonfrancesco_InternshipReport.pdf` ([GitHub][1])

---

[1]: https://github.com/Sergio-ddf/internship-istat-ensai "GitHub - Sergio-ddf/internship-istat-ensai"
