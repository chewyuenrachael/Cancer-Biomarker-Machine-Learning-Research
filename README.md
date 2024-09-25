# Breast Cancer Biomarker Research

## Overview

This project explores the prognostic capabilities of molecular biomarkers in breast cancer patients. By applying various clustering algorithms and survival analysis techniques to molecular expression profiles, we aim to understand how these biomarkers influence patient survival outcomes.

## Objectives

- **Clustering Patients**: Categorize patients based on molecular expression profiles using different clustering algorithms.
- **Biomarker Analysis**: Investigate the relationships between selected genes and their impact on survival.
- **Survival Analysis**: Perform Kaplan-Meier and Cox proportional hazards analyses to assess the prognostic significance of clusters.

## Dataset

The study utilizes data from breast cancer patients, including:

- **Molecular Data**: Expression levels of selected genes.
- **Clinical Data**: Survival times (`OS_MONTHS`) and status (`OS_STATUS`).

## Selected Biomarkers

The following genes were selected for analysis due to their relevance in breast cancer research:

- `BAG1`, `BCL2`, `BIRC5`, `CCNB1`, `CCND1`, `CD68`, `GSTM1`, `MYBL2`, `ERBB2`, `MKI67`, `MMP11`, `MYC`, `PGR`, `UBE2C`, `EGFR`, `GRB7`, `PNMA2`, `HOXB13`, `VGLL1`

## Methodology

### 1. Exploratory Data Analysis (EDA)

- **Statistical Summary**: Computed basic statistics for molecular and clinical data.
- **Distribution Analysis**: Plotted histograms for gene expression levels to understand their distributions.
- **Correlation Heatmap**: Identified highly correlated genes to understand potential co-regulation.
- **Survival Time Distribution**: Analyzed the distribution of patient survival times.
- **Boxplots**: Visualized gene expression levels stratified by survival status.

### 2. Clustering Algorithms

#### a. K-Means Clustering

- **Procedure**:
  - Scaled data using `StandardScaler`.
  - Determined the optimal number of clusters (`k`) using the Elbow method.
  - Applied K-Means clustering with `k=3` and `k=4`.
- **Analysis**:
  - Evaluated cluster assignments using Kaplan-Meier survival curves.
  - Performed Cox proportional hazards regression to assess the impact of clusters on survival.

#### b. One-Class Support Vector Machine (OneSVM)

- **Procedure**:
  - Scaled data and reduced dimensionality using PCA.
  - Applied One-Class SVM for anomaly detection.
- **Analysis**:
  - Visualized clusters in reduced dimensional space.
  - Conducted survival analysis using Kaplan-Meier curves and Cox regression.

#### c. Spectral Clustering

- **Procedure**:
  - Scaled data and applied PCA for dimensionality reduction.
  - Applied Spectral Clustering with varying cluster numbers (`n=2`, `n=3`, `n=4`).
- **Analysis**:
  - Visualized clusters in PCA-reduced space.
  - Evaluated survival differences among clusters using Kaplan-Meier curves and log-rank tests.
  - Performed Cox regression to assess the prognostic significance of clusters.

## Results

### Correlation Analysis

Identified highly correlated gene pairs:

- **MYBL2 & UBE2C**: Strong positive correlation (0.899).
- **BIRC5 & UBE2C**: Strong positive correlation (0.889).
- **ERBB2 & GRB7**: Notable correlation (0.844), suggesting potential co-amplification.

### Clustering Outcomes

- **K-Means Clustering**:
  - Clusters did not show significant differences in survival outcomes.
  - Cox regression did not yield statistically significant hazard ratios for clusters.

- **One-Class SVM Clustering**:
  - Survival curves showed visual separation but were not statistically significant.
  - Log-rank test p-value was above 0.05, indicating no significant survival differences.

- **Spectral Clustering**:
  - Increasing the number of clusters did not improve the significance of survival differences.
  - Cox regression showed non-significant coefficients for clusters.

### Survival Analysis

- **Kaplan-Meier Curves**:
  - Visual separation between clusters was observed but lacked statistical significance.
  - Median survival times varied among clusters but did not correlate with statistical significance.

- **Cox Proportional Hazards Model**:
  - Clusters from all algorithms did not significantly predict survival outcomes.
  - Concordance indices were around 0.54, indicating weak predictive power.

## Conclusions

- The clustering algorithms applied did not produce clusters that significantly predict survival outcomes.
- The selected molecular biomarkers, in isolation, may not be sufficient to stratify patients based on prognosis.
- Further research is needed to identify more robust biomarkers or incorporate additional data.

## Future Work

1. **Incorporate Additional Covariates**: Include more clinical variables or molecular data to enhance model accuracy.
2. **Alternative Models**: Explore advanced survival models like machine learning-based approaches.
3. **Functional Analysis**: Conduct pathway or gene set enrichment analyses to understand biological significance.
4. **Clustering Validation**: Use internal validation metrics and external datasets for cluster validation.

## Dependencies

- **Python Libraries**:
  - Data Manipulation: `pandas`, `numpy`
  - Visualization: `matplotlib`, `seaborn`
  - Machine Learning: `scikit-learn`
  - Survival Analysis: `lifelines`
  - Miscellaneous: `warnings`

## How to Run the Project

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/yourusername/breast-cancer-biomarker-research.git
   ```

2. **Install Dependencies**:

   ```bash
   pip install -r requirements.txt
   ```

3. **Prepare the Data**:

   - Place the molecular and clinical data files in the `data/` directory.
   - Update file paths in the scripts if necessary.

4. **Run the Analysis**:

   - Execute the Jupyter notebooks or Python scripts in the `scripts/` directory in the following order:
     1. Data Loading and EDA
     2. Clustering Algorithms
     3. Survival Analysis

## Repository Structure

- `data/`: Contains the dataset files.
- `scripts/`: Python scripts and notebooks for analysis.
- `results/`: Generated figures, models, and output files.
- `README.md`: Project overview and instructions.

## Acknowledgements

Thank you to the most inspiring team I had the chance to work with. Matias and Genaro were the best mentors I could have asked for.

- **Institution**: Multiomix Team, Buenos Aires, Argentina
- **Lead Researcher**: Matias Butti, Genaro Camele
