# Towards Marketing Analytics: Customer Segmentation by Clustering

## Project Overview

This project applies unsupervised machine learning to customer segmentation using a Kaggle customer dataset containing 2,240 observations. It evaluates six clustering algorithms, applies Principal Component Analysis (PCA) for dimensionality reduction, and compares clustering performance to identify meaningful customer groups.

The study identifies **AGNES hierarchical clustering** as the preferred model, producing four main customer clusters. The results demonstrate how clustering can support marketing analytics, customer relationship management (CRM), customer profiling, and targeted marketing strategies.

## Abstract

<blockquote><small>
This study explores unsupervised learning techniques, notably, clustering algorithms in market segmentation—to enhance customer service delivery, guide targeted marketing initiatives, and optimize business resource utilization. Some related works are benchmarked to guide the selection of appropriate algorithms for the identified problem. The clustering techniques K-Means, K-Medoids, DBSCAN, AGNES hierarchical clustering, simple grid-based, and EM clustering were used to identify distinct market segments. Prior to building the models, data preprocessing was performed on the market segmentation data to handle possible data anomalies including outliers, skewness, and high correlation. PCA was used as a data reduction technique to retain twelve (12) components for onward analysis. Typically, clustering problems do not require data partitioning, however, 80% training dataset was used to build the six (6) models with cross validation of ten (10) iterations, and 20% test data to evaluate the best two (2) models. Using KMeans algorithm and performance metrics such as Within-Cluster Sum of Squares or Inertia, Silhouette Score, Caliński-Harabasz Index and Davies-Bouldin Index, eight (8) best initial clusters were predetermined. By constructing appropriate dendrograms using complete and Ward linkages, visual illustrations of the data's hierarchical structure—relationship, cohesion, and separation between the clusters—were analyzed. AGNES hierarchical model emerged as the best performing model—creating four (4) clusters. The study provides an understanding of these market segments building an integrated, trackable, and scalable solution. We finally propose the novel Market Segmentation Trees–MST algorithm (2023) for future work—to improve the accuracy of response behaviors of target customers.
</small></blockquote>

## Research Objectives

* Apply unsupervised machine learning to identify meaningful customer segments.
* Compare six clustering algorithms using established clustering evaluation metrics.
* Prepare customer data by addressing skewness, outliers, categorical variables, and high correlation.
* Apply PCA to reduce dimensionality while retaining important information.
* Evaluate the leading clustering models using training and test datasets.
* Identify a suitable clustering model to support marketing analysis and customer profiling.
* Explore Market Segmentation Trees (MST) as a potential direction for future research.

## Dataset

The study uses the **Customer Segmentation dataset** obtained from Kaggle.

The dataset contains 2,240 customer observations and 28 predictor variables, along with a `Response` label that was excluded from the unsupervised clustering analysis.

The data includes customer demographic characteristics, purchasing behavior, income-related information, and marketing campaign response attributes.

