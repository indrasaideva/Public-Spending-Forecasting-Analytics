📊 Fiscal Risk in Europe
Clustering, Resilience, and Forecasting

📌 Project Overview

This project builds an interpretable fiscal risk framework for European countries using official government finance data from Eurostat 


We combine:

Fiscal ratio construction

Machine learning clustering

Crisis resilience measurement

Composite risk scoring

Interactive visualizations

Time-series forecasting

The goal is to move beyond raw debt numbers and build a structured, data-driven fiscal risk model that explains:

Which countries are fiscally stable?

Which are structurally vulnerable?

How did countries react during major crises?

What do current fiscal dynamics suggest for the future?

🎯 Objectives

Clean and transform raw Eurostat government finance data

Construct core fiscal metrics (Debt, Deficit, Growth)

Cluster countries by fiscal behavior

Measure fiscal shock resilience (GFC + COVID)

Build a composite fiscal risk score

Visualize fiscal risk across Europe

Demonstrate forecasting using ARIMA and VAR

🗂 Data Source

Primary dataset:

Eurostat Government Finance Statistics
Dataset: GOV_10DD_EDPT1 

Fiscal Risk in Europe_ Clusteri…

Variables extracted:

GDP (B1GQ)

Government Debt (GD)

Net Lending/Borrowing (B9) → treated as fiscal deficit

🔧 Methodology
1️⃣ Data Cleaning & Transformation

Eurostat provides data in wide, multi-dimensional TSV format.
We:

Split dimensions from metadata column

Removed EU aggregates

Converted years into panel format

Cleaned missing and flagged values

Reshaped into country–year panel

Output: Clean fiscal panel dataset

2️⃣ Core Fiscal Metrics

For each country-year observation:

Debt-to-GDP (%)

Deficit-to-GDP (%)

Annual Debt Growth (%)

These metrics capture:

Structural debt burden

Fiscal discipline

Dynamic debt acceleration

3️⃣ Clustering Fiscal Behavior (K-Means)

We applied:

StandardScaler

K-Means (k=3)

Features used:

Debt-to-GDP

Deficit-to-GDP

Debt Growth

Clusters represent:

Cluster Type	Interpretation
Stable	Low debt, moderate deficits
Moderate Risk	High structural debt
High Risk	High deficit volatility / rapid debt growth

This creates a behavioral classification instead of ranking countries by one variable.

4️⃣ Fiscal Shock Resilience Index

We analyze fiscal response during:

Global Financial Crisis (2008–2009)

COVID Shock (2020–2021)

We compute:

Average crisis deficit ratio

Delta vs. pre-crisis baseline

Interpretation:

Larger deterioration = weaker fiscal resilience

Controlled deterioration = stronger structural resilience

5️⃣ Composite Fiscal Risk Score

We combine three normalized components:

Average Debt-to-GDP

Deficit Volatility

Crisis Deficit Magnitude

All components are MinMax scaled and equally weighted.
Fiscal Risk Score=
Debt+Volatility+Crisis/3
	​
Higher score → Higher fiscal vulnerability.

🗺 Visualizations
🇪🇺 Europe Choropleth

Displays Fiscal Risk Score by country

Red → Higher risk

Green → Lower risk

Europe-only scope

📈 Executive Bubble Chart

X-axis: Average Debt-to-GDP
Y-axis: Deficit Volatility
Bubble size: Average GDP Growth
Color: Fiscal Risk Score

This visualization provides a policy-level overview of structural position.

🔮 Forecasting Module (Demonstration)

We include a forecasting component for a selected country:

ARIMA Model

Forecasts Debt-to-GDP time series
Used for short-term projection

VAR Model

Joint modeling of:

Debt-to-GDP

Deficit-to-GDP

GDP Growth

Purpose:

Demonstrate macro-fiscal interdependence

Show dynamic interactions

Note:
Forecasting is illustrative — not part of the core risk score

📊 Key Insights

High debt alone does not define risk.

Volatility and crisis sensitivity matter significantly.

Some moderate-debt countries display higher instability.

Fiscal behavior clusters reveal structural differences.

Crisis response provides an additional resilience dimension.

Forecasting shows persistence in fiscal dynamics.

🧠 What This Project Demonstrates

This project integrates:

Economic reasoning

Panel data engineering

Machine learning clustering

Composite index construction

Macroeconomic interpretation

Forecasting models

Policy-relevant visualization

It reflects applied skills in:

Data cleaning

Feature engineering

Model interpretation

Risk quantification

Executive communication

🚀 How to Run

Install dependencies:

pandas

numpy

sklearn

statsmodels

matplotlib

plotly

Load Eurostat TSV file.

Run notebook sequentially from setup to forecasting.
