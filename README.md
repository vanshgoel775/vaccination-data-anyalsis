# 💉 Vaccination Data Analysis & Visualization

## 📌 Project Overview

This project performs **vaccination data analysis, exploratory data analysis (EDA), MySQL database management, and Power BI visualization** using multiple vaccination-related datasets.

The project analyzes vaccination coverage, disease incidence rates, reported cases, vaccine introductions, and vaccine schedules to identify trends and patterns across countries, diseases, years, and vaccine types.

---

## 🎯 Objectives

* Analyze vaccination coverage over different years.
* Study vaccination coverage by antigen.
* Analyze disease incidence rates.
* Explore reported disease cases and their trends.
* Analyze vaccine introduction status over time.
* Study vaccine schedules and vaccine codes.
* Store and organize vaccination data in **MySQL**.
* Normalize the database to reduce redundancy.
* Build an interactive **Power BI dashboard** for visualization.
* Generate meaningful insights from vaccination datasets.

---

## 🛠️ Technologies Used

| Technology       | Purpose                           |
| ---------------- | --------------------------------- |
| Python           | Data analysis and preprocessing   |
| Pandas           | Data manipulation                 |
| NumPy            | Numerical operations              |
| Matplotlib       | Data visualization                |
| Seaborn          | Statistical visualization         |
| Jupyter Notebook | Development and EDA               |
| MySQL            | Database storage and SQL analysis |
| PyMySQL          | Python-MySQL connectivity         |
| Power BI         | Interactive dashboard             |
| Excel            | Source datasets                   |

---

## 📂 Datasets

The project uses five major datasets:

### 1. Coverage Data

Contains information related to:

* Country/Region
* Year
* Antigen
* Target population
* Number of doses
* Vaccination coverage

Main analysis includes:

* Vaccination coverage trends
* Mean coverage by antigen
* Total doses by antigen
* Top antigens by coverage
* Target population vs doses

---

### 2. Incidence Rate Data

Contains disease incidence information.

Important fields include:

* Country/Region
* Year
* Disease
* Incidence Rate

Analysis includes:

* Mean incidence rate by disease
* Incidence rate by region
* Highest-incidence region for each disease
* Disease incidence trends over time

---

### 3. Reported Cases Data

Contains reported disease cases by region and year.

Analysis includes:

* Total reported cases by disease
* Reported cases over time
* Top regions with reported cases
* Disease-wise case distribution
* Relationship between reported cases and incidence rate

---

### 4. Vaccine Introduction Data

Contains information about vaccine introduction status.

Analysis includes:

* Vaccine introduction status distribution
* Introduction status by year
* Trends in vaccine introductions

---

### 5. Vaccine Schedule Data

Contains vaccine scheduling information.

Analysis includes:

* Top vaccine codes
* Scheduled rounds
* Vaccine distribution by geographical area
* Vaccines by age group
* Year-wise vaccine counts
* Vaccine recommendations by target population

---

# 🔄 Project Workflow

```text
Raw Excel Data
      ↓
Data Loading
      ↓
Data Cleaning & Preprocessing
      ↓
Exploratory Data Analysis
      ↓
Python Visualization
      ↓
MySQL Database
      ↓
Database Normalization
      ↓
SQL Relationships
      ↓
Power BI Dashboard
      ↓
Insights & Reporting
```

---

# 🐍 Python EDA

The `Vaccination_analysis.ipynb` notebook performs exploratory analysis on all five datasets.

### Coverage Analysis

The project analyzes:

* Coverage trends over years
* Top regions by average coverage
* Total doses by antigen
* Mean coverage by antigen
* Coverage distribution
* Coverage trends for top antigens
* Target population and dose trends

Example visualization:

```python
sns.lineplot(
    data=coverage_data,
    x='YEAR',
    y='COVERAGE',
    errorbar=None
)
```

---

### Incidence Rate Analysis

The project calculates average incidence rates for different diseases and regions.

```python
disease_rates = (
    incidence_rate_data
    .groupby('DISEASE')['INCIDENCE_RATE']
    .mean()
    .reset_index()
)
```

It also analyzes incidence-rate trends over time.

---

### Reported Cases Analysis

Reported cases are analyzed by:

* Disease
* Year
* Region

Example:

```python
cases_over_time = (
    reported_cases_data
    .groupby(['YEAR', 'DISEASE'])['CASES']
    .sum()
    .reset_index()
)
```

The project also compares:

```text
Incidence Rate ↔ Reported Cases
```

using a scatter plot.

---

### Vaccine Introduction Analysis

The project examines different vaccine introduction statuses and their distribution over time.

The analysis includes statuses such as:

