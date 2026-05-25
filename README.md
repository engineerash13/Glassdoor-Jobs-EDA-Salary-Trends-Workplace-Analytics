# 💼 Glassdoor Jobs — Exploratory Data Analysis

> **Decoding salary trends, workplace satisfaction, and hiring patterns across industries using 956 real job postings**

---

## 📌 Project Overview

In today's competitive talent market, understanding **what companies pay, how they're rated, and what skills they demand** is invaluable for job seekers, employers, and recruiters alike. This project performs a structured **Exploratory Data Analysis (EDA)** on Glassdoor job posting data to surface actionable insights around salary benchmarks, company ratings, sector demand, and the workplace factors that shape the modern employment landscape.

---

## 🗂️ Dataset Description

| Attribute | Details |
|---|---|
| **Dataset** | `glassdoor_jobs.csv` |
| **Rows** | 956 |
| **Columns** | 15 |
| **Duplicates** | 0 |
| **Missing Values** | None (post-cleaning) |

### Key Columns

| Column | Description |
|---|---|
| `Job Title` | Position title (e.g., Data Scientist, Software Engineer) |
| `Company Name` | Hiring company |
| `Salary Estimate` | Raw salary range string (e.g., `$80K–$120K`) |
| `Rating` | Glassdoor company rating (1–5 scale) |
| `Location` | City, State of the job |
| `Headquarters` | Company HQ location |
| `Company Size` | Employee count range |
| `Company Type` | Public / Private / Government |
| `Industry` | Business sector (Tech, Finance, Healthcare, etc.) |
| `Sector` | Broad classification (IT, Banking, Consulting, etc.) |
| `Revenue` | Company revenue range |
| `Founded` | Year of company founding |
| `Competitor` | List of competing companies |

---

## 🎯 Business Objective

This analysis serves four key stakeholder groups:

| Stakeholder | Value Delivered |
|---|---|
| **Job Seekers** | Understand salary expectations by role, location & company size |
| **Employers** | Benchmark compensation packages to attract top talent |
| **Recruiters** | Identify fair compensation practices across industries |
| **Analysts** | Data-driven salary trend insights by industry & geography |

---

## 🧹 Feature Engineering & Data Wrangling

Raw Glassdoor salary data required significant transformation before analysis:

```python
# Salary parsing pipeline
salary → strip Glassdoor estimate tags
       → remove '$', 'K', 'per hour' labels
       → extract min_salary and max_salary
       → compute avg_salary = (min + max) / 2
```

### New Features Created

| Feature | Description |
|---|---|
| `min_salary` | Lower bound of salary range |
| `max_salary` | Upper bound of salary range |
| `avg_salary` | Midpoint salary for analysis |
| `job_state` | State extracted from Location |
| `same_state` | Binary: Is job location == HQ? |
| `job_simp` | Simplified job title |
| `desc_len` | Length of job description |
| Skill flags | Binary columns for Python, SQL, ML, etc. |

---

## 📊 Key Visualizations & Insights

### ⭐ Company Ratings Distribution
- Distribution is **slightly right-skewed** — most companies cluster between **3.0 and 4.0** on Glassdoor
- The modal rating sits around **3.5**, suggesting most companies are perceived as "decent but not exceptional"
- Very high ratings (4.5+) are rare, suggesting Glassdoor reviewers lean critical

### 💰 Salary Analysis

#### By Job Role
- **Data Scientists and Machine Learning Engineers** command the highest average salaries
- **DevOps and Software Engineers** follow, with significant variance driven by experience level and company size
- Junior roles (OJT/Entry-level equivalent) show tighter salary bands

#### By Location
- **San Francisco** and **New York** show premium salary clusters well above national averages
- **Austin** and **Seattle** represent competitive mid-tier markets gaining ground
- Geographic salary disparity remains significant — same title, different state = potentially $20K–$40K difference

#### By Company Size
- Larger companies (5000+ employees) generally offer **higher base salaries**
- Smaller firms show more **salary variability**, compensating with equity or culture premiums

#### By Sector
- **Finance, IT, and Consulting** sectors show the broadest salary spreads
- Healthcare and Government sectors cluster at lower medians with less variability
- **Violin plots** reveal that salary distributions are rarely symmetric — most are skewed or multimodal

### 🏢 Industry & Sector Demand
- **IT and Business Services** dominate job posting counts
- Healthcare is a growing sector for analytical and data roles
- Countplots show sharp demand concentration in a few sectors — **specialization pays**

### 🔗 Correlation Analysis
- **Weak correlations** between rating and salary — a highly-rated company doesn't necessarily pay more
- Job description length shows **minimal salary predictive power**
- `same_state` flag reveals companies hiring outside HQ tend to offer slightly higher packages

---

## 🛠️ Tech Stack

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import warnings
```

| Library | Purpose |
|---|---|
| Pandas & NumPy | Data transformation & feature engineering |
| Matplotlib | Histograms, bar charts, box plots |
| Seaborn | Violin plots, heatmaps, countplots, pair plots |

---

## 📁 Project Structure

```
Glassdoor-EDA/
├── Glassdoor_EDA_By_Ashwin_Suryawanshi.ipynb
├── glassdoor_jobs.csv
└── README.md
```

---

## 🔍 Analysis Workflow

```
Raw Data → Feature Engineering (Salary Parsing, Skill Flags)
    → Univariate Analysis (Ratings, Salary Distribution)
    → Bivariate Analysis (Salary vs Role, Salary vs Location, Rating vs Sector)
    → Multivariate Analysis (Sector + Size + Salary, Skill + Role + Pay)
    → Business Recommendations → Conclusion
```

---

## 💡 Business Recommendations

### For Employers
- **Move beyond simplistic salary benchmarks** — description length and company rating are poor salary predictors; use role complexity and market surveys instead
- **Offer total compensation packages** — benefits, equity, and WLB often outweigh base salary in candidate decision-making
- **Maintain internal pay equity** — regular salary audits prevent quiet dissatisfaction and attrition

### For Job Seekers
- **Location is a lever** — targeting SF or NY for the same role can yield 20–30%+ higher compensation
- **Sector matters more than company size** — Finance and IT outperform other sectors even at similar headcounts
- **Skill stacking pays** — postings requiring Python + SQL + ML/DL tools consistently cluster at higher salary bands

### Key KPIs to Monitor
- Time-to-hire | Employee satisfaction scores | Turnover rate | Cost-per-hire | Quality-of-hire

---

## 🏁 Conclusion

This EDA project surfaces critical patterns in the modern hiring landscape. The findings demonstrate that salary is a complex function of **role, location, sector, and company scale** — and that simple correlations with rating or description length are misleading. By leveraging these data-driven insights, both job seekers and employers can make smarter, evidence-backed decisions in a competitive talent environment.

---

## 👨‍💻 Author

**Ashwin Suryawanshi**
*EDA Capstone Project — Individual Contribution*

---

## 📜 License

This project is for educational and analytical purposes only.
