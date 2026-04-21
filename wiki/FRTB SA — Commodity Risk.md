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

| Bucket | Commodity Group | Examples | RW |
|---|---|---|---|
| 1 | Energy — Solid combustibles | Coal, charcoal, wood pellets, uranium | 30% |
| 2 | Energy — Liquid combustibles | Crude oil (WTI, Brent), biofuels, petrochemicals, refined fuels | 35% |
| 3 | Energy — Electricity & carbon trading | Spot/peak/off-peak electricity, emissions certificates | 60% |
| 4 | Freight | Capesize, Panamax, Suezmax, VLCC routes | 80% |
| 5 | Metals — Non-precious | Aluminium, copper, zinc, nickel, steel, iron ore | 40% |
| 6 | Gaseous combustibles | Natural gas, LNG | 45% |
| 7 | Precious metals (inc. gold) | Gold, silver, platinum, palladium | 20% |
| 8 | Grains & oilseed | Corn, wheat, soybean, palm oil, rice | 35% |
| 9 | Livestock & dairy | Live cattle, hog, poultry, milk, eggs, cheese | 25% |
| 10 | Softs & other agriculturals | Cocoa, coffee, tea, sugar, cotton, lumber | 35% |
| 11 | Other commodity | Potash, fertilizer, rare earths | 50% |

---

## 3. Intra-Bucket Correlations ρ_{kl} ([[MAR_20260323.pdf#page=57|MAR21.83, page 57]] / [[CRR_20260101.pdf#page=522|CRR Art. 325at]])

$$\rho_{kl} = \rho_{commodity} \times \rho_{tenor} \times \rho_{location}$$

| Parameter | Value when same | Value when different |
|---|---|---|
| ρ_commodity | 1 | See table below |
| ρ_tenor | 1 | 99.00% |
| ρ_location | 1 | 99.90% |

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

## See Also

- [[FRTB SA — Sensitivities-Based Method]]
- [[FRTB SA — Equity Risk]]
- [[FRTB SA — FX Risk]]
