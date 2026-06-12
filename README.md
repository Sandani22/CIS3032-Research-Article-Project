# The Impact of Product Pricing Strategies on Online Purchase Decisions Using E-Commerce Data

This repository contains the empirical source code, datasets, visual analytics, and the final research article for the study completed under the Bachelor of Computing (Hons) in Information Systems program at the Faculty of Computing, University of Sri Jayewardenepura.

---

## 📌 Project Overview
[cite_start]This study investigates how product pricing tactics and web-resident value indicators jointly influence online purchase decisions[cite: 16]. [cite_start]E-commerce platforms routinely manipulate demand signals through traditional pricing mechanisms, yet the financial value embedded within a user's digital browsing environment remains a critical, understudied complement[cite: 27, 45, 51]. 

[cite_start]To bridge this gap, this research deploys a **dual-phase pipeline** connecting front-end session-level clickstream analytics with back-end customer transactional dynamics[cite: 38, 75].

### 🔬 Methodology Breakdown
* [cite_start]**Phase 1 (Clickstream Analytics):** Models session conversion behavior using the UCI Online Shoppers Purchasing Intention Dataset (12,330 user sessions)[cite: 17]. [cite_start]It leverages Logistic Regression for interpretability and coefficient extraction alongside Random Forest ensemble classification to handle severe class imbalances via SMOTE processing[cite: 17, 106, 114].
* [cite_start]**Phase 2 (Transactional Economics):** Analyzes macro-level transactional data using the UCI Online Retail Dataset (406,829 valid line items across 4,372 unique customers)[cite: 18, 92]. [cite_start]It uses K-Means clustering to partition the customer base into distinct value tiers based on Recency, Frequency, and Monetary (RFM) modeling, computing the Price Elasticity of Demand ($e$) within each segment via Ordinary Least Squares ($log-log$ linear regression)[cite: 18, 65, 117, 119].

---

## 📊 Key Findings

### Phase 1: Session Conversion Predictors
* [cite_start]**Dominant Feature:** `PageValues` (an estimated monetary indicator computed via server-side analytics tracking) is the single strongest predictor of session conversion[cite: 19, 86, 87]. [cite_start]It accounts for **37.9% of total predictive importance** in the Random Forest feature importance ranking[cite: 19].
* [cite_start]**Effect Size:** Logistic Regression yields a positive coefficient ($b = 0.074, p < 0.001$) for `PageValues`[cite: 135]. [cite_start]This corresponds to an **Odds Ratio (OR) of 1.077**, meaning every single-dollar increase in a page's value profile is associated with a **7.7% increase in the odds of session conversion**, holding all other variables constant[cite: 135, 136].
* [cite_start]**Classification Performance:** The Random Forest classifier achieves an **AUC-ROC of 0.92** and an overall classification accuracy of **0.90**[cite: 19].

### Phase 2: Uniform Demand Inelasticity
* [cite_start]**Overall Elasticity:** The platform-wide Price Elasticity of Demand is **-0.52**, establishing that consumer demand across the digital storefront is highly inelastic[cite: 20, 195].
* [cite_start]**Segment-Level Profiles:** K-Means clustering $(k=3)$ establishes that pricing power is uniform and stable across completely distinct customer engagement tiers[cite: 20, 211, 243]:
  * [cite_start]**Cluster A (VIP Wholesalers):** Generates 62.3% of platform revenue from just 8.0% of the customer base with an elasticity of $e = -0.50$[cite: 20, 214].
  * [cite_start]**Cluster B (Frequent Mainstream Retailers):** Comprises 30.9% of customers with an elasticity of $e = -0.52$[cite: 214, 217].
  * [cite_start]**Cluster C (Low-Engagement Occasional Buyers):** Comprises 61.1% of customers with an elasticity of $e = -0.53$[cite: 20, 214].

> [cite_start]💡 **Strategic Implication:** The near-uniform inelasticity indicates that the platform commands strong competitive pricing power[cite: 218, 273]. [cite_start]Moderate price adjustments (e.g., 5% to 10%) are unlikely to suppress transaction volumes drastically, proving that profit optimization lies in margin expansion and platform layout enhancements rather than aggressive discount promotions[cite: 287, 313].

---

## 📁 Repository Structure

```text
├── data/
│   ├── online_shoppers_intention.csv  # Session clickstream analytics sample
│   └── online_retail_reference.md     # Instructions/URL to download the full 541k transactional records
├── notebooks_or_code/
│   ├── phase1_conversion_prediction.py # SMOTE, Logistic Regression, & Random Forest pipeline
│   └── phase2_econometric_elasticity.py# RFM processing, K-Means clustering, & log-log OLS regressions
├── graphs/
│   ├── normalised_confusion_matrix.png # Phase 1 model performance visual
│   ├── feature_importance_scores.png   # PageValues ranking layout
│   ├── log_log_elasticity_curve.png   # Platform-wide demand curve slope
│   └── segment_price_elasticity.png   # Cluster-level inelasticity comparison chart
├── CIS3032 - E-commerce and Digital Marketing (1).pdf # Full academic research paper
├── requirements.txt                   # Environment dependencies
└── README.md                          # Repository documentation
