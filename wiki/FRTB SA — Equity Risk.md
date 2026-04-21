---
tags: [MAR, FRTB, SbM, equity]
sources:
  - "[[raw/MAR_20260323]]"
created: 2026-04-21
---
# FRTB SA — Equity Risk

> [!info] Regulatory Reference
> Basel MAR21.12, MAR21.21–21.22, MAR21.72–21.80
> [[MAR_20260323.pdf#page=29|MAR21.12, page 29]] — [[MAR_20260323.pdf#page=53|MAR21.72–21.80, page 53]]

---

## 1. Risk Factors ([[MAR_20260323.pdf#page=29|MAR21.12, page 29]])

| Type | Delta | Vega | Curvature |
|---|---|---|---|
| **Equity spot price** | ✓ | ✓ (implied vol) | ✓ |
| **Equity repo rate** | ✓ | ✗ | ✗ |

### Vega Risk Factors
Implied volatilities of options referencing equity spot prices, along **one dimension** — option maturity: 0.5y, 1y, 3y, 5y, 10y.

---

## 2. Buckets ([[MAR_20260323.pdf#page=53|MAR21.72, page 53]])

13 buckets along **market cap** × **economy** × **sector**:

| Bucket | Market Cap | Economy | Sector |
|---|---|---|---|
| 1 | Large | Emerging | Consumer goods, healthcare, transport, utilities |
| 2 | Large | Emerging | Telecom, industrials |
| 3 | Large | Emerging | Basic materials, energy, agriculture, mining |
| 4 | Large | Emerging | Financials, real estate, technology |
| 5 | Large | Advanced | Consumer goods, healthcare, transport, utilities |
| 6 | Large | Advanced | Telecom, industrials |
| 7 | Large | Advanced | Basic materials, energy, agriculture, mining |
| 8 | Large | Advanced | Financials, real estate, technology |
| 9 | Small | Emerging | All sectors (buckets 1–4) |
| 10 | Small | Advanced | All sectors (buckets 5–8) |
| 11 | — | — | Other sector |
| 12 | — | — | Large cap, advanced economy indices |
| 13 | — | — | Other equity indices |

### Key Definitions
- **Large cap**: market capitalisation ≥ **USD 2 billion** (MAR21.74)
- **Small cap**: market capitalisation < USD 2 billion
- **Advanced economies** (MAR21.75): Canada, US, Mexico, euro area, UK, Norway, Sweden, Denmark, Switzerland, Japan, Australia, New Zealand, Singapore, Hong Kong SAR

---

## 3. Delta Risk Weights ([[MAR_20260323.pdf#page=55|MAR21.77, page 55]])

| Bucket | Spot Price RW | Repo Rate RW |
|---|---|---|
| 1 | 55% | 0.55% |
| 2 | 60% | 0.60% |
| 3 | 45% | 0.45% |
| 4 | 55% | 0.55% |
| 5 | 30% | 0.30% |
| 6 | 35% | 0.35% |
| 7 | 40% | 0.40% |
| 8 | 50% | 0.50% |
| 9 | 70% | 0.70% |
| 10 | 50% | 0.50% |
| 11 | 70% | 0.70% |
| 12 | 15% | 0.15% |
| 13 | 25% | 0.25% |

> [!note] Repo rate risk weights are exactly 1/100th of spot price risk weights.

---

## 4. Intra-Bucket Correlations ρ ([[MAR_20260323.pdf#page=55|MAR21.78, page 55]])

### Same Issuer, Spot vs Repo
ρ = **99.90%**

### Different Issuers, Same type (both spot or both repo)

| Buckets | ρ |
|---|---|
| 1–4 (Large, Emerging) | 15% |
| 5–8 (Large, Advanced) | 25% |
| 9 (Small, Emerging) | 7.5% |
| 10 (Small, Advanced) | 12.5% |
| 12–13 (Indices) | 80% |

### Different Issuers, Spot vs Repo
= Above correlation × **99.90%**

### Bucket 11 (Other Sector)
No correlation — simple sum of absolute values of net weighted sensitivities (MAR21.79).

---

## 5. Inter-Bucket Correlations γ_{bc} ([[MAR_20260323.pdf#page=56|MAR21.80, page 56]])

| Condition | γ |
|---|---|
| Both buckets in 1–10 | **15%** |
| Either bucket is 11 | **0%** |
| Buckets 12 and 13 (both are index buckets) | **75%** |
| Otherwise | **45%** |

---

## 6. Sensitivity Definitions

### Delta Equity Spot ([[MAR_20260323.pdf#page=32|MAR21.21, page 32]])
$$s_k = \frac{V_i(1.01 \cdot EQ_k) - V_i(EQ_k)}{0.01}$$

### Delta Equity Repo Rate ([[MAR_20260323.pdf#page=33|MAR21.22, page 33]])
$$s_k = \frac{V_i(RepoTS_k + 0.0001) - V_i(RepoTS_k)}{0.0001}$$

---

## 7. Vega Risk Weight ([[MAR_20260323.pdf#page=60|MAR21.92, page 60]])

| Sub-class | Liquidity Horizon | Risk Weight |
|---|---|---|
| Large cap & indices (buckets 1–8, 12–13) | 20 days | 77.78% |
| Small cap & other (buckets 9–11) | 60 days | 100% |

---

## 8. Curvature Risk Weight ([[MAR_20260323.pdf#page=63|MAR21.98, page 63]])

The curvature risk weight = the **delta risk weight** for equity spot (relative shift). No curvature for equity repo rates.

---

## See Also

- [[FRTB SA — Sensitivities-Based Method]]
- [[FRTB SA — Commodity Risk]]
- [[FRTB SA — FX Risk]]
- [[FRTB SA — Default Risk Charge]]
