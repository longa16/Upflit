# Uplift Modeling (A/B Testing)

## Business Context
In direct marketing, targeting the entire customer base is often inefficient and costly. Worse, some campaigns can negatively impact certain segments ("Sleeping Dogs").
The goal of this project is not simply to predict "who will buy," but to identify the **causal effect** of a marketing campaign: "Who will buy *because of* email?"

## Technical Stack
* **Language:** Python 3.x
* **Libraries:** Pandas, Scikit-learn, Seaborn.
* **Methodology:** A/B Testing, Uplift Modeling.

* **Approach:** Two-Model Approach (T-Learner) with RandomForest.

## Data
Use of the **Kevin Hillstrom Email Analytics** dataset (64,000 customers).

* **Treatment Group:** Received a marketing email for men.

* **Control Group:** Did not receive any emails.

* **Objective:** Conversion (Purchase).

## Methodology & Modeling

### 1. Classic A/B Analysis
Calculation of the ATE (Average Treatment Effect).

* Result: The email has a small overall positive impact (+0.6% conversion). However, this masks some disparities.

### 2. Uplift Modeling (Two-Model Approach)
Training two distinct models (Random Forest):

1. **Treatment Model ($M_t$):** Learns the behavior of targeted customers.

2. **Control Model ($M_c$):** Learns the organic behavior of customers.

The **Uplift Score** is calculated for each customer:
$$Uplift = P(Purchase | Email) - P(Purchase | Nothing)$$

## Results & Strategic Impact

Analysis of the Uplift score distribution allowed us to segment the database into 4 categories:
| Segment | Uplift Score | Action Recommandée                                                                 |
| :--- | :--- |:-----------------------------------------------------------------------------------|
| **Persuadables** | **Positif (> 0)** | **Cibler en priorité.** Ce sont les seuls pour qui le ROI est positif.             |
| **Sure Things** | Proche de 0 | **Ne pas cibler.** Ils auraient acheté de toute façon. Économie de budget.         |
| **Lost Causes** | Proche de 0 | **Ne pas cibler.** N'achèteront pas.                                               |
| **Sleeping Dogs** | **Négatif (< 0)** |  **Éviter absolument.** L'email réduit leur probabilité d'achat (réaction négative).|

**Conclusion:** By targeting only "Persuadables", the company can reduce its sending costs while maximizing incremental revenue.