# Credit Card Customer Segmentation
### ARTI308 – Machine Learning | K-Means Clustering Project

---

## Overview

This project applies **K-Means clustering** to segment credit card customers based on their usage behavior. Since the dataset has no predefined labels, this is an **unsupervised learning** problem — the goal is to let the algorithm discover natural groupings in the data.

The insights from this segmentation can help a company understand different customer types and design better, more targeted marketing strategies.

---

## Dataset

**Source:** [Kaggle – Credit Card Dataset for Clustering](https://www.kaggle.com/datasets/arjunbhasin2013/ccdata/data)

**File:** `CC_GENERAL.csv`

- 8,950 customers
- 18 features describing credit card usage behavior
- Features include: `BALANCE`, `PURCHASES`, `CASH_ADVANCE`, `CREDIT_LIMIT`, `PAYMENTS`, `TENURE`, and various frequency/transaction columns

---

## Project Steps

1. **Data Loading & Exploration** – shape, info, describe, head
2. **Data Cleaning** – dropped `CUST_ID`, filled missing values (`CREDIT_LIMIT`, `MINIMUM_PAYMENTS`) with column means
3. **Exploratory Data Analysis** – histograms, correlation heatmap, scatter plots
4. **Feature Scaling** – StandardScaler (required for distance-based algorithms)
5. **Choosing K** – Elbow method + Silhouette score for K = 1 to 10
6. **Final Model** – K-Means with K=3, `random_state=42`, `n_init=10`
7. **Cluster Analysis** – groupby summary, cluster sizes
8. **Visualization** – PCA reduced to 2D for cluster plotting

---

## Results

**Optimal K = 3** based on:
- Highest silhouette score at K=3 (0.2506)
- Visible elbow in the inertia curve at K=3

### Customer Segments

| Cluster | Label | Size | Key Characteristics |
|---------|-------|------|---------------------|
| 0 | Cash Advance Users | 1,596 | High balance ($3,989), very high cash advance ($3,869, ~12 transactions), low purchases, almost never pays in full (3%) |
| 1 | Active High Spenders | 1,235 | Highest purchases ($4,268, ~56 transactions), highest credit limit ($7,734), pays in full 30% of the time |
| 2 | Dormant / Low Activity | 6,119 | Low balance ($799), low purchases ($505), low cash advance, lowest credit limit ($3,269) |

### Marketing Strategy

- **Cluster 0 (Cash Advance Users):** Offer debt consolidation products and lower-interest installment plans
- **Cluster 1 (High Spenders):** Reward with loyalty programs, cashback, travel benefits, or premium card upgrades
- **Cluster 2 (Dormant):** Re-engagement campaigns with personalized incentives to encourage card usage

---

## Libraries Used

```
pandas
numpy
matplotlib
seaborn
scikit-learn (StandardScaler, KMeans, silhouette_score, PCA)
```

---

## How to Run

1. Clone the repository
2. Make sure `CC_GENERAL.csv` is in the same folder as the notebook
3. Open `02-Credit_Card_Customer_Segmentation_Completed.ipynb` in Jupyter Notebook or JupyterLab
4. Run all cells from top to bottom (`Kernel > Restart & Run All`)
