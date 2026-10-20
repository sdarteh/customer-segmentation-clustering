# Towards Marketing Analytics: Customer Segmentation by Clustering

**Research Project | Machine Learning | Unsupervised Learning | Customer Analytics**

## Overview

This repository presents our 2024 research on customer segmentation using unsupervised machine learning techniques.

The study investigates clustering algorithms for identifying meaningful customer groups to support targeted marketing initiatives, customer relationship management (CRM), customer service delivery, and business resource allocation.

The research compares six clustering approaches and evaluates their performance using established clustering metrics.

## Research Objectives

* Explore customer data to identify meaningful market segments.
* Apply data preprocessing and dimensionality reduction techniques.
* Compare multiple clustering algorithms using quantitative evaluation metrics.
* Identify a suitable clustering model for customer segmentation.
* Establish a foundation for future research into customer response prediction.

## Methodology

The research includes the following stages:

1. **Exploratory Data Analysis:** Examine the distribution, characteristics, and relationships of customer variables.
2. **Data Preprocessing:** Address missing values, skewness, outliers, categorical variables, and correlated features.
3. **Feature Engineering:** Derive customer age and customer relationship longevity from existing variables.
4. **Dimensionality Reduction:** Apply Principal Component Analysis (PCA), retaining 12 components for subsequent analysis.
5. **Model Development:** Implement and compare six clustering approaches.
6. **Model Evaluation:** Assess clustering performance using Silhouette Score, Calinski–Harabasz Index, and Davies–Bouldin Index.
7. **Final Model Selection:** Evaluate the leading candidate models on the test dataset.

## Algorithms Evaluated

The study investigates the following clustering techniques:

* K-Means
* K-Medoids
* DBSCAN
* AGNES (Agglomerative Hierarchical Clustering)
* Simple Grid-Based Clustering
* Expectation-Maximization (EM) Clustering

## Dataset

The research uses a customer segmentation dataset obtained from Kaggle.

The paper describes a dataset containing 2,240 customer records, 28 predictors, and a response label that was excluded from the unsupervised learning analysis.

Dataset source: [Customer Segmentation Clustering — Kaggle](https://www.kaggle.com/datasets/vishakhdapat/customer-segmentation-clustering)

## Evaluation Metrics

The clustering algorithms were compared using:

* **Silhouette Score:** Evaluates cluster cohesion and separation.
* **Calinski–Harabasz Index:** Assesses the relationship between between-cluster and within-cluster dispersion.
* **Davies–Bouldin Index:** Evaluates cluster compactness and separation.
* **Within-Cluster Sum of Squares (Inertia):** Used with K-Means to investigate the appropriate number of clusters.

## Key Findings

The research identifies AGNES hierarchical clustering as the final selected model.

The test-data analysis resulted in four principal customer clusters, providing a basis for further investigation of customer characteristics and marketing strategies.

The study also highlights the importance of comparing clustering algorithms using multiple evaluation metrics rather than relying on a single measure.

## Repository Contents

| File                                              | Description                                                                                  |
| ------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `FPclustering-code.ipynb`                      | Original Python Jupyter Notebook containing the research implementation and recorded outputs |
| `project_paper_customerseg_by_clustering2024.pdf` | Original research paper documenting the methodology, experiments, findings, and conclusions  |

## Future Research

The original paper proposes Market Segmentation Trees (MST) as a direction for future work.

This approach could extend the research toward integrating customer segmentation with response modeling, enabling further investigation of customer behavior and marketing response prediction.

Additional experiments, methodological improvements, and model extensions are outside the scope of the current published research artifacts and are reserved for future work.

## Authors

* [**Samuel Darteh**](https://linkedin.com/in/sdartehpro)
* Mohammed Sahidu Bah
* Yaw Opoku Debrah

**Affiliation:** [Michigan Technological University](https://mtu.edu)

## Research Paper

The complete research paper is included in this repository.

**Publication year:** 2024

**Research title:** Towards Marketing Analytics: Customer Segmentation by Clustering

---

*This repository presents the original research artifacts. The notebook and paper are provided as documented in the original work; no additional experiments or post-publication corrections are represented here.*

