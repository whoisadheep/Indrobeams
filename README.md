# Data Analytics & Engineering Assignments

This repository contains internship assignments focused on data cleaning, exploratory data analysis (EDA), and statistical SQL querying.

---

## Project Structure

```text
Indrobeams/
├── data/
│   ├── titanic.csv                     # Raw Titanic dataset
│   ├── titanic_cleaned.csv             # Cleaned Titanic dataset
│   ├── titanic_cleaned.parquet         # Parquet format of cleaned Titanic data
│   ├── dc_bikeshare_q1_2012.csv        # Mode Analytics DC Bikeshare sample
│   └── bike_sharing_hourly.csv         # Full 2-year hourly Bikeshare time-series (17,379 rows)
├── notebooks/
│   ├── titanic.ipynb                   # Task 1: Data cleaning & preprocessing pipeline
│   ├── eda_statistical_queries.ipynb   # Task 2: EDA, SQL window functions, and statistical analysis
│   └── pandas_data_cleaning.ipynb      # Reference tutorial on Pandas subsetting
├── .gitignore                          # Ignored virtual environments, caches, and checkpoints
├── README.md                           # Project documentation
└── requirements.txt                    # Project dependencies
```

---

## Task 1: Data Cleaning & Preprocessing (Titanic Dataset)

- **Objective**: Handle missing values, deduplicate records, normalize data formats, and export validated CSV/Parquet files.
- **Key Steps**:
  1. Profiled and audited schema dimensions (891 rows, 12 columns).
  2. Verified deduplication across all columns and candidate keys (`PassengerId`).
  3. Dropped `Cabin` (>77% missing), imputed `Age` with rounded mean (30), and dropped 2 rows missing `Embarked`.
  4. Normalized `Age` to `int`, rounded `Fare` to 2 decimal places, and trimmed/lowercased text fields.
  5. Exported validated data to `data/titanic_cleaned.csv` and `data/titanic_cleaned.parquet`.

---

## Task 2: Exploratory Data Analysis & Statistical SQL Queries (Due 3 Nov 2026)

- **Objective**: Execute exploratory queries using SQL window functions, aggregations, and correlation matrices. Identify trends, distribution outliers, and seasonal variations with histograms, box plots, and summary tables.
- **Dataset**: Capital Bikeshare Hourly Time-Series (`bike_sharing_hourly.csv`, 17,379 records).
- **Techniques & Highlights**:
  1. **SQL Window Functions**:
     - `RANK() OVER (PARTITION BY season ORDER BY AVG(cnt) DESC)`: Top peak commute hours per season.
     - `AVG() OVER (ORDER BY dteday ROWS BETWEEN 6 PRECEDING AND CURRENT ROW)`: 7-day rolling moving average smoothing daily fluctuations.
     - `LAG(cnt, 24) OVER (ORDER BY dteday, hr)`: Day-over-day same-hour ridership comparison.
     - `NTILE(4) OVER (ORDER BY cnt)`: Segmenting hourly demand into operational quartiles.
  2. **Distributions & Outlier Detection**:
     - Histograms: Right-skewed hourly demand distribution and bell-shaped temperature distribution.
     - Box Plots: Seasonal demand distributions and working day vs. weekend profiles.
     - IQR Rule: Statistically identified 505 outlier hours (>574 rides/hour) coinciding with pleasant weather and special events.
  3. **Seasonality & Trends**:
     - Bimodal weekday commuter peaks (8:00 AM & 5:00–6:00 PM) driven by registered users vs. unimodal weekend afternoon peaks (1:00–3:00 PM) driven by casual users.
     - Multi-year ridership growth from 2011 to 2012.
  4. **Correlation Analysis**:
     - Pearson heatmap showing strong positive correlation between temperature and ridership ($r = +0.40$), and negative correlation with humidity ($r = -0.32$).

---

## Setup & Running the Notebooks

1. **Clone the repository**:
   ```bash
   git clone https://github.com/whoisadheep/Indrobeams.git
   cd Indrobeams
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Launch Jupyter**:
   ```bash
   jupyter lab
   ```
   - Open `notebooks/titanic.ipynb` for Task 1.
   - Open `notebooks/eda_statistical_queries.ipynb` for Task 2.
