# 🛒 Customer Shopping Behavior Analysis

> A full-stack data analytics project covering exploratory data analysis, SQL querying, Power BI dashboarding, and executive reporting — built to uncover actionable insights from retail shopping data.

---

## 📌 Overview

This project analyzes a **Customer Shopping Behavior** dataset to identify purchasing patterns, segment customers, and surface business insights relevant to retail strategy. The workflow spans Python-based EDA, relational database querying across PostgreSQL/MySQL/SQL Server, an interactive Power BI dashboard, a structured analytical report, and a recruiter-ready presentation built in Gamma.

**Key Business Questions Answered:**
- Who are the most valuable customer segments?
- What products and categories drive the most revenue?
- How does shopping behavior vary by age, gender, and location?
- What seasonal or frequency-based trends exist?

---

## 📂 Dataset

| Field | Details |
|---|---|
| **Source** | [Customer Shopping Behavior Dataset – Kaggle / GitHub](https://github.com/amlanmohanty1/customer_behavior) |
| **Format** | CSV |
| **Records** | ~3,900 rows |
| **Key Columns** | `Customer ID`, `Age`, `Gender`, `Item Purchased`, `Category`, `Purchase Amount (USD)`, `Location`, `Season`, `Review Rating`, `Subscription Status`, `Payment Method`, `Frequency of Purchases` |

---

## 🛠️ Tools & Technologies

| Layer | Tool |
|---|---|
| Data Loading & EDA | Python (Pandas, Matplotlib, Seaborn) |
| Database Querying | PostgreSQL / MySQL / SQL Server |
| Dashboard | Power BI |
| Report | PDF / Word (structured analytical report) |
| Presentation | Gamma (AI-powered PPT) |
| Version Control | Git & GitHub |

---

## 🔄 Steps

### 1. 📥 Data Loading & Cleaning (Python)

```python
import pandas as pd

df = pd.read_csv('customer_shopping_behavior.csv')
df.info()
df.isnull().sum()
df.drop_duplicates(inplace=True)
df['Purchase Amount (USD)'] = df['Purchase Amount (USD)'].astype(float)
```

- Loaded dataset using **Pandas**
- Checked for null values and duplicates
- Standardized column data types
- Encoded categorical variables where needed

---

### 2. 🔍 Exploratory Data Analysis (EDA)

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Purchase distribution by category
df.groupby('Category')['Purchase Amount (USD)'].sum().plot(kind='bar')
plt.title('Total Revenue by Category')
plt.show()

# Age distribution
sns.histplot(df['Age'], bins=20, kde=True)
```

Key analyses performed:
- Distribution of purchase amounts
- Revenue by product category and gender
- Seasonal purchase trends
- Customer segmentation by subscription status
- Review rating analysis

---

### 3. 🗄️ SQL Analysis (PostgreSQL / MySQL / SQL Server)

```sql
-- Top 5 highest spending customers
SELECT customer_id, SUM(purchase_amount_usd) AS total_spent
FROM shopping_behavior
GROUP BY customer_id
ORDER BY total_spent DESC
LIMIT 5;

-- Revenue by season
SELECT season, ROUND(SUM(purchase_amount_usd), 2) AS revenue
FROM shopping_behavior
GROUP BY season
ORDER BY revenue DESC;

-- Subscription vs non-subscription average spend
SELECT subscription_status, ROUND(AVG(purchase_amount_usd), 2) AS avg_spend
FROM shopping_behavior
GROUP BY subscription_status;
```

Queries covered:
- Aggregations by category, season, and location
- Customer lifetime value approximations
- Segmentation by subscription status and frequency
- Top-performing products and regions

---

### 4. 📊 Power BI Dashboard

The interactive dashboard includes:

- **KPI Cards** – Total Revenue, Avg Purchase Value, Total Customers
- **Bar Charts** – Revenue by Category, Top Items by Sales
- **Donut Charts** – Gender split, Subscription Status breakdown
- **Map Visual** – Purchase distribution by US State/Location
- **Slicers** – Season, Category, Gender, Subscription Status

> 📁 File: `Customer_Shopping_Dashboard.pbix`

---

### 5. 📝 Report

A structured analytical report was created summarizing:

- Executive Summary
- Data Overview & Cleaning Notes
- Key Findings from EDA and SQL
- Business Recommendations
- Appendix (charts and query outputs)

> 📁 File: `Customer_Shopping_Report.pdf`

---

### 6. 🎞️ Presentation (Gamma)

A clean, recruiter-friendly slide deck built using **Gamma** covering:

1. Project Overview
2. Dataset Summary
3. Tools Used
4. Key Insights
5. Dashboard Walkthrough
6. Business Recommendations
7. Conclusion

> 🔗 [View Presentation](#) *(link to Gamma deck)*

---

## 📈 Results & Key Insights

- 🏆 **Clothing** is the highest revenue-generating category, followed by Accessories
- 👩 **Female customers** have a slightly higher average purchase value than male customers
- ❄️ **Winter** season sees the highest total purchases across all categories
- 💳 **Subscribed customers** spend ~23% more on average than non-subscribers
- 📍 **Montana, Illinois, and California** are top-performing states by revenue

---

## ▶️ How to Run

### Prerequisites

```bash
pip install pandas matplotlib seaborn jupyter
```

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/amlanmohanty1/customer_behavior.git
   cd customer_behavior
   ```

2. **Run the Jupyter Notebook**
   ```bash
   jupyter notebook EDA_Customer_Shopping.ipynb
   ```

3. **Import SQL scripts**
   - Open MySQL Workbench / pgAdmin / SQL Server Management Studio
   - Run `schema.sql` to create the table
   - Run `queries.sql` for all analytical queries

4. **Open the Power BI file**
   - Open `Customer_Shopping_Dashboard.pbix` in Power BI Desktop
   - Refresh data source if needed

---

## 📁 Project Structure

```
customer_behavior/
│
├── data/
│   └── customer_shopping_behavior.csv
│
├── notebooks/
│   └── EDA_Customer_Shopping.ipynb
│
├── sql/
│   ├── schema.sql
│   └── queries.sql
│
├── dashboard/
│   └── Customer_Shopping_Dashboard.pbix
│
├── report/
│   └── Customer_Shopping_Report.pdf
│
├── presentation/
│   └── Customer_Shopping_Gamma.pdf
│
└── README.md
```

---



## 📄 License

This project is for educational and portfolio purposes. Dataset sourced from publicly available Kaggle/GitHub repositories.
