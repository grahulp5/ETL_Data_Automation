# ETL_Data_Automation

# 🛍️ US Sales Data Generation & Enrichment Pipeline

### 📊 Case Study Submission – Rahul Gupta

---

## 📌 Overview

This project is a dynamic data pipeline developed in Python to simulate, update, and manage synthetic sales data for US-based retail shampoo products. The solution was developed as part of a case study to evaluate data generation, enrichment, logging, and data integrity validation capabilities.

It includes:
- Synthetic data generation using the `Faker` library
- Monthly sales data automation
- Integration of macroeconomic indicators (Gas Prices and CPI) using the `FRED API`
- Logging of key processing steps
- Integrity checks for critical fields
- Output as monthly CSVs and a master historical dataset

---

## 🚀 Execution Instructions

> ⚙️ This solution is built using Python and is fully compatible with **Jupyter Notebook** or **Google Colab**.

1. **Install Required Libraries**
   ```bash
   !pip install fredapi
   !pip install Faker

## Folder Structure

.
├── US_Historical_Sales.csv            # Master historical dataset
├── US_Monthly_Sales_Month_Year.csv   # Monthly sales files
├── data_check_log.txt            # Auto-generated log file
├── CaseStudy_Documentation.docx      # Professional documentation
├── CaseStudy_SalesPipeline.ipynb     # Python Notebook file
└── README.md                         # Project readme

Execution Steps
Open the CaseStudy_SalesPipeline.ipynb notebook in Jupyter or Google Colab.

Run all cells from top to bottom.

Outputs will be generated in the specified folder:

Monthly sales CSV files

Master sales file

Log file: TESTdata_check_log.txt

To generate data for the next month, simply re-run the notebook when a new month starts.

🔍 Approach Summary
This pipeline simulates realistic weekly retail sales data and manages it month-over-month. Here's the step-by-step breakdown:

🧩 Initialization Check
If US_Historical_Sales.csv does not exist:

Create synthetic data for Jan–Dec 2024 using Faker.

Else:

Load the master file.

Detect the latest generated month using filenames.

📊 Data Generation
Create weekly sales data using W-SUN frequency.

Each entry includes:

50 SKUs

Base pricing ($4–$15), random discounts (0–20%)

Units sold impacted by seasonality and promotions

Revenue = units × discounted price

🌐 Economic Enrichment
Use fredapi to pull:

Weekly average gas prices (GASREGW)

Weekly Consumer Price Index (CPIAUCSL)

Both are forward-filled and resampled to weekly (Sunday-based)

Merged with the weekly sales dataset

📅 Monthly File Logic
Scan existing files to determine latest month generated.

Generate data only if the next month has arrived.

Save new data as a monthly file and update the master file by removing duplicates.

🛡️ Logging & Data Integrity
Logs saved to:

Console

TESTdata_check_log.txt

Checks include:

Missing critical fields (week_start_date, product_id, etc.)

Missing economic indicators

Product count validation

🧠 Assumptions Made
🧭 Two Execution Scenarios
If US_Historical_Sales.csv is missing:

Generate full year synthetic data for 2024.

If it exists:

Begin monthly updates from Jan 2025 to current month.

🗓️ Monthly Update Check
Script scans US_Monthly_Sales_*.csv filenames.

If current month already exists, script skips regeneration.

🛒 Sales Simulation
Fixed SKUs: P001 to P050

Price range: $4 – $15

Discount range: 0% – 20%

Seasonality applied for summer and winter boosts

Weekly data ends every Sunday (W-SUN)

📈 Economic Enrichment
FRED series:

CPI (CPIAUCSL)

Gas prices (GASREGW)

Missing values filled forward to ensure completeness

🧾 Logging & Monitoring
Log files include step-by-step tracing

Integrity checks for:

Null fields

Sales/revenue anomalies

Missing economic indicators

Duplicate product IDs


✅ Features
🔁 Automatically detects and generates next month’s data

💡 Adds economic context with CPI & gas price data

📊 Weekly sales granularity with seasonality & discount simulation

🧹 Forward-fill and resample logic for clean CPI/gas price values

✅ Logs and checks for:

Missing values

Economic data anomalies

Sales inconsistencies

Product ID mismatches

📎 Files for Submission
File	Purpose
CaseStudy_SalesPipeline.ipynb	Jupyter/Colab executable version of the code
CaseStudy_Documentation.docx	Formal write-up of the solution
US_Historical_Sales.csv	Master file containing historical sales data
US_Monthly_Sales_*.csv	Monthly generated output files
TESTdata_check_log.txt	Logging output for traceability and validation
README.md	Project summary and instructions (you are reading this)

📘 Documentation Highlights
The .docx file CaseStudy_Documentation.docx includes:

✅ Execution instructions

🧠 Summary of logic and components

🔍 Key assumptions

📊 Sample output description

🧹 Logging and data integrity handling

📷 Visual placeholders and screenshots (optional)

