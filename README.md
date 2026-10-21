# Titanic Dataset - Data Cleaning & Preprocessing

This repository contains data cleaning, preprocessing, and exploratory workflows on the Titanic dataset, completed as part of the internship assignment.

---

## Project Structure

```text
Indrobeams/
├── data/
│   ├── titanic.csv               # Raw dataset
│   └── titanic_cleaned.csv       # Cleaned and processed dataset
├── notebooks/
│   ├── titanic.ipynb             # Main cleaning and preprocessing notebook
│   └── pandas_data_cleaning.ipynb# Subsetting & Pandas reference tutorial
├── .gitignore                    # Ignored files (virtual environments, caches)
├── README.md                     # Project documentation
└── requirements.txt              # Project dependencies
```

---

## Data Cleaning Steps Applied

1. **Profiling & Inspection**:
   - Analyzed dataset dimensions (891 rows, 12 columns), data types, and initial records.
2. **Deduplication**:
   - Checked for duplicate rows and verified unique passenger identifiers (`PassengerId`). No duplicates were found.
3. **Handling Missing Values**:
   - `Cabin`: Dropped the column due to excessive missing values (>77%).
   - `Age`: Imputed missing entries (~20%) with the rounded mean age (30).
   - `Embarked`: Dropped the 2 rows with missing boarding ports (<0.3%).
4. **Data Normalization & Formatting**:
   - Converted `Age` from floating point to clean integer (`int`).
   - Rounded `Fare` to 2 decimal places (standard financial currency format).
   - Trimmed whitespace and converted `Sex` and `Embarked` strings to consistent lowercase.
5. **Validation & Output**:
   - Verified that 0 missing values remain across all columns.
   - Saved the final clean dataset to `data/titanic_cleaned.csv` with `index=False`.

---

## Setup & Running the Notebook

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
   Open `notebooks/titanic.ipynb` to view or run the full data cleaning process.
