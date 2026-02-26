# 📊 Systematic Risk and Idiosyncratic Volatility Dynamics  
## US Mid-Cap (S&P 400) vs Indian Large-Cap (Nifty 100) Across Crisis Regimes

**Authors:** Gabriele Alberto, Mohammed El-Zein
**Institution:** Grenoble Ecole de Management  
**Course:** Research Methods  
**Date:** February 2026  

---

## 🔎 Project Overview

This project investigates how **systematic risk (beta)** and **idiosyncratic volatility (IVOL)** behave across crisis and normal regimes in:

- 🇺🇸 **S&P 400 Mid-Cap (US)**
- 🇮🇳 **Nifty 100 (India)**

The analysis uses:

- Rolling 252-day CAPM estimation  
- AR(10) models with crisis dummies  
- Newey-West HAC standard errors  
- Regime-dependent correlation analysis  
- IQR-based outlier detection  

The sample period spans **2007–2025**, covering:

- Global Financial Crisis (2008–2009)  
- European Debt Crisis (2011–2012)  
- COVID-19 Pandemic (2020)  
- Inflation & Rate Hike Cycle (2022–2023)

The full academic paper is included in the repository.

---

## 🧠 Research Question

> How do systematic risk and idiosyncratic volatility dynamics differ between developed and emerging markets during global financial crises?

---

## 📂 Repository Structure

```bash
.
├── Research_methods_data_cleaning.ipynb
├── Rates_&_Merge_S&p400.ipynb
├── Rates_&_Merge_Nifty100.ipynb
├── Final_program.ipynb
│
├── SP400_Ready_Data.csv
├── Nifty100_Ready_Data.csv
│
├── MSCI_World.csv
├── MSCI_World_cleaned.csv
├── Exchange_rate_hist.csv
├── s&p_400_Mid.csv
├── Nifty_100_Mid_cleaned_USD.csv
│
├── Final_Paper_Research_Methods.pdf
├── Project_Execution_Guide.pdf
└── README.md
```


---

## ⚙️ Methodology

### 1️⃣ Data Cleaning

Notebook:

Research_methods_data_cleaning.ipynb


Main operations:

- Date standardization  
- Sorting and alignment of time series  
- Linear interpolation of missing values  
- INR → USD conversion for Nifty 100  
- Log return computation  
- Risk-free rate construction (DTB3)  
- Calendar synchronization between US and India  

---

### 2️⃣ Market-Specific Construction

Run separately:


Rates_&Merge_S&p400.ipynb
Rates&_Merge_Nifty100.ipynb


Each notebook:

- Merges index returns with:
  - MSCI World (global market proxy)
  - US 3M Treasury Bill (risk-free rate)
- Exports final datasets:


SP400_Ready_Data.csv
Nifty100_Ready_Data.csv


---

### 3️⃣ Final Econometric Analysis

Notebook:

Final_program.ipynb


Performs:

- Alignment of US and India datasets  
- Crisis vs Normal regime split  
- AR(p) lag selection (AIC, BIC, HQIC, Ljung-Box)  
- AR(10) estimation on ΔIVOL and ΔTotal Volatility  
- Newey-West HAC standard errors  
- Correlation matrices (regime dependent)  
- IQR-based outlier detection  
- Generation of all tables and figures from the paper  

---

## 🔁 Full Reproduction Order

To fully reproduce the analysis:

1. `Research_methods_data_cleaning.ipynb`  
2. `Rates_&_Merge_S&p400.ipynb`  
3. `Rates_&_Merge_Nifty100.ipynb`  
4. `Final_program.ipynb`  

Alternatively:

You can run `Final_program.ipynb` directly if:


SP400_Ready_Data.csv
Nifty100_Ready_Data.csv


are already in the same directory.

---

## 📈 Key Results

- 🇺🇸 S&P 400 shows **lower baseline IVOL** but **higher crisis sensitivity (+32.54%)**
- 🇮🇳 Nifty 100 shows **higher unconditional IVOL**, but smaller relative crisis amplification (+15.75%)**
- Cross-market IVOL correlation remains high during crises (~0.76)
- US beta extremely stable (0 outliers)
- India beta time-varying (116 outliers)
- Indian market experiences nearly double extreme IVOL events

---

## 📊 Econometric Specifications

### Rolling CAPM

\[
(R_i - R_f)_t = \alpha_t + \beta_t (R_g - R_f)_t + \epsilon_t
\]

Window length: 252 trading days

---

### AR(10) Crisis Model

\[
\Delta Y_t = \gamma_0 + \sum_{j=1}^{10} \phi_j \Delta Y_{t-j} + \delta \cdot Crisis_t + \epsilon_t
\]

Where:

- \( Y_t \) = IVOL or Total Volatility  
- HAC Newey-West standard errors are applied  

---

## 🧪 Statistical Tools Used

- Rolling OLS  
- Augmented Dickey-Fuller tests  
- AIC / BIC / HQIC  
- Ljung-Box test  
- Newey-West HAC correction  
- Pearson correlations  
- IQR outlier detection  

---

## 💻 Technologies

- Python 3.x  
- pandas  
- numpy  
- statsmodels  
- matplotlib  
- scipy  

---

## 📌 Important Notes

- Nifty 100 returns are USD-denominated → embedded FX volatility.
- Forbes-Rigobon contagion correction is discussed but not implemented.
- Crisis periods are calendar-based and not endogenously estimated.
- Analysis is index-level, not firm-level.

---

## 🔬 Possible Extensions

- Implement Forbes-Rigobon correction  
- Markov regime-switching models  
- Multi-factor models (Fama-French extensions)  
- Currency-hedged decomposition  
- Firm-level or sector-level analysis  

---

## 📜 Citation

If referencing this project:

Alberto, G., El-Zein, M. (2026).  
*Systematic Risk and Idiosyncratic Volatility Dynamics: A Comparative Analysis of US Mid-Cap and Indian Equities Across Crisis Regimes.*

---

## 👤 Author

**Gabriele Alberto**  
MSc Finance  
Grenoble Ecole de Management  

---

⭐ If you found this project interesting, feel free to star the repository.