**Dataset source:** [Kaggle — Customer Segmentation](https://www.kaggle.com/datasets/vishakhdapat/customer-segmentation-clustering)

## Methodology

### 1. Exploratory Data Analysis and Preprocessing

The preprocessing stage involved:

* Examining dataset structure, variable types, and distributions.
* Analyzing categorical variables and class distributions.
* Investigating skewness, outliers, and correlations among numerical variables.
* Removing irrelevant and zero-variance variables.
* Excluding the `Response` label from the clustering inputs.
* Encoding categorical variables, including `Education` and `Marital_Status`.
* Applying Box-Cox transformations to address skewness.
* Applying interquartile range (IQR)-based processing to address outliers.
* Creating more meaningful features from `Year_Birth` and `Dt_Customer`.

The transformed features were prepared for dimensionality reduction and clustering.

### 2. Data Partitioning and Dimensionality Reduction

The dataset was divided into training and test subsets.

| Dataset   | Percentage |
| --------- | ---------: |
| Training  |        80% |
| Testing   |        20% |
| **Total** |   **100%** |

`StandardScaler` was used to scale the data. Scaling was fitted on the training data to avoid data leakage, with the fitted transformation applied to the test data.

Principal Component Analysis (PCA) was then used to reduce dimensionality and address high correlation among variables.

**Twelve principal components** were retained, explaining approximately 95% of the variance in the data.

### 3. Clustering Models

Six clustering algorithms were implemented and evaluated.

| No. | Algorithm                                | Approach                    |
| --: | ---------------------------------------- | --------------------------- |
|   1 | K-Means                                  | Partitioning                |
|   2 | K-Medoids                                | Partitioning                |
|   3 | DBSCAN                                   | Density-based               |
|   4 | AGNES                                    | Hierarchical, agglomerative |
|   5 | Simple Grid-Based Clustering             | Grid-based                  |
|   6 | Expectation-Maximization (EM) Clustering | Probabilistic/model-based   |

K-Means was initially used to investigate an appropriate number of clusters. Eight clusters were selected as the initial configuration for model development.

Hierarchical clustering was also investigated using Ward and Complete linkage methods to examine cluster relationships and structure through dendrograms.

Ten iterations were used to evaluate model performance on the training data.

### 4. Model Evaluation

The clustering algorithms were compared using the following metrics:

| Metric                                  | Description                                                                                 | Preferred Direction                       |
| --------------------------------------- | ------------------------------------------------------------------------------------------- | ----------------------------------------- |
| Silhouette Score                        | Measures cluster cohesion and separation.                                                   | Higher                                    |
| Calinski-Harabasz Index                 | Compares between-cluster dispersion with within-cluster dispersion.                         | Higher                                    |
| Davies-Bouldin Index                    | Measures cluster similarity based on within-cluster scatter and between-cluster separation. | Lower                                     |
| Inertia / Within-Cluster Sum of Squares | Measures within-cluster variation for K-Means.                                              | Lower, considered alongside cluster count |

The two leading models selected from the training evaluation were K-Means and AGNES hierarchical clustering. Both were subsequently evaluated using the test data.

## Training Results and Findings

The following table presents the reported average training results across the six clustering algorithms.

| Model             | Clustering Approach       | Silhouette Score | Calinski-Harabasz Index | Davies-Bouldin Index |
| ----------------- | ------------------------- | ---------------: | ----------------------: | -------------------: |
| K-Means           | Partitioning              |             0.20 |                  206.52 |                 1.73 |
| K-Medoids         | Partitioning              |             0.14 |                  232.01 |                 2.15 |
| DBSCAN            | Density-based             |             0.44 |                  144.51 |                 0.72 |
| AGNES             | Hierarchical              |             0.14 |                  156.67 |                 1.92 |
| Simple Grid-Based | Grid-based                |            -0.03 |                   25.54 |                 3.06 |
| EM Clustering     | Probabilistic/model-based |             0.15 |                  145.84 |                 2.09 |

### Key Findings

* **K-Means** achieved a Calinski-Harabasz Index of 206.52 and a Davies-Bouldin Index of 1.73.
* **K-Medoids** recorded the highest Calinski-Harabasz Index at 232.01.
* **DBSCAN** achieved the highest Silhouette Score of 0.44 and the lowest Davies-Bouldin Index of 0.72. However, its sensitivity to noise and difficulty producing stable, interpretable clusters limited its suitability for the study.
* **AGNES** was selected as the preferred model for further analysis based on the overall evaluation and hierarchical structure of the resulting clusters.
* **Simple Grid-Based Clustering** recorded the weakest overall results, including a Silhouette Score of -0.03.

These findings illustrate why selecting a clustering model requires considering multiple evaluation metrics, cluster interpretability, and model stability rather than relying on a single score.

## Test Evaluation and Recommended Model

The two leading training models—K-Means and AGNES—were evaluated on the test dataset.

The study reported that:

* K-Means showed signs of underfitting on the test data.
* AGNES demonstrated improved test performance compared with its training results.
* AGNES was selected as the final model for customer segmentation.

**The recommended model is AGNES hierarchical clustering.**

The final analysis identified **four main customer clusters** in the test dataset.

## Conclusion and Business Applications

This study compared six unsupervised machine learning algorithms for customer segmentation. The analysis incorporated data preprocessing, feature transformation, PCA-based dimensionality reduction, clustering evaluation, and test-set comparison.

AGNES hierarchical clustering was selected as the preferred model and produced four main customer clusters.

The resulting segments can support business activities such as:

* Customer profiling and behavioral analysis.
* Targeted marketing and campaign planning.
* Customer relationship management.
* Customer retention and engagement strategies.
* Marketing resource allocation.
* Data-driven product and service development.

### Future Research

The study proposes **Market Segmentation Trees (MST)** as a future research direction. MST combines market segmentation with response modeling and may provide a framework for analyzing customer response behavior and improving marketing decision-making.

## Repository Contents

The repository contains the research report, Python implementation, and supporting project materials.

| File or Directory            | Description                                                                   |
| ---------------------------- | ----------------------------------------------------------------------------- |
| `README.md`                  | Project overview, methodology, algorithms, results, and conclusions.          |
| `FPclustering-code(1).ipynb` | Jupyter Notebook containing the Python implementation and experiments.        |
| `docs/`                      | Research paper and supporting documentation.                                  |
| `results/`                   | Model evaluation results, charts, and visualizations, if included separately. |

## Technologies and Techniques

* **Programming Language:** Python
* **Environment:** Jupyter Notebook
* **Data Analysis:** Pandas and NumPy
* **Machine Learning:** Scikit-learn and clustering algorithms
* **Data Preprocessing:** Feature encoding, Box-Cox transformation, IQR-based outlier processing, and StandardScaler
* **Dimensionality Reduction:** Principal Component Analysis (PCA)
* **Clustering:** K-Means, K-Medoids, DBSCAN, AGNES, Simple Grid-Based Clustering, and EM Clustering
* **Model Evaluation:** Silhouette Score, Calinski-Harabasz Index, Davies-Bouldin Index, and K-Means inertia
* **Visualization:** Histograms, boxplots, correlation matrices, scree plots, and dendrograms

## Authors

* **Samuel Darteh** | LinkedIn: (https://linkedin.com/in/sdartehpro)
* Mohammed Sahidu Bah
* Yaw Opoku Debrah

**Affiliation:** [Michigan Technological University](https://mtu.edu)

## Research Paper

The complete research paper as was presented [Michigan Technological University](https://mtu.edu) is included in this repository. <br>
**Research Title:** Towards Marketing Analytics: Customer Segmentation by Clustering (2024)


## Disclaimer

The notebook and paper are provided as documented in the original work. The project is presented for academic, research, and professional portfolio purposes. The findings demonstrate the application of unsupervised machine learning to customer segmentation. The identified clusters should be interpreted in the context of the dataset and validated against business objectives before being used to guide real-world marketing decisions.