```text
Yes
Yes (P)
Yes (R)
Yes (A)
Yes (O)
Yes (S)
Yes (OPV)
High risk
No
No (D)
ND
NR
```

---

### Vaccine Schedule Analysis

The project analyzes:

* Top vaccine codes
* Scheduled rounds
* Geographical distribution
* Age groups
* Vaccine counts by year
* Target populations

---

# 🗄️ MySQL Database

The `Python_to_Sql_database_connect.ipynb` notebook connects Python with MySQL using **PyMySQL**.

Database created:

```text
vaccination_data_analysis
```

The project creates tables for:

```text
Coverage
IncidenceRate
ReportedCases
VaccineIntroduction
VaccineSchedule
Countries
Diseases
Years
WHO_Region
```

---

# 🏗️ Database Normalization

The database is normalized to reduce duplicate information and improve query performance.

Separate tables are created for:

* Countries
* Diseases
* Years
* WHO Regions

Relationships are established using:

```text
Primary Keys
Foreign Keys
```

For example:

```text
Countries
   │
   ├── Coverage
   ├── IncidenceRate
   └── ReportedCases
```

and:

```text
Years
   │
   ├── Coverage
   ├── IncidenceRate
   ├── ReportedCases
   └── VaccineIntroduction
```

---

# 📊 Power BI Dashboard

The project also includes a Power BI dashboard:

```text
Vaccination-Data-Analysis-and-Visualization.pbix
```

The dashboard provides visual analysis of vaccination-related data and helps understand trends across:

* Vaccination coverage
* Diseases
* Incidence rates
* Reported cases
* Vaccine introductions
* Vaccine schedules
* Regions
* Years

---

# 📁 Project Structure

```text
Vaccination-Data-Analysis/
│
├── Vaccination_analysis.ipynb
├── Python_to_Sql_database_connect.ipynb
│
├── coverage-data.xlsx
├── incidence-rate-data.xlsx
├── reported-cases-data.xlsx
├── vaccine-introduction-data.xlsx
├── vaccine-schedule-data.xlsx
│
├── Vaccination-Data-Analysis-and-Visualization.pbix
│
├── clean_coverage_data.xlsx
├── clean_incidence_rate_data.xlsx
├── clean_reported_cases_data.xlsx
├── clean_vaccine_introduction_data.xlsx
├── clean_vaccine_schedule_data.xlsx
│
└── README.md
```

---

# ⚙️ Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/vaccination-data-analysis.git
```

Move into the project directory:

```bash
cd vaccination-data-analysis
```

Install the required Python libraries:

```bash
pip install pandas numpy matplotlib seaborn openpyxl pymysql jupyter
```

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open:

```text
Vaccination_analysis.ipynb
```

---

# 🗄️ MySQL Setup

Make sure MySQL Server is installed and running.

The project creates a database named:

```sql
vaccination_data_analysis
```

Update the MySQL credentials in the notebook before running the database connection code:

```python
host = "localhost"
user = "root"
password = "YOUR_PASSWORD"
```

**Do not upload your real MySQL password to GitHub.**

---

# 📈 Key Analysis Performed

The project covers:

### Vaccination

* Vaccination coverage trends
* Doses administered
* Target population
* Antigen-wise coverage
* Regional vaccination differences

### Disease

* Disease incidence rates
* Reported cases
* Disease trends over time
* Regional disease burden

### Vaccine Introduction

* Introduction status
* Year-wise introduction trends

### Vaccine Schedule

* Vaccine codes
* Scheduled rounds
* Age groups
* Target populations
* Geographical distribution

### Combined Analysis

The project also merges:

```text
Reported Cases
        +
Incidence Rate
        +
Vaccination Coverage
```

to explore relationships between vaccination-related measures and reported disease outcomes.

---

# 💡 Project Highlights

* Performed EDA on multiple real-world datasets.
* Used Python for data cleaning and visualization.
* Created multiple analytical visualizations using Matplotlib and Seaborn.
* Connected Python with MySQL.
* Designed a normalized relational database.
* Used primary and foreign keys to establish relationships.
* Built a Power BI dashboard for interactive visualization.
* Combined multiple datasets for deeper analysis.

---

# 🚀 Future Improvements

Possible improvements include:

* Add more interactive Power BI filters.
* Add advanced SQL analytical queries.
* Create automated ETL pipelines.
* Add statistical correlation analysis.
* Add machine learning models for forecasting.
* Automate data refresh.
* Deploy the dashboard/report online.
* Create an automated data pipeline from source to dashboard.

---

# 👨‍💻 Author

**Vansh Goel**

B.Tech – Computer Science & Engineering

GitHub:
`https://github.com/vanshgoel775`

---

## ⭐ If you find this project useful

Consider giving the repository a ⭐ on GitHub.
