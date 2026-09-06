# Titanic Dataset — Data Cleaning & Preprocessing

## Project Overview

This project focuses on cleaning and preprocessing the Titanic dataset to make it clean, consistent, and ready for further data analysis.

The project was completed as **Task 1: Data Cleaning & Preprocessing** of the Synent Technologies Data Science Internship Program.

---

## Objective

The objective of this project is to preprocess the raw Titanic dataset by:

* Handling missing values
* Removing duplicate records
* Converting data types
* Renaming columns
* Validating the cleaned dataset
* Exporting the final cleaned dataset

---

## Dataset

**Dataset:** Titanic Dataset
**Source:** Kaggle

The original dataset contains:

* **891 rows**
* **12 columns**

### Original Columns

```text
PassengerId
Survived
Pclass
Name
Sex
Age
SibSp
Parch
Ticket
Fare
Cabin
Embarked
```

---

## Tools and Libraries

* Python
* Pandas
* Jupyter Notebook

---

## Data Cleaning Process

### 1. Dataset Loading

The raw Titanic dataset was loaded into a Pandas DataFrame using `read_csv()`.

```python
df = pd.read_csv("../data/Titanic-Dataset_Cleaned.csv")
```

---

### 2. Initial Dataset Inspection

The dataset was inspected before preprocessing to understand its structure and identify potential data quality issues.

The following checks were performed:

* Dataset dimensions
* Column names
* Data types
* Statistical summary
* Sample records
* Missing values

---

### 3. Handling Missing Values

Missing values were identified and handled according to the type and amount of missing data.

| Column     | Treatment                                                  |
| ---------- | ---------------------------------------------------------- |
| `Age`      | Missing values replaced with the median                    |
| `Embarked` | Missing values replaced with the mode                      |
| `Cabin`    | Column removed due to a large proportion of missing values |

#### Age

The missing values in `Age` were replaced using the median value of the column.

```python
df["Age"] = df["Age"].fillna(df["Age"].median())
```

#### Embarked

The missing values in `Embarked` were replaced using the mode.

```python
df["Embarked"] = df["Embarked"].fillna(df["Embarked"].mode()[0])
```

#### Cabin

The `Cabin` column was removed because it contained a large proportion of missing values.

```python
df.drop(columns=["Cabin"], inplace=True)
```

---

### 4. Removing Duplicate Records

The dataset was checked for duplicate rows.

```python
df.duplicated().sum()
```

Any duplicate records were removed using:

```python
df.drop_duplicates(inplace=True)
```

The dataset was then checked again to verify that duplicate records had been removed.

---

### 5. Data Type Conversion

The data types of the columns were standardized according to the nature of the data.

Numerical columns were converted to appropriate integer or floating-point types.

Categorical columns were converted to the categorical data type.

Examples include:

```python
df["PassengerId"] = df["PassengerId"].astype("int64")
df["Survived"] = df["Survived"].astype("int64")
df["Pclass"] = df["Pclass"].astype("int64")

df["Age"] = df["Age"].astype("float64")
df["Fare"] = df["Fare"].astype("float64")

df["Sex"] = df["Sex"].astype("category")
df["Embarked"] = df["Embarked"].astype("category")
```

---

### 6. Renaming Columns

The column names were standardized using lowercase letters and underscores to improve consistency and readability.

The renamed columns include:

| Original Column | New Column         |
| --------------- | ------------------ |
| `PassengerId`   | `passenger_id`     |
| `Survived`      | `survived`         |
| `Pclass`        | `passenger_class`  |
| `Name`          | `name`             |
| `Sex`           | `sex`              |
| `Age`           | `age`              |
| `SibSp`         | `siblings_spouses` |
| `Parch`         | `parents_children` |
| `Ticket`        | `ticket`           |
| `Fare`          | `fare`             |
| `Embarked`      | `embarked`         |

The `Cabin` column is not included because it was removed during missing-value handling.

---

## Final Validation

After completing the preprocessing steps, the cleaned dataset was validated to ensure that the required cleaning operations were successfully completed.

The final validation included:

* Checking dataset dimensions
* Checking for remaining missing values
* Checking for duplicate records
* Checking data types
* Checking final column names
* Reviewing sample records

---

## Output

The cleaned dataset was exported as:

```text
Titanic-Cleaned.csv
```

The original dataset was kept unchanged, while the cleaned version was saved separately for further analysis.

---

## Project Structure

```text
synent-task1-titanic-cleaning-yourname/
│
├── data/
│   ├── Titanic-Dataset.csv
│   └── Titanic-Dataset_Cleaned.csv
│
├── notebooks/
│   └── titanic_dataset_cleaning.ipynb
│
└── README.md
```

---

## Result

The Titanic dataset was successfully cleaned and preprocessed.

The completed preprocessing tasks are:

* Missing values handled
* Duplicate records checked and removed
* Data types converted
* Column names standardized
* Final dataset validated
* Cleaned dataset exported

The resulting dataset is ready for further data analysis.
