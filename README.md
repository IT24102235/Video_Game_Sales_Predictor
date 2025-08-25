

# 🎮 Video Game Sales Predictor

> **Predict video game sales from platform, genre, release info, scores, and more — with a clean, reproducible ML pipeline.**  
> Built for teamwork in **VS Code** with **GitHub** and **Jupyter**.

<p align="center">
  <img alt="Project banner" src="https://img.shields.io/badge/Python-3.10%2B-informational" />
  <img alt="scikit-learn" src="https://img.shields.io/badge/scikit--learn-Pipeline-blue" />
  <img alt="VS Code" src="https://img.shields.io/badge/Editor-VS%20Code-blueviolet" />
  <img alt="License" src="https://img.shields.io/badge/License-MIT-success" />
</p>

---

## ✨ Highlights
- **Beginner-friendly** but **production‑style** layout (src/ + notebooks/ + data/).
- **Reproducible pipeline** for data cleaning → feature engineering → modeling.
- **VS Code first** (Git, Pull Requests, code review) **+ Jupyter notebooks** for EDA/demos.
- **Team‑ready**: issue templates, branch naming, and PR checklist included below.
- Works with classic datasets like `vgsales.csv`, `Video_Games_Sales_as_at_22_Dec_2016.csv`, and newer `vgchartz-2024.csv` (place them in `data/raw/`).

---

## 🗂️ Project Structure
```
video-game-sales-predictor/
├─ data/
│  ├─ raw/          # put original CSVs here (ignored by Git)
│  └─ processed/    # cleaned/feature files (ignored by Git)
├─ notebooks/
│  └─ 01_eda.ipynb  # quick EDA starter (open in VS Code + Jupyter)
├─ reports/
│  └─ figures/      # images for README/report
├─ src/
│  ├─ data.py         # loading + column standardization helpers
│  ├─ preprocess.py   # missing values, encoding, scaling, outliers
│  └─ train.py        # baseline model + k-fold CV
├─ .gitignore
├─ requirements.txt
└─ README.md
```

> **Tip:** `data/` is ignored by Git to keep large files out of the repo. Share raw CSVs via Drive/OneDrive or ask each teammate to download locally.

---

## 🚀 Quick Start

### 1) Clone and set up
```bash
git clone https://github.com/<YOUR_ORG_OR_USER>/<YOUR_REPO>.git
cd <YOUR_REPO>

# Create a virtual environment
python -m venv .venv
# macOS/Linux
source .venv/bin/activate
# Windows
# .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### 2) Add datasets
Place one or more CSVs into `data/raw/`:
```
data/raw/vgsales.csv
data/raw/Video_Games_Sales_as_at_22_Dec_2016.csv
data/raw/vgchartz-2024.csv
```

### 3) Run a baseline model
```bash
python -m src.train
```
This will:
- Load and standardize columns,
- Apply a simple preprocessing pipeline,
- Train a baseline regressor (e.g., RandomForest) with K‑Fold CV,
- Print metrics and save any figures to `reports/figures/`.

### 4) Explore EDA in a notebook (inside VS Code)
```bash
jupyter notebook notebooks/01_eda.ipynb
```

---

## 🧹 Data Cleaning & Preprocessing Plan

Use the checklist below to **assign one technique per teammate** (great for dividing work and showcasing individual contributions):

- [ ] **Missing values**: numeric (median), categorical (most frequent or “Unknown”); document rationale.
- [ ] **Type fixes**: coerce scores/years to numeric (`errors="coerce"`); handle strings like `tbd`.
- [ ] **Column standardization**: unify names across sources (e.g., `Global_Sales` → `total_sales`).
- [ ] **Feature engineering**: game age, handheld flag, regional share ratios, decade bins, etc.
- [ ] **Categorical encoding**: One‑Hot (with `handle_unknown="ignore"`); consider grouping rare publishers.
- [ ] **Outliers**: inspect with boxplots; choose to cap/winsorize or leave as-is (justify).
- [ ] **Scaling**: Standard/MinMax for models that need it (linear/NN); keep raw for tree models.
- [ ] **Target shaping**: try `log1p(total_sales)` if distribution is highly skewed.
- [ ] **Train–validation split**: if predicting *future* sales, consider **time‑based** splits to avoid leakage.

> Capture decisions in `README.md` and commit small, focused PRs (one technique each).

---

## 📊 EDA Ideas (your first visuals)
- Missing‑value heatmap, class balance for `genre`/`platform`.
- Histograms/boxplots for `total_sales`, `critic_score`, `user_score`.
- Correlation heatmap (numeric only).
- Sales by **platform**, **genre**, **publisher**, **year/decade** (bar + trend).

Add figures to `reports/figures/` and reference them in your report or slides.

---

## 🤖 Modeling (baseline → better)

1. **Baseline**: RandomForestRegressor (robust to mixed features, minimal tuning).  
2. **Try next**: GradientBoosting / ExtraTrees / XGBoost (optional) and simple linear baselines on `log1p(total_sales)`.  
3. **Evaluation**: K‑Fold RMSE/MAE + a simple hold‑out by time if the task is “predict future sales”.  
4. **Feature importance**: permutation importance or model‑specific importances; add plots to `reports/figures/`.  
5. **Error analysis**: where do we under/over‑predict? Certain platforms, certain years?

> Keep results in a simple markdown table in your PR description for quick comparison.

---

## 🧪 Reproducibility
- Fix random seeds where possible (`np.random.seed`, model `random_state`).
- Keep **data transforms inside scikit‑learn Pipelines**.
- Log data versions and filtering steps in commit messages and PR body.
- Avoid hand‑editing CSVs; write transformation code and save to `data/processed/`.

---

## 🤝 Collaboration Guide (GitHub)

**One‑time setup**
```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

