1# 🎯 Customer Segmentation Using RFM Analysis and K-Means Clustering

## 📊 Project Overview

This project builds a data-driven customer segmentation framework by combining **RFM (Recency, Frequency, Monetary) analysis** with **K-Means clustering** to uncover behavioral customer groups from retail transaction data, and translates each segment into actionable business recommendations.

Unlike a purely rule-based RFM approach, this project lets the data determine the segment structure statistically — using formal cluster validation techniques rather than fixed quantile thresholds — while still grounding the final model choice in business interpretability.

---

## 🔑 Key Insights

- Statistical validation (Elbow, Silhouette, Calinski-Harabasz) pointed to **K = 2** as the strongest solution by pure clustering metrics, but **K = 4** was deliberately selected instead, based on a quantified tradeoff analysis showing it preserves most of the clustering quality (WCSS increases only ~32%) while revealing far more actionable behavioral distinctions.
- Four distinct customer segments emerged: **High Value/Loyal**, **At-Risk High-Value**, **Potential Loyal**, and **Low Value/At-Risk** — each with a clear, differentiated business strategy.
- **At-Risk High-Value customers** represent one of the most strategically important segments: historically strong spenders showing signs of declining recent engagement, prioritized for retention efforts.
- The first two Principal Components explain **86%+ of the variance** in the transformed RFM feature space, confirming that a low-dimensional structure meaningfully separates the segments.

---

## ⚙️ Methodology

1. **Data Preparation** — Filtered to U.S. transactions, computed Recency, Frequency, and Monetary features per customer, with full data quality checks.
2. **Statistical Analysis of RFM** — Distribution analysis, skewness, and correlation structure (Kendall's τ) across R, F, and M.
3. **Feature Transformation** — Yeo-Johnson power transformation to correct skew, followed by standardization.
4. **K Selection** — Elbow Method (WCSS + automated `KneeLocator` detection), Silhouette Score, and Calinski-Harabasz Index evaluated jointly across K = 2–9.
5. **Model Comparison** — K = 2 vs. K = 4 solutions compared side-by-side on cluster profiles, with a quantified statistical tradeoff analysis justifying the final business-driven choice.
6. **Segment Profiling** — Descriptive segment naming, distribution analysis, heatmaps, boxplots, and PCA-based visualization of the final clusters.
7. **Business Recommendations** — Segment-specific strategies (retention, upsell, reactivation, loyalty).
8. **Annex** — Comparative analysis between this K-Means solution and a rule-based RFM segmentation approach.

---

## 📈 Visualizations

The notebook includes:
- RFM distribution histograms and boxplots (before/after transformation)
- Correlation heatmap (Kendall's τ) across R, F, M
  
- Elbow / Silhouette / Calinski-Harabasz curves across candidate K values
https://github.com/Starmos86/KMeans-RFM-customer-Segmentation/blob/main/Images/Elbow%20%26%20others.png

- Segment distribution and RFM heatmap by cluster
  https://github.com/Starmos86/KMeans-RFM-customer-Segmentation/blob/main/Images/Average%20RFM%20%20by%20Segment.png
  
- Boxplots comparing RFM values across the four segments
  https://github.com/Starmos86/KMeans-RFM-customer-Segmentation/blob/main/Images/RFM%20by%20Cluster%20Boxplots.png
  
- 2D PCA scatter plot of customer segments
https://github.com/Starmos86/KMeans-RFM-customer-Segmentation/blob/main/Images/PCA.png
---

## 📦 Dataset Information

- **Dataset:** Superstore retail dataset
- **Records:** ~10,000 transactions, 793 unique U.S. customers after filtering
- **Time period:** January 2021 – December 2024

---

## 🛠️ Technologies Used

- Python
- Pandas, NumPy
- scikit-learn (`KMeans`, `PowerTransformer`, `StandardScaler`, `PCA`, `silhouette_score`, `calinski_harabasz_score`)
- `kneed` (automated elbow detection)
- Matplotlib, Seaborn
- Jupyter Notebook

---

## 📁 Repository Structure

```bash
├── Kmeans Clustering Segmentation.ipynb   # Main analysis notebook
├── data/                              # Dataset files
├── images/                            # Exported visualizations
└── README.md
```

---

## 🔗 Related Project

This project is part of a broader customer segmentation analysis using the same dataset. The companion project, [Rule-Based RFM Customer Segmentation](https://github.com/Starmos86/Rule-Based-RFM-Customer-Segmentation/blob/main/Rule-based%20RFM%20Customer%20Segmentation.ipynb), explores a traditional quantile-based RFM segmentation framework, providing a comparative perspective against this machine learning–based K-Means clustering approach.

---

## Conclusion

This project demonstrates a complete, statistically rigorous approach to customer segmentation — from raw transaction data through validated cluster selection to business-ready, quantified recommendations — while transparently documenting the tradeoffs behind every modeling decision along the way.
