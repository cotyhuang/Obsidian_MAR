---
tags: [MAR, FRTB, SbM, CSR, securitisation]
sources:
  - "[[raw/MAR_20260323]]"
created: 2026-04-21
---
# FRTB SA — CSR Securitisation (Non-CTP)

> [!info] Regulatory Reference
> Basel MAR21.10, MAR21.62–21.71
> [[MAR_20260323.pdf#page=28|MAR21.10, page 28]] — [[MAR_20260323.pdf#page=51|MAR21.62–21.71, page 51]]

---

## 1. Risk Factors

### Delta (MAR21.10(2))
- **Tranche credit spread curves** (not underlying issuer curves)
- Tenors: 0.5y, 1y, 3y, 5y, 10y
- Sensitivities (CS01) calculated with respect to the **spread of the tranche** (MAR21.10(1))

### Vega (MAR21.10(3))
- Implied volatilities of options referencing non-CTP credit spreads
- One dimension: option maturity (0.5y, 1y, 3y, 5y, 10y)

### Curvature (MAR21.10(4))
- Relevant tranche credit spread curves (bond and CDS considered a single curve)
- All tenors shifted in parallel

---

## 2. Buckets ([[MAR_20260323.pdf#page=51|MAR21.62, page 51]])

25 buckets along **seniority/credit quality** × **asset class**:

| Buckets | Seniority | Asset Classes |
|---|---|---|
| 1–8 | Senior Investment Grade | RMBS Prime, RMBS Mid-prime, RMBS Sub-prime, CMBS, ABS Student Loans, ABS Credit Cards, ABS Auto, CLO |
| 9–16 | Non-Senior IG | Same 8 asset classes |
| 17–24 | High Yield & Non-Rated | Same 8 asset classes |
| 25 | — | Other sector |

---

## 3. Delta Risk Weights ([[MAR_20260323.pdf#page=52|MAR21.64–21.67, page 52]])

### Senior IG (Buckets 1–8)

| Bucket | Asset Class | RW |
|---|---|---|
| 1 | RMBS Prime | 0.9% |
| 2 | RMBS Mid-prime | 1.5% |
| 3 | RMBS Sub-prime | 2.0% |
| 4 | CMBS | 2.0% |
| 5 | ABS Student Loans | 0.8% |
| 6 | ABS Credit Cards | 1.2% |
| 7 | ABS Auto | 1.2% |
| 8 | CLO | 1.4% |

### Non-Senior IG (Buckets 9–16)
= Senior IG risk weights × **1.25**

### High Yield / Non-Rated (Buckets 17–24)
= Senior IG risk weights × **1.75**

### Other Sector (Bucket 25)
= **3.5%**

---

## 4. Intra-Bucket Correlations ρ_{kl} ([[MAR_20260323.pdf#page=52|MAR21.68, page 52]])

$$\rho_{kl} = \rho_{tranche} \times \rho_{tenor} \times \rho_{basis}$$

| Parameter | Value when same | Value when different |
|---|---|---|
| ρ_tranche | 1 (>80% notional overlap) | 40% |
| ρ_tenor | 1 | 80% |
| ρ_basis | 1 | 99.90% |

> [!warning] Unlike CSR non-sec, correlation is based on **tranche similarity** (>80% notional overlap), not issuer name. Two tranches from the same issuer but different seniorities get only 40% correlation (FAQ1).

### Bucket 25 (Other Sector)
No correlation — simple sum of absolute values of net weighted sensitivities (MAR21.69).

---

## 5. Inter-Bucket Correlations γ_{bc} ([[MAR_20260323.pdf#page=53|MAR21.70–21.71, page 53]])

- **γ = 0%** between all buckets 1–24
- Bucket 25 is simply **added** to the aggregate — no diversification (MAR21.71)

---

## See Also

- [[FRTB SA — Sensitivities-Based Method]]
- [[FRTB SA — CSR Non-Securitisation]]
- [[FRTB SA — CSR CTP]]
- [[FRTB SA — Default Risk Charge]]