**Branching**
- Protect `main`.
- Use short‑lived branches: `feat/missing-values`, `feat/encoding`, `feat/outliers`, `feat/scaling`, `feat/features-genre-platform`.

**Conventional commit messages (suggested)**
```
feat: add one-hot encoder with rare-category grouping
fix: handle tbd values in user_score
docs: update README with EDA plots
refactor: move standardize_columns into data.py
```

**PR checklist**
- [ ] Clear title & description of the change.
- [ ] Screenshots/plots for EDA or metrics.
- [ ] “Why” explained (dataset‑specific rationale).
- [ ] No big files committed (data stays in `data/`).

---

## 🧾 Assignment Deliverables Map (helpful checklist)

### Progress Review I — *Data Cleaning, Preprocessing & EDA*
- [ ] Each member: one technique with **reasoning + code + output plot**.
- [ ] Group: a **combined preprocessing pipeline** that runs end‑to‑end.
- [ ] Notebook/script walkthrough prepared.

### Progress Review II — *Model Design & Implementation*
- [ ] Baseline vs improved models; cross‑validation results table.
- [ ] What worked/what didn’t; feature importance and error analysis.

### Progress Review III — *Evaluation & Comparison*
- [ ] Final model selection with metrics; fair comparison.
- [ ] Clear visuals/tables; limitations + future work.

### Final Report
- [ ] Ethics & bias analysis (data source, representation, bias mitigation).
- [ ] Teamwork & contribution evidence.
- [ ] Final cleaned dataset & code rerun instructions.

---

## 🧰 Tech Stack

- **Python 3.10+**
- **pandas**, **numpy**, **matplotlib**
- **scikit‑learn** (pipelines, preprocessing, models)
- **VS Code** + **Jupyter** extensions

> Optional: **XGBoost**, **lightgbm**, **optuna** for tuning (add to `requirements.txt` if used).

---

## ⚙️ VS Code: recommended extensions
- **Python** (ms-python.python)
- **Jupyter** (ms-toolsai.jupyter)
- **GitHub Pull Requests** (GitHub.vscode-pull-request-github)
- **Pylance** (ms-python.vscode-pylance)

Create `.vscode/extensions.json`:
```json
{
  "recommendations": [
    "ms-python.python",
    "ms-toolsai.jupyter",
    "github.vscode-pull-request-github",
    "ms-python.vscode-pylance"
  ]
}
```

---

## 🗃️ Data Sources (examples to acknowledge)
- Kaggle “Video Game Sales” variants (`vgsales.csv`, `Video_Games_Sales_as_at_22_Dec_2016.csv`)
- VGChartz‑style exports (`vgchartz-2024.csv`)


---

## 🧑‍💻 Maintainers
- **Senuja Thisum** (maintainer) — @senujathisumekanayake  
- **Nimesh Gunathilake**
- **Okindu Abeyawickrama**
- **Moulana**
- **Imalka Nishshanka**
- **Supuni Warushawithanage**

---

## 📄 License
This project does'nt have a License.

---

## ❓FAQ / Troubleshooting
- **Git asks for user.name/user.email** → set once:  
  `git config --global user.name "Your Name" && git config --global user.email "you@example.com"`
- **Can’t push to `main`** → open a PR from your feature branch; ask for a review.
- **Plots don’t show in VS Code** → install Jupyter extension and select the correct Python interpreter (`.venv`).

---

> If you want, open an issue titled “🏁 Onboarding” and paste this checklist so every new teammate can tick through setup quickly.

