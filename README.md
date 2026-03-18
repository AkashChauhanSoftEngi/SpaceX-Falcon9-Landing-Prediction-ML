# 🚀 SpaceX Falcon 9 First Stage Landing Prediction
### IBM Data Science Professional Certificate — Capstone Project

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![sklearn](https://img.shields.io/badge/scikit--learn-ML-green.svg)](https://scikit-learn.org/)
[![Plotly Dash](https://img.shields.io/badge/Plotly-Dash-purple.svg)](https://dash.plotly.com/)
[![Folium](https://img.shields.io/badge/Folium-Maps-darkgreen.svg)](https://python-visualization.github.io/folium/)

---

## 📋 Project Overview

SpaceX advertises Falcon 9 rocket launches on its website with a cost of **$62 million**, while other providers cost upward of **$165 million** each. Much of this saving is due to SpaceX's ability to **reuse the first stage booster**.

This project builds a **machine learning pipeline** to predict whether the Falcon 9 first stage will land successfully — enabling any competing company to estimate the true cost of a launch and make competitive bids. (SpaceX-Falcon9-Landing-Prediction — IBM Data Science Capstone)
---

## 🎯 Objectives

- Collect SpaceX launch data via REST API and Web Scraping
- Perform Exploratory Data Analysis (EDA) with SQL and visualizations
- Build interactive maps and dashboards for visual analytics
- Train and evaluate multiple ML classification models
- Identify the best-performing model for landing prediction

---

## 📁 Repository Structure

```
DataScienceProjectsIBM/
│
├── 📓 jupyter-labs-spacex-data-collection-api.ipynb
│      → Data collection via SpaceX REST API
│
├── 📓 jupyter-labs-webscraping (1).ipynb
│      → Data collection via Wikipedia web scraping (BeautifulSoup)
│
├── 📓 labs-jupyter-spacex-Data wrangling.ipynb
│      → Data cleaning, feature engineering & target variable creation
│
├── 📓 jupyter-labs-eda-sql-coursera_sqllite (2).ipynb
│      → Exploratory Data Analysis using SQL & SQLite
│
├── 📓 edadataviz (1).ipynb
│      → EDA with Matplotlib & Seaborn visualizations
│
├── 📓 lab_jupyter_launch_site_location.ipynb
│      → Interactive visual analytics with Folium maps
│
└── 📓 SpaceX_Machine Learning Prediction_Part_5.ipynb
       → ML model training, hyperparameter tuning & evaluation
```

---

## 🔄 Project Workflow

```
Data Collection        Data Wrangling         EDA
─────────────────    ─────────────────    ─────────────────
SpaceX REST API   →  Clean & Engineer  →  SQL Queries
Web Scraping          Target Variable       Visualizations
                      One-Hot Encoding      Folium Maps
                      StandardScaler        Plotly Dash

                          ↓
                   Machine Learning
                   ─────────────────
                   Logistic Regression
                   Support Vector Machine
                   Decision Tree          → Best Model → Predict
                   K-Nearest Neighbors
```

---

## 📊 Notebooks Description

### 1. `jupyter-labs-spacex-data-collection-api.ipynb`
**Data Collection — SpaceX REST API**
- Makes GET requests to `api.spacexdata.com` endpoints
- Extracts: FlightNumber, BoosterVersion, PayloadMass, Orbit, LaunchSite, Outcome, LandingPad, etc.
- Handles nested JSON and missing values
- Outputs: `dataset_part_1.csv` with 90 launch records

### 2. `jupyter-labs-webscraping (1).ipynb`
**Data Collection — Web Scraping**
- Scrapes Wikipedia's *List of Falcon 9 and Falcon Heavy launches*
- Uses `BeautifulSoup` to parse HTML tables
- Extracts: Flight number, Date, Launch site, Payload, Orbit, Customer, Landing outcome
- Outputs: `spacex_web_scraped.csv`

### 3. `labs-jupyter-spacex-Data wrangling.ipynb`
**Data Wrangling & Feature Engineering**
- Handles missing `PayloadMass` values (filled with column mean)
- Creates binary target column `Class`: `1` = Successful landing, `0` = Failed
- Maps 9+ landing outcome types to binary labels
- Outputs: `dataset_part_2.csv`

### 4. `jupyter-labs-eda-sql-coursera_sqllite (2).ipynb`
**Exploratory Data Analysis — SQL**
- Loads data into SQLite database using `sqlite3`
- Executes 10 SQL tasks covering:
  - Unique launch sites
  - Total payload mass by customer
  - Success rates by orbit
  - First successful ground pad landing date
  - Ranked landing outcomes between date ranges

### 5. `edadataviz (1).ipynb`
**EDA with Visualizations**
- Uses `Matplotlib`, `Seaborn`, and `catplot`
- Visualizations include:
  - FlightNumber vs LaunchSite scatter plot
  - PayloadMass vs LaunchSite scatter plot
  - Success rate by Orbit type (bar chart)
  - FlightNumber vs Orbit type
  - PayloadMass vs Orbit type
  - Yearly launch success trend (line chart)
- Feature engineering: One-Hot Encoding → 80 features

### 6. `lab_jupyter_launch_site_location.ipynb`
**Interactive Visual Analytics — Folium**
- Creates interactive world map with all 4 launch sites marked
- MarkerCluster with green (success) / red (failure) markers
- Proximity analysis for CCAFS LC-40:
  - 🌊 Coastline: **0.93 km**
  - 🚂 Railway: **1.33 km**
  - 🛣️ Highway: **10.52 km**
  - 🏙️ City: **27.02 km**

### 7. `SpaceX_Machine Learning Prediction_Part_5.ipynb`
**Machine Learning Prediction**
- Standardizes features using `StandardScaler`
- Splits data: 80% train / 20% test (`random_state=2`)
- Trains 4 models with `GridSearchCV` (cv=10):

| Model | CV Accuracy | Test Accuracy | Best Parameters |
|-------|-------------|---------------|-----------------|
| Logistic Regression | 84.6% | **83.33%** | C=0.1, penalty=l2 |
| Support Vector Machine | 84.8% | **83.33%** | kernel=rbf, C=1.0 |
| Decision Tree | **87.5%** | **83.33%** | criterion=entropy, max_depth=6 |
| K-Nearest Neighbors | 84.8% | **83.33%** | n_neighbors=7 |

🏆 **Best Model: Decision Tree** — Highest cross-validation accuracy (87.5%)

---

## 💡 Key Insights

1. **KSC LC-39A** has the highest launch success rate (41.7% of all successes)
2. **LEO orbit** has the best landing success rate (~85%)
3. **GTO orbit** is the hardest to land (~46% success rate)
4. **Higher flight numbers** correlate with more successful landings (experience effect)
5. **Payload range 2,000–4,000 kg** shows the best landing outcomes
6. **FT and B5 booster versions** have the highest success rates
7. Success rate grew from **0% (2010) to 100% (2020)** — continuous improvement

---

## 🛠️ Technologies Used

| Category | Tools |
|----------|-------|
| Language | Python 3.8+ |
| Data Manipulation | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Interactive Maps | Folium, MarkerCluster |
| Dashboard | Plotly Dash |
| Machine Learning | Scikit-learn |
| Database | SQLite3, SQL |
| Web Scraping | BeautifulSoup4, Requests |
| API | SpaceX REST API |
| Environment | Jupyter Notebook |

---

## ⚙️ Installation & Setup

```bash
# Clone the repository
git clone https://github.com/AkashChauhanSoftEngi/DataScienceProjectsIBM.git
cd DataScienceProjectsIBM

# Install required packages
pip install pandas numpy matplotlib seaborn scikit-learn
pip install folium dash plotly
pip install beautifulsoup4 requests
pip install ipython-sql sqlalchemy

# Launch Jupyter Notebook
jupyter notebook
```

---

## 🚀 Running the Dashboard

```bash
# Install dash
pip install pandas dash

# Run the Plotly Dash app
python spacex_dash_app.py

# Open browser at:
# http://127.0.0.1:8050
```

---

## 📈 Results Summary

- **Dataset**: 90 SpaceX launch records (2010–2020)
- **Features**: 80 (after one-hot encoding)
- **Test Samples**: 18
- **Best Test Accuracy**: **83.33%** (all 4 models)
- **Best CV Accuracy**: **87.5%** (Decision Tree)

---

## 👤 Author

**Akash Chauhan**  
IBM Data Science Professional Certificate — Capstone Project  
GitHub: [@AkashChauhanSoftEngi](https://github.com/AkashChauhanSoftEngi)

---

## 📄 License

This project is part of the IBM Data Science Professional Certificate program on Coursera.  
© IBM Corporation 2021. All rights reserved.
