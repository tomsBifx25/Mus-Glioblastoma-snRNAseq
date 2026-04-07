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
│   ├── Check01_EDA.ipynb                  # Data loading, cleaning, initial EDA
├── Data/
│   └── Cohort-Old.csv                     # Young cohort sn RNA seq data
│   └── Cohort-Young.csv                   # Old cohort sn RNA seq data
│   └── UMAP.h5ad                          # UMAP data
├── Results/
│   ├── fig01_gen_Reads-Genes.png          # Reads vs. Genes (scatter plot)
│   ├── fig02_gen_Reads-Genes-byType.png   # Reads vs. Genes by Cell Type (scatter plot)
│   ├── fig03_gen_Reads-Genes-bySex.png    # Reads vs. Genes by Sex (scatter plot)
│   ├── fig04_gen_Distrib-Reads.png        # Distribution of Reads by Cell type (violin plot)
│   ├── fig05_gen_Distrib-Genes.png        # Distribution of Genes by Cell type (violin plot)
├── src/
│   └── preprocess.py                      # Possible preprocess cleaning needed
├── README.md                              # Project Overview
└── requirements.txt                       # List of possible dependencies
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
git clone https://github.com/tomsBifx25/Mus-Glioblastoma-snRNAseq.git
cd Mus-Glioblastoma-snRNAseq

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter notebook
```

Open notebooks in order: `Check01_EDA.ipynb`

---

## Key Results & Plots

| Figure | File | Description |
|---|---|---|
| Fig 1 | `results/fig01_gen_Reads-Genes.png` | Number of Reads by Number of Genes (scatter plot) |
| Fig 2 | `results/fig02_gen_Reads-Genes-byType.png` | Reads vs. Genes by Cell type (scatter plot) |
| Fig 3 | `results/fig03_gen_Reads-Genes-bySex.png` | Reads vs. Genes by Sex (scatter plot) |
| Fig 4 | `results/fig04_gen_Distrib-Reads.png` | Distribution of the number of Reads by Cell type (violin plot) |
| Fig 5 | `results/fig05_gen_Distrib-Genes.png` | Distribution of the number of Genes by Cell type (violin plot) |

---

## Dependencies

See `requirements.txt`. Core packages:

```
pandas>=1.5
numpy>=1.23
matplotlib>=3.6
seaborn>=0.12
scanpy>=1.12
scikit-learn>=1.2
scipy>=1.10
jupyter
```

---

## References

1. Darmanis, S., Sloan, S. A., et al. (2023). "Transcriptional programs of glioblastoma subclasses are preserved in the tumor microenvironment." Nature Communications, 14(1), 3848. PMID: 37400346 DOI: 10.1038/s41467-023-39434-2

2. Mayo clinic, for information behind Glioblastoma (GBM). https://www.mayoclinic.org/diseases-conditions/glioblastoma/symptoms-causes/syc-20569077

3. Stephanie Hicks, "Welcome to the World of Single-Cell RNA-Sequencing". https://learn.gencore.bio.nyu.edu/single-cell-rnaseq/

4. Gemini was used in the modification and use of some python scripts for this project.

5. Dr. Sarangan (Ravi) Ravichandran and Dr. Randall Johnson from Hood College for their contributions in the form of knowledge gained through lectures, lecture notes and workbooks.

---

*BIFX-546 · Hood College · Spring 2026 · Thomas Walsh · Dr. Sarangan Ravichandran (Instructor)*
