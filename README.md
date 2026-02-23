# 🇪🇺 Fiscal Risk in Europe: Clustering, Resilience & Forecasting

> An end-to-end fiscal risk analytics framework for 27 European countries using 25+ years of official Eurostat government finance data (1995–2024).

---

## 📌 Overview

This project builds a transparent, reproducible, and policy-relevant **fiscal risk intelligence framework** for European economies. It combines panel data engineering, unsupervised machine learning, shock resilience analysis, composite scoring, and time-series forecasting into a unified analytical pipeline — culminating in interactive executive visualizations.

The framework answers five core research questions:

1. Can European countries be meaningfully grouped by fiscal behavior?
2. How resilient are governments to major fiscal shocks (GFC, COVID-19)?
3. Can a composite fiscal risk score integrate multiple dimensions of vulnerability?
4. What does the geographic distribution of fiscal risk reveal about European integration?
5. Can time-series models forecast near-term fiscal trajectories for individual countries?

---

## 📊 Key Outputs

| Output | Description |
|--------|-------------|
| **Panel Dataset** | Clean long-format dataset: Debt-to-GDP, Deficit-to-GDP, Debt Growth (27 countries × 30 years) |
| **Country Clusters** | K-Means segmentation into Stable / Moderate Risk / High Risk fiscal regimes |
| **Resilience Index** | Shock Response Index measuring deficit deterioration during GFC & COVID |
| **Fiscal Risk Score** | Composite normalized score combining debt level, deficit volatility, and crisis sensitivity |
| **Choropleth Map** | Interactive Europe map colored by fiscal risk score |
| **Bubble Chart** | Executive visualization: Debt-to-GDP vs. Deficit Volatility vs. GDP size |
| **ARIMA Forecast** | AIC-optimized univariate debt forecast with 95% confidence intervals + rolling backtest |
| **VAR Model** | Multivariate forecast of Debt, Deficit, and GDP Growth jointly |

---

## 🗂️ Project Structure

```
├── Fiscal_Risk_Europe_Complete.ipynb   # Main analysis notebook
├── Report-and-Visualizations-of-Fiscal-Risk-Project.pdf     # Pdf Report of the Project
├── Report and Visualizations of Fiscal Risk Project.html     # RevealJs Presentation of the Project
├── fiscal_data_exports/
│   └── estat_gov_10dd_edpt1.tsv        # Raw Eurostat TSV data
│   
└── README.md
```

---

## 🔬 Methodology

### 1. Data Pipeline
- Source: [Eurostat Government Finance Statistics](https://ec.europa.eu/eurostat/databrowser/product/page/GOV_10DD_EDPT1)
- Indicators extracted: GDP (`B1GQ`), Government Debt (`GD`), Net Lending/Borrowing (`B9`)
- Strict filtering: annual frequency, general government sector (`S13`), monetary units (`MIO_EUR`)
- Reshaped from wide TSV format into a clean long-format panel

### 2. Fiscal Metrics Engineering
- **Debt-to-GDP** = Government Debt / GDP × 100
- **Deficit-to-GDP** = Net Lending / GDP × 100 *(negative = deficit)*
- **Debt Growth** = Year-on-year % change in government debt

### 3. K-Means Clustering (k=3)
- Features standardized with `StandardScaler`
- Optimal k selected via Elbow Method + Silhouette Score
- Clusters labeled: **Stable**, **Moderate Risk**, **High Risk**

### 4. Shock Resilience Index
- Crisis years: 2008, 2009 (GFC) and 2020, 2021 (COVID-19)
- Metric: average deficit-to-GDP during crisis years vs. pre-crisis baseline
- More negative = stronger deficit deterioration = less resilient

### 5. Composite Fiscal Risk Score
- Three equal-weighted normalized components (Min-Max scaled):
  - Average Debt-to-GDP
  - Deficit Volatility (standard deviation)
  - Crisis Deficit Magnitude
- Higher score → higher fiscal risk

### 6. Time-Series Forecasting (Demo: Germany)
- **ARIMA**: AIC grid search over p∈[0,3], d∈[0,1], q∈[0,3] + rolling-origin backtest
- **VAR**: Differenced trivariate model (Debt, Deficit, GDP Growth) with AIC lag selection and stability check

---

## 📈 Key Findings

- **Fiscal divergence is structural, not cyclical** — cluster membership persists across 30 years, reflecting deep institutional and demographic differences
- **North–South risk gradient** — Greece, Italy, Portugal, Belgium consistently score highest; Luxembourg, Denmark, Sweden lowest
- **Crises amplify existing gaps** — high-debt countries experienced far greater and longer-lasting deficit deterioration during both the GFC and COVID
- **Forecasting is feasible but uncertain around shocks** — ARIMA tracks broad debt trajectories well; VAR reveals interdependencies between growth, deficits, and debt accumulation

---

## 🛠️ Requirements

```bash
pip install pandas numpy scikit-learn statsmodels plotly matplotlib scipy pyyaml nbformat nbclient ipykernel
```

---

## ▶️ How to Run

**In Google Colab (recommended):**
- Open `Fiscal_Risk_Europe_Complete.ipynb` directly in Colab and run all cells

**Locally with Jupyter:**
```bash
jupyter notebook Fiscal_Risk_Europe_Complete.ipynb
```

**Render with Quarto:**
```bash
# HTML report
quarto render Fiscal_Risk_Europe_Complete.qmd --to html

# PDF
quarto render Fiscal_Risk_Europe_Complete.qmd --to pdf

# RevealJS slides
quarto render Fiscal_Risk_Europe_Complete.qmd --to revealjs
```

---

## 📚 Data Source

**Eurostat — Government Finance Statistics**  
[estat_gov_10dd_edpt1](https://ec.europa.eu/eurostat/databrowser/product/page/GOV_10DD_EDPT1)  
Coverage: EU Member States, 1995–2024, Annual frequency

---

## 👤 Author

**Athikarathparambil Surjith Indra Prasad**  
[GitHub](https://github.com/indrasaideva) · [Repository](https://github.com/indrasaideva/Fiscal-Risk-in-Europe-Clustering-Resilience-and-Forecasting)
