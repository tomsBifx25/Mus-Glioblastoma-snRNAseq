# Comparative Single-Nucleus Transcriptomics of Glioblastoma Across the Lifespan
### BIFX-546: Machine Learning for Bioinformatics — Spring 2026

**Team Members:**
- Thomas Walsh (tjw8@hood.edu)

---

## Project Goal

How does the age-dependent Tumor microenvironment diverge in glioblastoma contexts between young and aged mice?

Aging is the primary risk factor for glioblastoma (GBM) and significantly correlates with poorer prognosis. While much research focuses on the tumor's genetic mutations, the age-dependent microenvironment remains under-explored. This dataset is unique because it provides high-resolution, single-nucleus RNA sequencing (snRNA-seq) across "young" and "aged" cohorts, allowing for a granular look at how the aging brain environment modulates cancer progression and immune evasion.

---

## Dataset

| Field | Details |
|---|---|
| **Name** | longevity-db/mouse-glioblastoma-snRNAseq (2025) |
| **Source** | Hugging Face |
| **URL** | https://huggingface.co/datasets/longevity-db/mouse-glioblastoma-snRNAseq |
| **Size** | ~431,000 single nucleus RNA-seq counts, 29 features |
| **Citation** | Darmanis, S., Sloan, S. A., et al. (2023) "Transcriptional programs of glioblastoma subclasses are preserved in the tumor microenvironment." Nature Communications, 14(1), 3848. PMID: 37400346 DOI: 10.1038/s41467-023-39434-2 |

This dataset comprises single-nucleus RNA sequencing (snRNA-seq) data from the brain (glioblastoma tumors and their microenvironment) of both young and aged mice. It provides a high-resolution cellular and molecular census of glioblastoma, a highly aggressive brain tumor, with crucial insights into its age-related characteristics.

The original data was sourced from a CELLxGENE Discover collection titled "Glioblastoma from young and aged mice." This processed version has been transformed from its original AnnData format into standardized .parquet files, enhancing its usability for machine learning, bioinformatics pipelines, and enabling detailed analysis of age-dependent changes in glioblastoma.

---

## Techniques Used

| Phase | Technique |
|---|---|
| EDA | Descriptive statistics (mean, median, std, IQR) |
| EDA | Scatter plots, Distribution plots, correlation heatmap |
| Analysis | Chi-square test of independence (readmission vs. diagnosis group) |
| Analysis | Bootstrap confidence intervals on readmission rate |
| Modeling | Logistic Regression with train/test split (80/20) |
| Modeling | Decision Tree for feature importance comparison |
| Evaluation | Accuracy, Precision, Recall, AUC-ROC |

---

## Repository Structure

```
Mus-Glioblastoma-snRNAseq/
├── Notebooks/
│   ├── 01_eda.ipynb              # Data loading, cleaning, EDA
├── Data/
│   └── README_data.md            # Link to UCI source; raw file not included (>50MB)
│   └── README_data.md            # Link to UCI source; raw file not included (>50MB)
│   └── README_data.md            # Link to UCI source; raw file not included (>50MB)
├── Results/
│   ├── fig01_gen_Reads-Genes.png
│   ├── fig02_gen_Reads-Genes-byType.png
│   ├── fig03_gen_Reads-Genes-bySex.png
│   ├── fig04_gen_Distrib-Reads.png
│   ├── fig05_gen_Distrib-Genes.png
├── src/
│   └── preprocess.py             # Reusable cleaning functions
├── README.md
└── requirements.txt
```

---

## How to Run

### Option 1 — Google Colab (recommended, no install needed)

1. Open [Google Colab](https://colab.research.google.com)
2. Click **File → Open notebook → GitHub**
3. Paste this repo URL and select the notebook you want to run
4. Run the first cell to install dependencies:
   ```python
   !pip install -r requirements.txt
   ```
5. Run all cells: **Runtime → Run all**

> **Note:** The dataset is downloaded automatically in the first notebook cell from the
> UCI URL. No manual download required.

### Option 2 — Local Jupyter

```bash
# Clone the repo
git clone https://github.com/yourteam/diabetes-readmission.git
cd diabetes-readmission

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter notebook
```

Open notebooks in order: `01_eda.ipynb` → `02_hypothesis_testing.ipynb` → `03_modeling.ipynb`

---

## 📈 Key Results & Plots

| Figure | File | Description |
|---|---|---|
| Fig 1 | `results/fig1_readmission_by_age.png` | Readmission rate by age group (bar chart) |
| Fig 2 | `results/fig2_correlation_heatmap.png` | Correlation matrix of numeric clinical features |
| Fig 3 | `results/fig3_roc_curve.png` | ROC curve comparing logistic regression vs. decision tree |

**Model performance summary:**

| Model | Accuracy | Precision | Recall | AUC-ROC |
|---|---|---|---|---|
| Logistic Regression | 0.74 | 0.61 | 0.58 | 0.79 |
| Decision Tree | 0.70 | 0.57 | 0.62 | 0.74 |

---

## 📝 Summary of Findings

Our EDA revealed that readmission rates differ substantially across age groups, with
patients aged 70–80 showing the highest 30-day readmission rate (~14%). A chi-square
test confirmed a statistically significant association between primary diagnosis category
and readmission status (p < 0.001), and bootstrap confidence intervals placed the
overall readmission rate at 11.2% ± 0.4%.

The logistic regression model achieved an AUC-ROC of 0.79, outperforming the
decision tree (0.74). The three strongest predictors of readmission were number of
inpatient visits in the prior year, number of diagnoses recorded at discharge, and
HbA1c result. These findings suggest that care-transition planning — particularly for
high-comorbidity patients with prior hospitalizations — may be the highest-yield
intervention target. Limitations include the dataset's age (1999–2008) and the
exclusion of social determinants of health, which likely confound readmission risk.

---

## 📦 Dependencies

See `requirements.txt`. Core packages:

```
pandas>=1.5
numpy>=1.23
matplotlib>=3.6
seaborn>=0.12
scikit-learn>=1.2
scipy>=1.10
jupyter
```

---

## 📜 References

1. Strack, B., DeShazo, J.P., et al. (2014). Impact of HbA1c Measurement on Hospital
   Readmission Rates: Analysis of 70,000 Clinical Database Patient Records.
   *BioMed Research International*, Article ID 781670.
   https://doi.org/10.1155/2014/781670

2. UCI Machine Learning Repository. (2014). Diabetes 130-US Hospitals Dataset.
   https://archive.ics.uci.edu/dataset/296

3. Grus, J. (2019). *Data Science from Scratch* (2nd ed.). O'Reilly Media.

---

*BIFX-546 · Hood College · Spring 2026 · Dr. Sarangan Ravichandran*
