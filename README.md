# The Impact of Product Pricing Strategies on Online Purchase Decisions Using E-Commerce Data

This repository contains the empirical source code, datasets, visual analytics, and the final research article for the study completed under the Bachelor of Computing (Hons) in Information Systems program at the Faculty of Computing, University of Sri Jayewardenepura.

---

## 📌 Project Overview
This study investigates how product pricing tactics and web-resident value indicators jointly influence online purchase decisions. E-commerce platforms routinely manipulate demand signals through traditional pricing mechanisms, yet the financial value embedded within a user's digital browsing environment remains a critical, understudied complement. 

To bridge this gap, this research deploys a **dual-phase pipeline** connecting front-end session-level clickstream analytics with back-end customer transactional dynamics.

### 🔬 Methodology Breakdown
* **Phase 1 (Clickstream Analytics):** Models session conversion behavior using the UCI Online Shoppers Purchasing Intention Dataset (12,330 user sessions). It leverages Logistic Regression for interpretability and coefficient extraction alongside Random Forest ensemble classification to handle severe class imbalances via SMOTE processing.
* **Phase 2 (Transactional Economics):** Analyzes macro-level transactional data using the UCI Online Retail Dataset (406,829 valid line items across 4,372 unique customers). It uses K-Means clustering to partition the customer base into distinct value tiers based on Recency, Frequency, and Monetary (RFM) modeling, computing the Price Elasticity of Demand ($e$) within each segment via Ordinary Least Squares ($log-log$ linear regression).

---

## 📊 Key Findings

### Phase 1: Session Conversion Predictors
* **Dominant Feature:** `PageValues` (an estimated monetary indicator computed via server-side analytics tracking) is the single strongest predictor of session conversion. It accounts for **37.9% of total predictive importance** in the Random Forest feature importance ranking.
* **Effect Size:** Logistic Regression yields a positive coefficient ($b = 0.074, p < 0.001$) for `PageValues`. This corresponds to an **Odds Ratio (OR) of 1.077**, meaning every single-dollar increase in a page's value profile is associated with a **7.7% increase in the odds of session conversion**, holding all other variables constant.
* **Classification Performance:** The Random Forest classifier achieves an **AUC-ROC of 0.92** and an overall classification accuracy of **0.90**.

### Phase 2: Uniform Demand Inelasticity
* **Overall Elasticity:** The platform-wide Price Elasticity of Demand is **-0.52**, establishing that consumer demand across the digital storefront is highly inelastic.
* **Segment-Level Profiles:** K-Means clustering ($k=3$) establishes that pricing power is uniform and stable across completely distinct customer engagement tiers:
  * **Cluster A (VIP Wholesalers):** Generates 62.3% of platform revenue from just 8.0% of the customer base with an elasticity of $e = -0.50$.
  * **Cluster B (Frequent Mainstream Retailers):** Comprises 30.9% of customers with an elasticity of $e = -0.52$.
  * **Cluster C (Low-Engagement Occasional Buyers):** Comprises 61.1% of customers with an elasticity of $e = -0.53$.

> 💡 **Strategic Implication:** The near-uniform inelasticity indicates that the platform commands strong competitive pricing power. Moderate price adjustments (e.g., 5% to 10%) are unlikely to suppress transaction volumes drastically, proving that profit optimization lies in margin expansion and platform layout enhancements rather than aggressive discount promotions.

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
