# Customer Shopping Behavior Analysis

## Overview
This project analyzes retail customer shopping behavior to help a company understand purchasing patterns, customer segments, and the factors that drive sales and loyalty. The goal is to answer one core business question:

> **How can the company leverage consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategies?**

The project covers the full analytics workflow — from raw data to a business-ready presentation — using Python, SQL, and Power BI.

## Dataset
- **Source file:** `customer_shopping_behavior.csv`
- **Size:** 3,900 rows × 18 columns
- **Key fields:**
  - **Demographics:** Age, Gender, Location
  - **Purchase details:** Item Purchased, Category, Purchase Amount, Season, Size, Color
  - **Shopping behavior:** Discount Applied, Promo Code Used, Previous Purchases, Frequency of Purchases, Review Rating, Shipping Type, Payment Method, Subscription Status
- **Data quality notes:** 37 missing values in the Review Rating column, later imputed using category-level medians.

## Tools & Technologies
| Purpose | Tool |
|---|---|
| Data cleaning & EDA | Python (pandas) |
| Database & querying | PostgreSQL (via SQLAlchemy + psycopg2) |
| Dashboard & visualization | Power BI |
| Report | PDF / Word document |
| Presentation | Gamma (AI-generated PPT) |

## Project Steps

### 1. Data Preparation (Python)
- Loaded the raw CSV using pandas.
- Explored structure and summary statistics with `df.info()` and `df.describe()`.
- Imputed missing Review Ratings using the median rating per product category.
- Standardized column names to snake_case.
- Engineered new features: `age_group` (binned ages) and `purchase_frequency_days`.
- Checked for redundancy between `discount_applied` and `promo_code_used`, and dropped the redundant column.
- Connected to PostgreSQL and loaded the cleaned dataset into a database table for SQL analysis.

### 2. Data Analysis (SQL / PostgreSQL)
Ran structured queries to answer key business questions, including:
- Revenue by gender
- High-spending customers who still used discounts
- Top 5 products by average review rating
- Standard vs. Express shipping — average spend comparison
- Subscribers vs. non-subscribers — spend and revenue comparison
- Discount-dependent products (highest % of discounted purchases)
- Customer segmentation (New, Returning, Loyal)
- Top 3 products per category
- Repeat buyers vs. subscription status
- Revenue by age group

### 3. Dashboard (Power BI)
Built an interactive dashboard (`customer-behavior-dashboard.pbix`) with filters for Subscription Status, Gender, Category, and Shipping Type, featuring:
- Key metrics: number of customers, average purchase amount, average review rating
- Revenue and sales breakdown by category
- Revenue and sales breakdown by age group
- Subscriber vs. non-subscriber split

### 4. Report & Presentation
- Compiled findings into a written report (`Customer_Shopping_Behavior_Analysis.pdf`) summarizing the methodology, SQL results, and dashboard insights.
- Created a stakeholder-facing presentation (`Customer_Shopping_Behavior_Analysis.pptx`) using Gamma to visually communicate insights and recommendations.

## Key Results & Insights
- **Male customers generated significantly more revenue** than female customers overall.
- **Loyal customers made up the majority of the base** (3,116 of 3,900), with only 83 classified as new.
- **Express shipping customers spent slightly more on average** ($60.48) than Standard shipping customers ($58.46).
- **Non-subscribers generated more total revenue** than subscribers, despite subscribers having a similar average spend — pointing to a large opportunity to convert casual buyers into subscribers.
- **Hats, Sneakers, and Coats were the most discount-dependent products**, each with close to 50% of purchases involving a discount.
- **Young Adults contributed the highest revenue** among age groups, followed closely by Middle-aged and Adult segments.

## Business Recommendations
- **Boost subscriptions** by promoting exclusive member benefits.
- **Build loyalty programs** to convert Returning customers into Loyal ones.
- **Review discount policy** to balance sales growth with profit margins, especially for discount-dependent products.
- **Highlight top-rated and best-selling products** (e.g., Gloves, Sandals, Boots) in marketing campaigns.
- **Target high-revenue age groups and Express-shipping users** with focused marketing efforts.

## How to Run This Project

### Prerequisites
- Python 3.x with `pandas` and `sqlalchemy` (and `psycopg2`) installed
- PostgreSQL server installed and running
- Power BI Desktop (to open the `.pbix` file)

### Steps
1. **Clone the repository** and ensure `customer_shopping_behavior.csv` is in the project folder.
2. **Run the Python notebook** (`Customer-Shopping-Behavior-Analysis.ipynb`) to clean the data and load it into PostgreSQL:
   ```bash
   jupyter notebook Customer-Shopping-Behavior-Analysis.ipynb
   ```
   Update the database credentials (username, password, host, port, database name) in the connection cell before running.
3. **Run the SQL queries** against the `customer` table in PostgreSQL to reproduce the analysis (see the Report for full query list).
4. **Open the Power BI dashboard** (`customer-behavior-dashboard.pbix`) in Power BI Desktop and refresh the data connection if needed.
5. **Review the Report and Presentation** (`Customer_Shopping_Behavior_Analysis.pdf` and `.pptx`) for the full write-up and stakeholder summary.

## Repository Structure
```
├── customer_shopping_behavior.csv                 # Raw dataset
├── Customer-Shopping-Behavior-Analysis.ipynb       # Python: cleaning, EDA, DB load
├── customer-behavior-dashboard.pbix                # Power BI dashboard
├── Customer_Shopping_Behavior_Analysis.pdf          # Written report
├── Customer_Shopping_Behavior_Analysis.pptx         # Stakeholder presentation (Gamma)
├── Business_Problem_Document.pdf                    # Original business problem brief
└── README.md                                        # Project documentation
```

## Author
Thabeeb — Business Analyst & Data Analyst
