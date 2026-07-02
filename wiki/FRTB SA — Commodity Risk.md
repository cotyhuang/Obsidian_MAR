---
tags: [MAR, FRTB, SbM, commodity]
sources:
  - "[[raw/MAR_20260323]]"
  - "[[raw/CRR_20260101.pdf]]"
created: 2026-04-21
---
# FRTB SA — Commodity Risk

> [!info] Regulatory Reference
> Basel MAR21.13, MAR21.23, MAR21.81–21.85
> [[MAR_20260323.pdf#page=29|MAR21.13, page 29]] — [[MAR_20260323.pdf#page=57|MAR21.81–21.85, page 57]]
> EU CRR3 Article 325q, 325as–325au
> [[CRR_20260101.pdf#page=491|CRR Art. 325q, page 491]] — [[CRR_20260101.pdf#page=522|CRR Art. 325as–325au, page 522]]

---

## 1. Risk Factors ([[MAR_20260323.pdf#page=29|MAR21.13, page 29]] / [[CRR_20260101.pdf#page=491|CRR Art. 325q]])

### Delta
Defined along **two dimensions**:
- **Delivery location** (legal terms)
- **Time to maturity**: 0y, 0.25y, 0.5y, 1y, 2y, 3y, 5y, 10y, 15y, 20y, 30y

> [!note] For commodities like electricity, the relevant risk factor can be the **forward price** rather than spot, since transactions are more frequent on forward prices (MAR21.13(1)).

### Vega
Implied volatilities of options referencing commodity spot prices:
- **No differentiation** by maturity of underlying or delivery location
- One dimension: option maturity (0.5y, 1y, 3y, 5y, 10y)

### Curvature
- Constructed curve per commodity spot price (no term structure decomposition)
- All tenors shifted in parallel

---

## 2. Buckets & Delta Risk Weights ([[MAR_20260323.pdf#page=57|MAR21.82, page 57]] / [[CRR_20260101.pdf#page=522|CRR Art. 325as]])

| Bucket | Commodity Group                       | Examples                                                        | RW  |
| ------ | ------------------------------------- | --------------------------------------------------------------- | --- |
| 1      | Energy — Solid combustibles           | Coal, charcoal, wood pellets, uranium                           | 30% |
| 2      | Energy — Liquid combustibles          | Crude oil (WTI, Brent), biofuels, petrochemicals, refined fuels | 35% |
| 3      | Energy — Electricity & carbon trading | Spot/peak/off-peak electricity, emissions certificates          | 60% |
| 4      | Freight                               | Capesize, Panamax, Suezmax, VLCC routes                         | 80% |
| 5      | Metals — Non-precious                 | Aluminium, copper, zinc, nickel, steel, iron ore                | 40% |
| 6      | Gaseous combustibles                  | Natural gas, LNG                                                | 45% |
| 7      | Precious metals (inc. gold)           | Gold, silver, platinum, palladium                               | 20% |
| 8      | Grains & oilseed                      | Corn, wheat, soybean, palm oil, rice                            | 35% |
| 9      | Livestock & dairy                     | Live cattle, hog, poultry, milk, eggs, cheese                   | 25% |
| 10     | Softs & other agriculturals           | Cocoa, coffee, tea, sugar, cotton, lumber                       | 35% |
| 11     | Other commodity                       | Potash, fertilizer, rare earths                                 | 50% |

---

## 3. Intra-Bucket Correlations ρ_{kl} ([[MAR_20260323.pdf#page=57|MAR21.83, page 57]] / [[CRR_20260101.pdf#page=522|CRR Art. 325at]])

$$\rho_{kl} = \rho_{commodity} \times \rho_{tenor} \times \rho_{location}$$

| Parameter   | Value when same | Value when different |
| ----------- | --------------- | -------------------- |
| ρ_commodity | 1               | See table below      |
| ρ_tenor     | 1               | 99.00%               |
| ρ_location  | 1               | 99.90%               |

### ρ_commodity by Bucket (MAR21.83, Table 12)

| Bucket | Commodity Group               | $ρ_{commodity}$ |
| ------ | ----------------------------- | --------------- |
| 1      | Energy — Solid combustibles   | 55%             |
| 2      | Energy — Liquid combustibles  | 95%             |
| 3      | Energy — Electricity & carbon | 40%             |
| 4      | Freight                       | 80%             |
| 5      | Metals — Non-precious         | 60%             |
| 6      | Gaseous combustibles          | 65%             |
| 7      | Precious metals               | 55%             |
| 8      | Grains & oilseed              | 45%             |
| 9      | Livestock & dairy             | 15%             |
| 10     | Softs & other agriculturals   | 40%             |
| 11     | Other commodity               | 15%             |

> [!note] Distinct Commodities
> Two commodities are distinct if market contracts differ in the **underlying to be delivered** (MAR21.83(1)). E.g. WTI and Brent are distinct commodities within bucket 2. Electricity at different delivery times (peak vs off-peak) are also distinct (MAR21.84).

---

## 4. Inter-Bucket Correlations γ_{bc} ([[MAR_20260323.pdf#page=59|MAR21.85, page 59]] / [[CRR_20260101.pdf#page=523|CRR Art. 325au]])

| Condition | γ |
|---|---|
| Both buckets in 1–10 | **20%** |
| Either bucket is 11 | **0%** |

---

## 5. Sensitivity Definition ([[MAR_20260323.pdf#page=33|MAR21.23, page 33]] / [[CRR_20260101.pdf#page=475|CRR Art. 325f]])

$$s_k = \frac{V_i(1.01 \cdot CTY_k) - V_i(CTY_k)}{0.01}$$

A **1% relative shift** in the commodity spot price.

---

## 6. Vega Risk Weight ([[MAR_20260323.pdf#page=60|MAR21.92, page 60]] / [[CRR_20260101.pdf#page=525|CRR Art. 325ay]])

| Risk Class | Liquidity Horizon | Risk Weight |
|---|---|---|
| Commodity | 120 days | 100% |

---

## 7. Curvature Risk Weight ([[MAR_20260323.pdf#page=64|MAR21.99, page 64]] / [[CRR_20260101.pdf#page=477|CRR Art. 325g]])

The curvature risk weight is the **highest delta risk weight** in the bucket, applied as a **relative** parallel shift to all tenors. For example, gold (bucket 7, RW 20%): shift the curve up by 1.2× and down by 0.8× (FAQ1 under MAR21.99).

---

## 8. Calculation Example

Here is a practical, step-by-step example of how **Delta**, **Vega**, and **Curvature** capital charges are calculated for Commodity Risk under the Sensitivities-Based Method (SbM).

### The Scenario: A Crude Oil Option
Let's assume a bank holds a single position in its trading book: A **Long European Call Option on WTI Crude Oil** (which falls into the FRTB bucket: *Energy - Liquid*).

**Market & Position Details:**
*   **Position size:** 1,000 barrels
*   **Spot Price ($S$):** $100 per barrel
*   **Implied Volatility ($\sigma$):** 20%
*   **Option Value (Base):** $5,000

---

### Delta Risk Capital (Linear Price Risk)
Delta measures the linear risk to changes in the underlying commodity price.

*   **Regulatory Risk Weight ($RW_k$):** Under FRTB, the delta risk weight for Liquid Energy is typically **35%** (Bucket 2).
*   **Delta Sensitivity ($s_k$):** This is the change in the portfolio value for a **1% relative shift** in the commodity price. 
    *   Let's assume the option's mathematical delta (from a Black-Scholes model) is $0.5$.
    *   Delta per barrel = $0.5 \times \$100 \times 1\% = \$0.50$
    *   Total Delta Sensitivity ($s_k$) = $\$0.50 \times 1,000 \text{ barrels} = \$500$
*   **Weighted Sensitivity ($WS_k$):** Multiply the sensitivity by the regulatory risk weight.
    *   $WS_k = \$500 \times 35\% = \$175$
*   **Capital Charge:** If this is the only position in the bucket, the Delta capital charge is the absolute weighted sensitivity: **$175**. *(If you had multiple positions in this bucket, you would aggregate their weighted sensitivities using a regulatory correlation matrix).*

---

### Vega Risk Capital (Volatility Risk)
Vega measures the risk of changes in the implied volatility of the commodity. Only instruments with optionality are subject to this charge.

*   **Vega Sensitivity ($s_k$):** Under FRTB, Vega sensitivity is defined as the mathematical vega multiplied by the implied volatility itself.
    *   Let's assume the model calculates that a 1% absolute increase in volatility increases the total option value by $\$40$.
    *   Total Vega Sensitivity = $\$40 \times 20\% = \$800$.
*   **Regulatory Risk Weight ($RW_k$):** For commodities, the Vega risk weight is **100%**.
*   **Weighted Sensitivity ($WS_k$):**
    *   $WS_k = \$800 \times 100\% = \$800$
*   **Capital Charge:** For this single option position, the Vega capital charge is **$800**.

---

### Curvature Risk Capital (Non-Linear / Gamma Risk)
Curvature captures the non-linear risk (gamma) that is not captured by Delta. Unlike Delta and Vega which use standard sensitivities, Curvature relies on **full revaluation under extreme stress scenarios**.

*   **Shock Scenarios:** The shocks applied use the highest delta risk weight in the bucket (which is **35%** for Bucket 2).
    *   **Upward shock price:** $\$100 \times (1 + 0.35) = \$135$
    *   **Downward shock price:** $\$100 \times (1 - 0.35) = \$65$
*   **Full Revaluation:** Reprice the option using your pricing model at these new shocked spot prices.
    *   Value at $\$135 \text{ (Up)} = \$36,000$ (illustrative)
    *   Value at $\$65 \text{ (Down)} = \$150$ (illustrative)
*   **Curvature Risk Measure ($CVR_k$):** Take the fully shocked value, subtract the base value, and then **subtract the linear delta effect** (because Delta is already capitalized). 
    *   *Linear Delta effect for a 35% shock:* $s_k \times (35\% / 1\%) = \$500 \times 35 = \$17,500$
    *   **Upward Curvature ($CVR_{up}$):** $- [ \text{Value(Up)} - \text{Value(Base)} - \text{Delta Effect} ]$
        $CVR_{up} = - [ \$36,000 - \$5,000 - \$17,500 ] = -\$13,500$
    *   **Downward Curvature ($CVR_{down}$):** $- [ \text{Value(Down)} - \text{Value(Base)} - (-\text{Delta Effect}) ]$
        $CVR_{down} = - [ \$150 - \$5,000 - (-\$17,500) ] = - [ -\$4,850 + \$17,500 ] = -\$12,650$
*   **Capital Charge:** Curvature capital only penalizes losses. Because we are *long* an option, we have positive gamma—meaning the non-linear effect works in our favor. 
    *   Because both $CVR$ values are negative, they do not represent a curvature loss. 
    *   The Curvature capital charge for this long option is **$0**.
    *   *(Note: If the bank had **sold** this option instead, the $CVR$ values would be positive, and the bank would take the worst of the two exposures as a heavy Curvature capital penalty).*

### Total Commodity Capital for this Position:
Under the Sensitivities-Based Method, the total capital for this specific position would be the simple sum (assuming no other correlations or portfolio effects):
*   **Delta:** $175
*   **Vega:** $800
*   **Curvature:** $0
*   **Total SA Capital:** **$975**

---

## See Also

- [[FRTB SA — Sensitivities-Based Method]]
- [[FRTB SA — Equity Risk]]
- [[FRTB SA — FX Risk]]
