# Customer Personality Analysis — Data Mining Project

A data mining project analyzing customer behavior and value using clustering, feature selection with a Genetic Algorithm, and a Fuzzy Logic inference system. This was a **team project completed by a group of 7**, covering the full pipeline from raw data to a working customer-segmentation system.

## 1. Introduction

**Dataset:** Customer Personality Analysis (Marketing Campaign Dataset)
**Source:** [Kaggle](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis)

The dataset contains 2,240 customer records describing personal characteristics (age, education, marital status), financial attributes (income), behavioral attributes (spending across product categories, purchase channels), and marketing campaign responses.

**Objective:** Analyze customer data and apply data mining techniques — clustering, a genetic algorithm for feature selection, and fuzzy logic for customer valuation — to extract insights and support marketing decision-making.

**Domain:** Marketing analytics. Understanding customer behavior helps businesses identify segments, improve targeting, and increase campaign effectiveness.

## 2. Methodology / Pipeline

The project follows an end-to-end pipeline:

1. **Exploratory Data Analysis (EDA)** — distribution, correlation, and categorical breakdown visualizations (age, education, income vs. spending, marital status, campaign response).
2. **Data Preprocessing** — handling missing values (median imputation for income), duplicate checks, datatype conversion, outlier removal (IQR method), feature engineering (Total Spending, Children, Is_Parent, Customer Tenure), categorical encoding (label encoding for Education, one-hot encoding for Marital Status), standardization (Z-score scaling), and dimensionality reduction (PCA, retaining ~90% variance).
3. **Feature Selection (Genetic Algorithm)** — evolved an optimal feature subset over 30 generations using tournament selection, single-point crossover, and mutation, evaluated via Silhouette Score. Selected features: `NumWebPurchases`, `Total_Spending`, `Is_Parent`.
4. **Clustering**
   - **K-Medoids** on the GA-selected features (best K=3 via Silhouette/Elbow analysis).
   - **Hierarchical Clustering** (Single/Complete/Average linkage, with dendrograms) as a comparison method, best configuration: Average linkage, K=3.
5. **Fuzzy Logic Inference System** — classifies customers into value tiers (Standard/Silver, Preferred/Gold, VIP/Platinum) using fuzzy membership functions over Income, Spending, and Cluster, with a 27-rule base and centroid defuzzification.
6. **System Implementation** — combines all steps into a single pipeline that takes a new customer's raw data and outputs a cluster assignment and value segment.

## 3. Key Results

- **Genetic Algorithm:** Improved clustering Silhouette Score by ~28% over the baseline, converging on 3 highly relevant features out of the original set.
- **K-Medoids Clustering (K=3):** Silhouette Score of 0.53, identifying segments such as *Big Spenders*, *Budget-Conscious Families*, and *Active/Web Shoppers*.
- **Hierarchical Clustering (K=3, Average linkage):** Silhouette Score of 0.44, producing comparable segment profiles.
- **Fuzzy Logic Segmentation:** Classified customers into Standard (Silver), Preferred (Gold), and VIP (Platinum) tiers based on income, spending, and cluster membership.

## 4. Business Insights

- **VIP customers** (high income/spending) should be prioritized for retention and loyalty programs.
- **Preferred customers** represent strong growth potential through targeted upsell campaigns.
- **Standard customers** need low-cost, broad engagement strategies (discounts, coupons).
- Customers with high web-purchase activity are strong candidates for digital marketing channels.

## 5. Repository Contents

```
├── customer_personality_analysis.ipynb   # Main notebook (EDA, preprocessing, GA, clustering, fuzzy system)
├── marketing_campaign.csv                # Raw dataset (from Kaggle)
├── Flowchart.drawio.png                  # Project pipeline flowchart
└── README.md
```

## 6. Tech Stack

Python · pandas · NumPy · scikit-learn · scikit-learn-extra (K-Medoids) · scikit-fuzzy · SciPy (hierarchical clustering) · Matplotlib · Seaborn

## 7. How to Run

1. Install dependencies: `pip install numpy scikit-learn scikit-learn-extra scikit-fuzzy pandas matplotlib seaborn`
2. Open `customer_personality_analysis.ipynb` in Jupyter/Colab
3. Upload `marketing_campaign.csv` when prompted, then run all cells in order

## 8. Team

This project was developed collaboratively by a team of 7 as part of a Data Mining course:

* [Maii Walid](https://github.com/maii818)
* [Hamsa Ehab](https://github.com/hamsa77788)
* [Hla Essam](https://github.com/hlaessam504)
* [Nourhan Essam](https://github.com/nourhanessam4)
* [Menna Emad](https://github.com/menna0602)
* [Malak Ashraf](https://github.com/MalakAshrafRezk)
* [Farah Ibrahim](https://github.com/Farah-Ibrahim1405)

## Skills Demonstrated

Exploratory Data Analysis · Data Preprocessing & Feature Engineering · PCA · Genetic Algorithms (Feature Selection) · K-Medoids & Hierarchical Clustering · Fuzzy Logic Inference Systems · Customer Segmentation
