📊 Digital Trust Score for Online Donations & NGO Programs
🔍 Project Overview

When people donate online, they usually judge NGOs or donation programs based on total funds raised or emotional appeal.
However, trust — the most critical factor — is rarely measured quantitatively.

This project introduces a Digital Trust Score, a data-driven metric that evaluates how trustworthy a donation program is based on real donor behavior, not just money collected.

🎯 Problem Statement

There is no standardized way to measure trustworthiness of donation programs using data.
Key questions remain unanswered:

Do donors return after donating once?

Are donations stable or highly volatile?

Which programs show consistent donor confidence over time?

Objective:
To design an explainable Trust Score (0–100) that reflects donor trust using behavioral and financial signals.

📁 Dataset

The project uses a Kaggle fundraising dataset consisting of multiple tables.
The primary table used is:

giving.csv → donation transaction data

Gift amount

Gift date

Donor ID

Designation (program/fund)

Other CRM-style tables were intentionally excluded to keep the analysis focused on trust-related signals.

🧠 Key Assumption

Since NGO-level identifiers were not available, trust is modeled at the “Designation” level, where:

Designation = Donation Program / Fund / Purpose

Each designation is treated as an independent trust unit

This reflects real-world donor behavior, where trust is built around specific programs, not abstract organizations.

🔎 Exploratory Data Analysis (EDA)

EDA was performed to understand donor behavior and identify trust signals, including:

Donation amount distribution and outliers

Donation frequency and volatility

Repeat vs one-time donors

Donor drop-off patterns

Time-based donation trends

EDA insights guided the definition of trust and feature selection.

🛠️ Feature Engineering

From raw donation transactions, the following trust-related features were engineered:

Retention Rate
Percentage of donors who donated again in the recent period (last 6 months)

Donation Volatility Ratio
Measures stability of donation amounts
(standard deviation / mean donation)

Total Amount Raised
Used as contextual information, not as a standalone trust signal

All features were aggregated at the designation (program) level.

🧮 Trust Score Design

To make trust measurable and comparable:

All features were normalized to a 0–100 scale

Business-driven weights were applied

A composite Trust Score was calculated

Trust Score Logic (Simplified):

Higher donor retention → higher trust

Lower donation volatility → higher trust

Stable, repeat donations → higher trust

Each program is categorized into:

High Trust

Medium Trust

Low Trust

📊 Final Dataset

The final engineered dataset is:

trust_score_final.csv

Columns:
Column	Description
designation	Donation program / fund
trust_score	Composite trust score (0–100)
trust_band	High / Medium / Low Trust
retention_rate	Donor retention metric
volatility_ratio	Donation stability indicator
total_amount	Total funds raised (contextual)

Each row represents one donation program.

🌐 Deployment

The project is deployed as an interactive Streamlit application that allows users to:

View trust scores across programs

Select a program and understand why it has a certain trust score

Compare programs visually

Tech Stack:

Python

Pandas

Streamlit

CSV-based analytics pipeline

💡 Key Insights

High fundraising totals do not always imply high trust

Donor retention is a strong indicator of trust

Donation ecosystems naturally have lower retention due to one-time donors

Trust must be measured behaviorally, not emotionally

⚠️ Limitations

Retention is defined using recent activity due to lack of churn labels

Dataset does not include real-time donor intent

NGO-level aggregation was not possible due to data constraints

These limitations are explicitly acknowledged and documented.

🚀 Future Improvements

Cohort-based retention analysis

6-month vs 12-month retention comparison

NGO-level trust aggregation

User-uploaded datasets in the Streamlit app

Sensitivity analysis on Trust Score weights

🧠 One-Line Summary

Built a data-driven Digital Trust Score that transforms donor behavior and funding stability into an explainable trust metric for online donation programs.
