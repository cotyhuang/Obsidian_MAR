---
tags: [MarketRisk, FRTB, MAR, CRR, BaselIII, BankingRegulation]
aliases: [Market Risk SA Comparison, SbM Methodology, CRR III Market Risk]
---

# Market Risk SA: MAR (Basel) vs. CRR (EU) Methodology Comparison

This document provides a technical comparison of the **Standardised Approach (SA)** for market risk as defined by the [[Basel Committee on Banking Supervision]] (MAR) and the [[European Banking Authority]] / [[European Commission]] (CRR).

## 1. Methodology Overview

Both frameworks implement the **Fundamental Review of the Trading Book (FRTB)**. The total own funds requirement for market risk under the Standardised Approach is the simple sum of three components:

1.  **[[Sensitivities-Based Method]] (SbM):** Captures Delta, Vega, and Curvature risks using risk-weighted sensitivities.
2.  **[[Default Risk Capital]] (DRC):** Captures jump-to-default risk for credit and equity.
3.  **[[Residual Risk Add-on]] (RRAO):** A flat charge for exotic risks (e.g., gap risk, correlation risk in complex derivatives).

### Methodology Differences

| Feature                   | MAR (Basel) Framework                          | CRR (EU) ASA                                                             |
| :------------------------ | :--------------------------------------------- | :----------------------------------------------------------------------- |
| **Governance**            | Global standard-setter (BCBS).                 | Legally binding EU Regulation (CRR II/III).                              |
| **Correlation Scenarios** | Uses Medium, High, Low correlation scenarios.  | Identical, but with specific EU-level calibrations for certain pairs.    |
| **FX Risk Base Currency** | Not explicitly emphasized in the core formula. | Permits a "base currency" approach (Art 325q) with supervisory approval. |
| **GIRR Risk Weights**     | Standardized across all currencies.            | Differentiates risk weights based on currency liquidity (Art 325ae).     |
| **Reporting**             | Set by national supervisors.                   | Strict technical standards (ITS) defined by the [[EBA]].                 |

---

## 2. Formula Comparisons

### A. Sensitivities-Based Method (SbM)
Both frameworks use the **Square Root of the Sum of Squares (SRSS)** aggregation logic.

#### Intra-Bucket Aggregation ($K_b$)
The capital requirement for a single bucket $b$ is:
$$K_b = \sqrt{\sum_k WS_k^2 + \sum_k \sum_{l \neq k} \rho_{kl} WS_k WS_l}$$
* **$WS_k$**: Weighted Sensitivity.
* **$\rho_{kl}$**: Correlation between risk factor $k$ and $l$ within the bucket.

#### Inter-Bucket Aggregation ($K$)
The total risk-class requirement is:
$$K = \sqrt{\sum_b K_b^2 + \sum_b \sum_{c \neq b} \gamma_{bc} S_b S_c}$$
* **$\gamma_{bc}$**: Correlation between bucket $b$ and bucket $c$.
* **$S_b$**: The sum of weighted sensitivities in bucket $b$, calculated as $S_b = \sum_{k \in b} WS_k$.

### B. Delta Risk Sensitivity Definition
* **MAR:** Defined as the change in the market value of an instrument for a 1bp (0.0001) shift in the interest rate or 1% shift in the price.
* **CRR:** Same definition, but CRR explicitly clarifies the treatment of **Linear vs. Non-Linear** sensitivities for specific products in Technical Standards.

---

## 3. Calculation Example: GIRR Delta Risk
This example demonstrates a 5-year EUR interest rate swap sensitivity calculation.

> [!tip] Input Data
> * **Instrument:** EUR 100M 5Y IRS.
> * **Sensitivity (PV01):** EUR 50,000 (Loss if rates rise 1bp).
> * **Framework:** Comparison of MAR vs CRR Weights for 5Y Tenor.

### Step 1: Normalize Sensitivity ($s_k$)
$$s_k = \frac{\text{PV01}}{0.0001} = \frac{50,000}{0.0001} = 500,000,000$$

### Step 2: Apply Tenor-Specific Risk Weights ($RW_k$)
* **MAR (Basel):** 5Y Tenor $RW \approx 1.30\%$ (interpolated/standard).
* **CRR (Art 325ae):** 5Y Tenor $RW = 1.10\%$.

### Step 3: Calculate Weighted Sensitivity ($WS_k$)
* **MAR:** $WS_k = 500,000,000 \times 0.013 = \mathbf{6,500,000}$
* **CRR:** $WS_k = 500,000,000 \times 0.011 = \mathbf{5,500,000}$

### Step 4: Final Requirement ($K_b$)
Assuming this is the only position in the EUR bucket:
* **MAR Result:** EUR 6.5M
* **CRR Result:** EUR 5.5M

> [!important] Result Difference
> The **CRR** often results in lower capital requirements for highly liquid EU currencies (like EUR) due to calibrated risk weights that differ from the global Basel MAR floor.

---

## 4. Official Resource Links

For the most up-to-date legislative text and technical standards, refer to:

### Basel Committee (MAR)
* **MAR - Calculation of RWA for Market Risk:** [Official Basel Framework](https://www.bis.org/basel_framework/standard/MAR.htm)
* **MAR21 - Sensitivities-based Method:** [MAR21 Chapter](https://www.bis.org/basel_framework/chapter/MAR/21.htm)

### European Union (CRR)
* **Regulation (EU) 2024/1623 (CRR III):** [Latest EUR-Lex Version](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202401623)
* **CRR Part Three, Title IV, Chapter 1a:** [Alternative Standardised Approach (Art 325a)](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32013R0575#d1e11361-1-1)

### EBA Technical Standards
* **Market Risk Single Rulebook:** [EBA Market Risk Policy](https://www.eba.europa.eu/regulation-and-policy/market-risk)
* **EBA Interactive Single Rulebook:** [Interactive CRR Search](https://www.eba.europa.eu/regulation-and-policy/single-rulebook/interactive-single-rulebook)