# Age-Dependent Transcriptional and Cellular Features of the Glioblastoma Microenvironment Revealed by Single-Nucleus RNA Sequencing

*Thomas J. Walsh | March 18, 2026*
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
| Further Analysis | Gene Set Enrichment Analysis (GSEA) |

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
|   │   ├── Fig14_ClusterLabels.png
|   │   ├── Fig15_Young_topGenes.png
|   │   ├── Fig16_Old_topGenes.png
|   │   ├── Fig17_Cluster_Proportions.png
|   │   ├── Fig18_Expr_dotplot.png
|   │   ├── Fig19_topExpr_violins.png
|   │   ├── Fig20_topExpr_heatmap.png
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
├── references.bib                         # BibTex file with References
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
| Figure 14 | `results/figures/Fig14_ClusterLabels.png` | Leiden Clusters Labeled by the top DE Gene for each Cluster (UMAP) |
| Figure 17 | `results/figures/Fig17_Cluster_Proportions.png` | Cell-Type proportions of each Leiden cluster (Box Plot) |
| Figure 18 | `results/figures/Fig18_Expr_dotplot.png` | Cellular Fractions and Expression of Top Genes for Each group (Dot Plot) |
| Ranked List | `results/gseapy_prerank_output_0/gseapy.gene_set.prerank.report.csv` | Gene Set Enrichment Analysis (GSEA) for Young Cohort (List) |
| Ranked List | `results/gseapy_prerank_output_1/gseapy.gene_set.prerank.report.csv` | Gene Set Enrichment Analysis (GSEA) for Old Cohort (List) |

---

## Conclusion: Unraveling Age-Dependent Divergence in Glioblastoma Microenvironments

This comprehensive single-cell RNA-seq analysis successfully investigated the age-dependent divergence within the glioblastoma tumor microenvironment (TME) in young versus aged mice. By processing and comparing data from two distinct cohorts, we leveraged a multi-faceted approach to identify key molecular and cellular distinctions.

Our workflow began with meticulous data preparation, including normalization, log-transformation, and quality control, ensuring robust downstream analysis. Dimensionality reduction techniques like PCA and UMAP effectively visualized the inherent cellular heterogeneity within each age group. Differential Gene Expression (DGE) analysis between the young and old cohorts highlighted numerous genes with significantly altered expression, offering direct molecular indicators of age-related changes. While Gene Set Enrichment Analysis (GSEA) explored enriched biological pathways, the lack of statistically significant findings after FDR correction suggests the need for further investigation into specific cellular contexts or alternative gene set databases.

Crucially, the application of a Random Forest Classifier provided a data-driven approach to pinpoint the most influential genes contributing to the TME's divergence. Achieving an accuracy of approximately 81.59% in distinguishing between young and old cells, the model identified a panel of top 20 genes (e.g., Hbb-bs, AC149090.1, Cd74, Ccl5, Avp) whose expression patterns are most predictive of the age phenotype. These genes represent compelling candidates for further functional validation, potentially serving as novel biomarkers or therapeutic targets in age-associated glioblastoma.

In essence, this report not only delineates the transcriptional landscape differences but also provides a prioritized list of genes that fundamentally distinguish the glioblastoma microenvironment in aged hosts. This knowledge is invaluable for understanding the mechanisms underlying age-related tumor progression and for developing age-appropriate therapeutic strategies.

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

1. Fang, Z., Liu, X., & Peltz, G. (2023). GSEApy: A comprehensive package for performing gene set enrichment analysis in Python. Bioinformatics, 39(1), btac757. https://doi.org/10.1093/bioinformatics/btac757

2. Glioblastoma—Symptoms and causes. (n.d.). Mayo Clinic. Retrieved May 7, 2026, from https://www.mayoclinic.org/diseases-conditions/glioblastoma/symptoms-causes/syc-20569077

4. Harris, C. R., Millman, K. J., Van Der Walt, S. J., Gommers, R., Virtanen, P., Cournapeau, D., Wieser, E., Taylor, J., Berg, S., Smith, N. J., Kern, R., Picus, M., Hoyer, S., Van Kerkwijk, M. H., Brett, M., Haldane, A., Del Río, J. F., Wiebe, M., Peterson, P., … Oliphant, T. E. (2020). Array programming with NumPy. Nature, 585(7825), 357–362. https://doi.org/10.1038/s41586-020-2649-2

3. Hicks, S. (n.d.). Single cell RNA sequencing – NGS Analysis [Single cell RNA sequencing]. NGS Analysis. Retrieved May 7, 2026, from https://learn.gencore.bio.nyu.edu/single-cell-rnaseq/

4. Hoogstrate, Y., Draaisma, K., Ghisai, S. A., Van Hijfte, L., Barin, N., De Heer, I., Coppieters, W., Van Den Bosch, T. P. P., Bolleboom, A., Gao, Z., Vincent, A. J. P. E., Karim, L., Deckers, M., Taphoorn, M. J. B., Kerkhof, M., Weyerbrock, A., Sanson, M., Hoeben, A., Lukacova, S., … French, P. J. (2023). Transcriptome analysis reveals tumor microenvironment changes in glioblastoma. Cancer Cell, 41(4), 678-692.e7. https://doi.org/10.1016/j.ccell.2023.02.019

5. Hunter, J. D. (2007). Matplotlib: A 2D Graphics Environment. Computing in Science & Engineering, 9(3), 90–95. https://doi.org/10.1109/MCSE.2007.55
Kramer, O. (2016). Scikit-Learn. In O. Kramer, Machine Learning for Evolution Strategies (Vol. 20, pp. 45–53). Springer International Publishing. https://doi.org/10.1007/978-3-319-33383-0_5

6. The pandas development team. (2026). pandas-dev/pandas: Pandas (Version v3.0.2) [Computer software]. Zenodo. https://doi.org/10.5281/ZENODO.3509134
Venkatachalam, Pooja, & Albert. (2025, June 15). Longevity-db/mouse-glioblastoma-snRNAseq · Datasets at Hugging Face [Hugging Face Repository]. Mouse Glioblastoma Atlas (snRNA-Seq) Dataset. https://huggingface.co/datasets/longevity-db/mouse-glioblastoma-snRNAseq

7. Wolf, F. A., Angerer, P., & Theis, F. J. (2018). SCANPY: Large-scale single-cell gene expression data analysis. Genome Biology, 19(1), 15. https://doi.org/10.1186/s13059-017-1382-0

8. Zhai, L., Castro, B., Zhao, J., Lauking, K., Bell, A., Miska, J., & Wainwright, D. (2024, January 1). Single Cell RNA Sequencing of Young and Aged Murine Glioblastoma [Accession Display]. NCBI. Series GSE215239. https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE215239

9. Dr. Sarangan (Ravi) Ravichandran and Dr. Randall Johnson from Hood College for their contributions in the form of knowledge gained through lectures, lecture notes and workbooks.

---

*BIFX-546 · Hood College · Spring 2026 · Thomas J. Walsh · Dr. Sarangan Ravichandran (Instructor)*
