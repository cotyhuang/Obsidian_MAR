---
tags: [MAR, FRTB, SbM, CSR, credit-spread]
sources:
  - "[[raw/MAR_20260323]]"
  - "[[raw/CRR_20260101.pdf]]"
created: 2026-04-21
---
# FRTB SA — CSR Non-Securitisation

> [!info] Regulatory Reference
> Basel MAR21.9, MAR21.20, MAR21.51–21.57
> [[MAR_20260323.pdf#page=27|MAR21.9, page 27]] — [[MAR_20260323.pdf#page=45|MAR21.51–21.57, page 45]]
> EU CRR3 Article 325m, 325ah–325aj
> [[CRR_20260101.pdf#page=488|CRR Art. 325m, page 488]] — [[CRR_20260101.pdf#page=513|CRR Art. 325ah–325aj, page 513]]

---

## 1. Risk Factors & Buckets

### Delta Risk Factors ([[MAR_20260323.pdf#page=27|MAR21.9(1), page 27]] / [[CRR_20260101.pdf#page=488|CRR Art. 325m]])
Defined along **two dimensions**:
- Issuer credit spread curves (bond and CDS separately)
- Tenors: 0.5y, 1y, 3y, 5y, 10y

### Vega Risk Factors (MAR21.9(2))
Implied volatilities of options referencing credit issuer names, defined along **one dimension** — option maturity: 0.5y, 1y, 3y, 5y, 10y.

### Curvature Risk Factors (MAR21.9(3))
Defined along **one dimension** — the relevant issuer credit spread curve. Bond and CDS curves of the same issuer are treated as a **single curve** for curvature (i.e. bond-CDS basis is ignored). All tenors shifted in parallel.

---

## 2. Buckets ([[MAR_20260323.pdf#page=45|MAR21.51, page 45]] / [[CRR_20260101.pdf#page=513|CRR Art. 325ah]])

Buckets are set along **credit quality** × **sector**:

| Bucket | Credit Quality | Sector |
|---|---|---|
| 1 | Investment Grade (IG) | Sovereigns, central banks, MDBs |
| 2 | IG | Local government, government-backed non-financials, education, public admin |
| 3 | IG | Financials including government-backed financials |
| 4 | IG | Basic materials, energy, industrials, agriculture, manufacturing, mining |
| 5 | IG | Consumer goods & services, transportation, admin & support services |
| 6 | IG | Technology, telecommunications |
| 7 | IG | Health care, utilities, professional & technical activities |
| 8 | IG | Covered bonds |
| 9 | High Yield / Non-Rated | Sovereigns, central banks, MDBs |
| 10 | HY/NR | Local government, government-backed non-financials, education, public admin |
| 11 | HY/NR | Financials including government-backed financials |
| 12 | HY/NR | Basic materials, energy, industrials, agriculture, manufacturing, mining |
| 13 | HY/NR | Consumer goods & services, transportation, admin & support services |
| 14 | HY/NR | Technology, telecommunications |
| 15 | HY/NR | Health care, utilities, professional & technical activities |
| 16 | — | Other sector |
| 17 | — | IG indices |
| 18 | — | HY indices |

---

## 3. Delta Risk Weights ([[MAR_20260323.pdf#page=46|MAR21.53, page 46]] / [[CRR_20260101.pdf#page=513|CRR Art. 325ah]])

Risk weights are **uniform** across all tenors within each bucket:

| Bucket | RW | Bucket | RW |
|---|---|---|---|
| 1 | 0.5% | 10 | 4.0% |
| 2 | 1.0% | 11 | 12.0% |
| 3 | 5.0% | 12 | 7.0% |
| 4 | 3.0% | 13 | 8.5% |
| 5 | 3.0% | 14 | 5.5% |
| 6 | 2.0% | 15 | 5.0% |
| 7 | 1.5% | 16 | 12.0% |
| 8 | 2.5% | 17 | 1.5% |
| 9 | 2.0% | 18 | 5.0% |

> [!tip] Covered bonds rated AA- or higher may use 1.5% instead of 2.5% (footnote 17).

---

## 4. Intra-Bucket Correlations ρ_{kl} ([[MAR_20260323.pdf#page=47|MAR21.54–21.56, page 47]] / [[CRR_20260101.pdf#page=514|CRR Art. 325ai]])

### Buckets 1–15
$$\rho_{kl} = \rho_{name} \times \rho_{tenor} \times \rho_{basis}$$

| Parameter | Value when same | Value when different |
|---|---|---|
| ρ_name | 1 | 35% |
| ρ_tenor | 1 | 65% |
| ρ_basis (bond vs CDS) | 1 | 99.90% |

### Buckets 17–18 (Index Buckets)
Same structure but ρ_name = **80%** when different names (MAR21.55).

### Bucket 16 (Other Sector)
**No correlation** — aggregate by simple sum of absolute values of net weighted sensitivities (MAR21.56).

---

## 5. Inter-Bucket Correlations γ_{bc} ([[MAR_20260323.pdf#page=48|MAR21.57, page 48]] / [[CRR_20260101.pdf#page=515|CRR Art. 325aj]])

$$\gamma_{bc} = \gamma_{rating} \times \gamma_{sector}$$

- **γ_rating** = 50% if buckets have different rating categories (IG vs HY/NR); 1 otherwise
- **γ_sector** — from the cross-sector correlation table:

| | 1/9 | 2/10 | 3/11 | 4/12 | 5/13 | 6/14 | 7/15 | 8 | 16 | 17 | 18 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **1/9** | — | 75% | 10% | 20% | 25% | 20% | 15% | 10% | 0% | 45% | 45% |
| **2/10** | — | — | 5% | 15% | 20% | 15% | 10% | 10% | 0% | 45% | 45% |
| **3/11** | — | — | — | 5% | 15% | 20% | 5% | 20% | 0% | 45% | 45% |
| **4/12** | — | — | — | — | 20% | 25% | 5% | 5% | 0% | 45% | 45% |
| **5/13** | — | — | — | — | — | 25% | 5% | 15% | 0% | 45% | 45% |
| **6/14** | — | — | — | — | — | — | 5% | 20% | 0% | 45% | 45% |
| **7/15** | — | — | — | — | — | — | — | 5% | 0% | 45% | 45% |
| **8** | — | — | — | — | — | — | — | — | 0% | 45% | 45% |
| **16** | — | — | — | — | — | — | — | — | — | 0% | 0% |
| **17** | — | — | — | — | — | — | — | — | — | — | 75% |

---

## 6. Sensitivity Definition — CS01 ([[MAR_20260323.pdf#page=32|MAR21.20, page 32]] / [[CRR_20260101.pdf#page=475|CRR Art. 325f]])

$$s_{k,cs_t} = \frac{V_i(r_t, cs_t + 0.0001) - V_i(r_t, cs_t)}{0.0001}$$

Where:
- $cs_t$ = credit spread at tenor *t*
- $r_t$ = risk-free yield curve held constant
- $V_i$ = market value of instrument *i*

---

## 7. Curvature Risk Weight ([[MAR_20260323.pdf#page=64|MAR21.99, page 64]] / [[CRR_20260101.pdf#page=477|CRR Art. 325g]])

For CSR, the curvature risk weight is the **highest delta risk weight** in the bucket, applied as a parallel shift to all tenors.

> [!note] When the downward shock would result in a negative credit spread, banks may floor the curvature risk factor at zero (FAQ2 under MAR21.99).

---

## See Also

- [[FRTB SA — Sensitivities-Based Method]]
- [[FRTB SA — CSR Securitisation]]
- [[FRTB SA — CSR CTP]]
- [[FRTB SA — Default Risk Charge]]
