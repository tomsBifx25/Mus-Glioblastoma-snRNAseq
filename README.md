# Age-Dependent Transcriptional and Cellular Features of the Glioblastoma Microenvironment Revealed by Single-Nucleus RNA Sequencing

*Thomas Walsh | March 18, 2026*
   *(tomjw31@gmail.com)*
   *(tjw8@hood.edu)*

---

## Hood College
* Machine Learning for Bioinformatics *(BIFX 546)*, Spring 2026
* Instructor: Dr. Sarangan (Ravi) Ravichandran

---

## Project Goal
### Research Question:
How do gene expression patterns and cellular compositions differ between young and aged glioblastoma microenvironments, and which transcriptional features best distinguish these age-dependent states?

### Relevance:
Aging is the strongest risk factor for glioblastoma and is associated with worse outcomes, yet the biological basis for this disparity remains incompletely understood. While prior work has focused heavily on tumor-intrinsic mutations, age-related differences in the tumor microenvironment may play a critical role in disease progression. Using single-nucleus RNA sequencing *(snRNA-seq)* data from young and aged mouse glioblastoma models, this study investigates both transcriptional changes and shifts in cellular structure. By integrating differential expression, clustering, and machine learning, the aim is to identify key genes and cellular patterns that distinguish age-dependent tumor states and provide insight into mechanisms that may underlie age-associated disease severity.

---

## Dataset
| Field | Details |
|---|---|
| **Name** | longevity-db/mouse-glioblastoma-snRNAseq (2025) |
| **Source** | Hugging Face |
| **URL** | https://huggingface.co/datasets/longevity-db/mouse-glioblastoma-snRNAseq |
| **Size** | ~431,000 single nucleus RNA-seq counts, 29 features |
| **Citation** | Darmanis, S., Sloan, S. A., et al. (2023) "Transcriptional programs of glioblastoma subclasses are preserved in the tumor microenvironment." Nature Communications, 14(1), 3848. PMID: 37400346 DOI: 10.1038/s41467-023-39434-2 |
| **Original Dataset** | *"Single Cell RNA Sequencing of Young and Aged Murine Glioblastoma"* |
| **Original Source** | https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE215239 |
| **Original Citation** | NCBI Gene Expression Omnibus. (2024). Single-cell RNA sequencing of young and aged murine glioblastoma (GEO Series GSE215239). Retrieved from https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE215239 |

This dataset comprises single-nucleus RNA sequencing (snRNA-seq) data from the brain (glioblastoma tumors and their microenvironment) of both young and aged mice. It provides a high-resolution cellular and molecular census of glioblastoma, a highly aggressive brain tumor, with crucial insights into its age-related characteristics.

The original data was sourced from NCBI Gene Expression Omnibus (GEO) (2024) under accession number GSE215239 (https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE215239).

---

## Techniques Used

| Phase | Technique |
|---|---|
| EDA | Descriptive statistics, Data Cleaning |
| EDA | QC and Normalization, Distribution plots |
| Analysis | Highly Variable Genes, Dimensionality Reduction: PCA |
| Analysis | Dimensionality Reduction: Compute Neighbourhood Graphs, UMAP |
| Analysis | Leiden clustering, Differential Expression Analysis (DEA) |
| Modeling | train/test split (80/20), Random Forest Classifier |
| Modeling | Evaluation, Feature Importance |
| Analysis | Gene Set Enrichment Analysis (GSEA) |

---

## Repository Structure
```
Mus-Glioblastoma-snRNAseq/
├── data/
│   ├── Old_GBM_barcodes.tsv.gz
│   ├── Old_GBM_features.tsv.gz
│   ├── Old_GBM_matrrix.mtx.gz
│   ├── Young_GBM_barcodes.tsv.gz
│   ├── Young_GBM_features.tsv.gz
│   ├── Young_GBM_matrrix.mtx.gz
├── notebooks/
│   └── GBM_snRNAseq_workflow.ipynb            # Full ML workflow
├── results/
│   ├── figures/
|   │   ├── Fig01_Young_mito_gene_percent.png
|   │   ├── Fig02_Old_mito_gene_percent.png
|   │   ├── Fig03_Young_totalCounts.png
|   │   ├── Fig04_Old_totalCounts.png
|   │   ├── Fig05_Young_nGenes_expr.png
|   │   ├── Fig06_Old_nGenes_expr.png
|   │   ├── Fig07_Young_HVGs.png
|   │   ├── Fig08_Old_HVGs.png
|   │   ├── Fig09_Young_PCA.png
|   │   ├── Fig10_Old_PCA.png
|   │   ├── Fig11_Young_UMAPcounts.png
|   │   ├── Fig12_Old_UMAPcounts.png
|   │   ├── Fig13_UMAPclusters.png
|   │   ├── Fig14_Young_topGenes.png
|   │   ├── Fig15_Old_topGenes.png
|   │   ├── Fig16_Expr_dotplot.png
|   │   ├── Fig17_topExpr_violins.png
|   │   ├── Fig18_topExpr_heatmap.png
│   ├── gseapy_prerank_output_0/
|   │   ├── gene_sets.gmt
|   │   ├── gseapy.gene_set.prerank.report.csv
|   │   ├── prerank_data.rnk
│   ├── gseapy_prerank_output_1/
|   │   ├── gene_sets.gmt
|   │   ├── gseapy.gene_set.prerank.report.csv
|   │   ├── prerank_data.rnk
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

> **Note:** The dataset is copied automatically from the repository data/ folder.
> After running the Setup cells, data will be in the local colab environment
> *No manual download required.*

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

Open notebook: `GBM_snRNAseq_workflow.ipynb`

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

4. Dr. Sarangan (Ravi) Ravichandran and Dr. Randall Johnson from Hood College for their contributions in the form of knowledge gained through lectures, lecture notes and workbooks.

---

*BIFX-546 · Hood College · Spring 2026 · Thomas Walsh · Dr. Sarangan Ravichandran (Instructor)*
