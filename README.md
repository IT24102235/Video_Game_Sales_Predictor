# 🎮 Video Game Sales Predictor

> **Predict video game sales from platform, genre, release info, scores, and more — with a clean, reproducible ML pipeline.**  
> Built collaboratively with **GitHub** and **Jupyter**.

---

## 📌 Proposal Insights
Our proposal established the **video game sales prediction problem** as highly relevant to the **gaming industry**, which relies on accurate forecasts for:
- **Publishers** → budget allocation and release planning.  
- **Retailers** → inventory management.  
- **Developers** → aligning design with demand.  
- **Investors** → identifying profitable titles.  

The chosen **VGChartz 2024 dataset** provides modern relevance with 64k+ rows, while alternative historical datasets (2016 & vgsales) allow comparative analysis and robustness checks.

---

## ✨ Progress Review I (Data Preprocessing & EDA)

### ✅ Work Completed
For **Progress Review I**, we focused on **data cleaning, preprocessing, and EDA visualizations**. All steps are stored in `data/cleaned/` and `notebooks/1. Data Preprocessing/`.

**1. Data Cleaning & Missing Values**  
- Removed duplicates and inconsistent rows.
- Handled missing values: numeric (median), categorical (mode/“Unknown”).
- Standardized column names across datasets.
- Drop unwanted columns

**2. Encoding & Outlier Removal**  
- **One-Hot Encoding** applied to categorical variables (Publisher, Developer, Genre, Platform).
- **Frequency Encoding** applied to categorical variables (Genre, Platform, Publisher, Developer).
- Outlier inspection via boxplots → retained true blockbuster outliers, removed invalid sales entries.

**3. Scaling & Normalization**  
- Standardization for numerical features (Critic Score, User Score, Sales).
- Min-Max scaling tested for algorithms sensitive to ranges.

**4. Feature Engineering**  
- Created `Total_Regional_Sales` (NA+EU+JP+Other).
- Derived `is Recent` and `Decade` features.

**5. Feature Selection**  
- Used correlation analysis, Chi-Square tests, and RFE to reduce redundant features.
- Identified Platform, Year, and Critic Score as most important.

**6. Dimensionality Reduction**  
- Applied SVD on One-Hot encoded dataset (reduced from ~130 features to ~113 while keeping ~90% variance).

**7. Exploratory Data Analysis (EDA)**  
- Histograms of Global Sales → highly skewed (few blockbuster titles dominate).
- Boxplots by Genre → Action & Sports genres sell highest.
- Correlation heatmap → Critic Score correlates more strongly with sales than User Score.
- Sales trends → peak sales between 2008–2010.

**8. Integrated Pipeline**  
- **Pipeline A (One-Hot + Scaling + SVD)**
- **Pipeline B (Frequency Encoding + Scaling)**

Both pipelines are modular and ready for model training in Progress Review II.

---

## 👥 Team Contributions (Progress Review I)
- **Senuja ( IT24102235 )** → Data Cleaning & Handling Missing Values  
- **Nimesh ( IT24102602 )** → Encoding & Outlier Removal  
- **Okindu ( IT24102827 )** → Scaling & Normalization  
- **Supuni ( IT24102564 )** → Feature Engineering  
- **Imalka ( IT24102531 )** → Feature Selection  
- **Moulana ( IT24102924 )** → Dimensionality Reduction  

Each member contributed one preprocessing technique with justification, implementation, and at least one visualization, integrated into the final pipeline.

---

## 🗂️ Project Structure (Updated for Review I)
```
video-game-sales/
├─ data/ 
│  ├─ raw/                                           # Original CSVs
│  └─ external/                                      # Step-by-step cleaned datasets
│      ├─ 1. Cleaning & Missing Values
│      ├─ 2. Encoding
│      ├─ 3. Scaling
│      ├─ 4. Feature Engineering
│      ├─ 5. Feature Selection
│      └─ 6. Dimensionality Reduction
│  
├─ notebooks/
|      ├─  1. Data Preprocessing/                    # All step-by-step data preprocessing parts
│      │    ├─ 1. Cleaning & Missing Values/
│      │    ├─ 2. Encoding/
│      │    ├─ 3. Feature Engineering/
│      │    ├─ 4. Scaling/
│      │    ├─ 5. Feature Selection/
│      │    └─ 6. Dimensionality Reduction/
│      ├─  2. Model Design & Implementation
│      └─  3. Model Evaluation
├─ results/
|  ├─eda_visualization                               # eda visualizations of data preprocessing parts 
│  │   ├─ 1. Cleaning & Missing Values/
│  │   ├─ 2. Encoding/
│  │   ├─ 3. Feature Engineering/
│  │   ├─ 4. Scaling/
│  │   ├─ 5. Feature Selection/
│  │   └─ 6. Dimensionality Reduction/
│  ├─ logs                                          
│  │   └─ Progress Review I.docx                     # Progress I report  
│  └─ outputs/                                       # Final CSV Files
│      ├─ Group Pipeline (One-Hot).csv
│      ├─ Group Pipeline (Frequency).csv
│      └─ Group Pipeline (One-Hot) & DR.csv
└─ README.md                       
```

---

## 📊 Next Steps (Progress Review II)
- Train baseline models (RandomForest, Linear Regression).
- Compare performance across One-Hot vs Frequency pipelines.
- Evaluate log-transformed target vs raw sales.
- Add feature importance plots and error analysis.

---

## 🧰 Tech Stack
- **Python 3.10+**, **pandas**, **numpy**, **matplotlib**, **scikit-learn**
- **Jupyter Notebooks** for step-by-step demos
- **GitHub** for version control and collaboration

---

📌 This README is updated **only up to Progress Review I** (Data Preprocessing & EDA).

