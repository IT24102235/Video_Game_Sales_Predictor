# 🎮 Video Game Sales Predictor

> **Predict video game sales from platform, genre, release info, scores, and more — with a clean, reproducible ML pipeline.**  
> Built for teamwork in **VS Code** with **GitHub** and **Jupyter**.

---

## ✨ Progress Review I (Data Preprocessing & EDA)

### ✅ Work Completed
For **Progress Review I**, we focused on **data cleaning, preprocessing, and EDA visualizations**. All steps are stored in `data/cleaned/` and `notebooks/1. Data Preprocessing/`.

**1. Data Cleaning & Missing Values**  
- Removed duplicates and inconsistent rows.
- Handled missing values: numeric (median), categorical (mode/“Unknown”).
- Standardized column names across datasets.

**2. Encoding**  
- **One-Hot Encoding** applied to categorical variables with limited categories (Genre, Platform).
- **Frequency Encoding** applied to high-cardinality variables (Publisher, Developer).

**3. Scaling**  
- Standardization (Z-score) for numerical features (Critic Score, User Score, Sales).
- Min-Max scaling tested for algorithms sensitive to ranges.

**4. Feature Engineering**  
- Created `Total_Regional_Sales` (NA+EU+JP+Other).
- Derived `Sales_per_Review` and `Decade` features.
- Applied log-transform to Global Sales for normalization.

**5. Feature Selection**  
- Used correlation analysis, Chi-Square tests, and RFE to reduce redundant features.
- Identified Platform, Year, and Critic Score as most important.

**6. Dimensionality Reduction**  
- Applied PCA on One-Hot encoded dataset (reduced from ~200 features to ~30 while keeping ~90% variance).

**7. Exploratory Data Analysis (EDA)**  
- Histograms of Global Sales → highly skewed (few blockbuster titles dominate).
- Boxplots by Genre → Action & Sports genres sell highest.
- Correlation heatmap → Critic Score correlates more strongly with sales than User Score.
- Sales trends → peak sales between 2008–2010.

**8. Integrated Pipeline**  
- **Pipeline A (One-Hot + Scaling + PCA)**
- **Pipeline B (Frequency Encoding + Scaling)**

Both pipelines are modular and ready for model training in Progress Review II.

---

## 🗂️ Project Structure (Updated for Review I)
```
video-game-sales/
├─ data/
│  ├─ raw/                                # Original CSVs
│  ├─ cleaned/                            # Step-by-step cleaned datasets
│  │   ├─ 1. Cleaning & Missing Values
│  │   ├─ 2. Encoding
│  │   ├─ 3. Scaling
│  │   ├─ 4. Feature Engineering
│  │   ├─ 5. Feature Selection
│  │   └─ 6. Dimensionality Reduction
│  └─ Final/                              # Integrated pipelines
│      └─ VGChartz_2024/
│           ├─ Final Pipeline (1-Hot).csv
│           ├─ Final Pipeline (Frequency).csv
│           └─ Final Pipeline (1-Hot)&DR.csv
├─ notebooks/
│  └─ 1. Data Preprocessing/              # Jupyter notebooks per step
├─ reports/
│  └─ Progress Review I.docx              # Viva notes/report
└─ README.md
```

---

## 📊 Next Steps (Progress Review II)
- Train baseline models (RandomForest, Linear Regression).
- Compare performance across One-Hot vs Frequency pipelines.
- Evaluate log-transformed target vs raw sales.
- Add feature importance plots and error analysis.

---

## 👥 Team Contributions
- Each team member implemented **one preprocessing technique** (missing values, encoding, scaling, feature engineering, etc.).
- Work integrated into a **combined pipeline** for group evaluation.

---

## 🧰 Tech Stack
- **Python 3.10+**, **pandas**, **numpy**, **matplotlib**, **scikit-learn**
- **Jupyter Notebooks** for step-by-step demos
- **GitHub + VS Code** for version control and collaboration

---

📌 This README is updated **only up to Progress Review I** (Data Preprocessing & EDA).

