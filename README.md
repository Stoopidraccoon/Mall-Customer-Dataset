# Mall Customers Segmentation (Clustering Project)

**Project Overview**

This project performs customer segmentation on the Mall Customers dataset using K-Means clustering.
The goal is to group customers into distinct clusters based on annual income, spending score, age, and gender, helping businesses understand customer behavior and tailor marketing strategies.

**Dataset**

Source: Mall Customers Dataset (CSV)

Rows: 200

Columns:

CustomerID → Unique ID for each customer

Gender → Male/Female

Age → Age of the customer

Annual Income (k$) → Income in thousand dollars

Spending Score (1-100) → Score assigned based on spending behavior

**Dataset Description**

- Customers have varying incomes and spending scores.

- Some groups naturally cluster into high income–high spenders, low income–low spenders, and average customers.

- Clustering provides actionable insights for personalized marketing campaigns.

**Results**

Optimal Clusters: 5 (based on silhouette analysis)

Silhouette Score: ~0.55 (moderate but acceptable for real-world overlapping data)

Cluster Insights:

Cluster 1: High Income – High Spenders

Cluster 2: Low Income – Low Spenders

Cluster 3: Young Average Spenders

Cluster 4: Older High Income – Low Spenders

Cluster 5: Middle Income – Moderate Spenders

**Dashboard (Power BI)**

To make results interactive, a Power BI dashboard was created:

KPIs: Total Customers, Avg Income, Avg Spending

Cluster-wise Analysis:

Customers per cluster

Avg Income per cluster

Avg Spending per cluster

Slicer: Filter results by cluster, Gender, Age Group

DAX Measures used
Age Group = 
SWITCH(
    TRUE(),
    'Mall_Customers'[Age] < 25, "<25",
    'Mall_Customers'[Age] < 35, "25-34",
    'Mall_Customers'[Age] < 50, "35-49",
    "50+"
)

CustomersInCluster =
CALCULATE(
    COUNT('Mall_Customers'[CustomerID]),
    'Mall_Customers'[Cluster] = SELECTEDVALUE('Mall_Customers'[Cluster])
)

**Power BI**

Import mall_customers_clustered.csv

Add measures (DAX)

Build dashboard

**Justification for Silhouette Score (0.55)**

Real-world data often overlaps → perfect separation isn’t realistic.

0.55 indicates moderately well-separated clusters, which are still actionable.

Industry benchmarks for this dataset typically range 0.50–0.60.
