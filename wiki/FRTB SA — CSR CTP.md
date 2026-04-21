---
tags: [MAR, FRTB, SbM, CSR, CTP, correlation-trading]
sources:
  - "[[raw/MAR_20260323]]"
created: 2026-04-21
---
# FRTB SA — CSR CTP (Correlation Trading Portfolio)

> [!info] Regulatory Reference
> Basel MAR20.5, MAR21.11, MAR21.58–21.61
> [[MAR_20260323.pdf#page=18|MAR20.5, page 18]] — [[MAR_20260323.pdf#page=28|MAR21.11, page 28]] — [[MAR_20260323.pdf#page=49|MAR21.58–21.61, page 49]]

---

## 1. Definition of CTP ([[MAR_20260323.pdf#page=18|MAR20.5, page 18]])

The CTP consists of:
1. **Securitisation positions** that:
   - Are not re-securitisations
   - Have single-name reference entities with liquid two-way markets
   - Do not reference retail/residential/commercial mortgage exposures
   - Do not reference special purpose entities
2. **Non-securitisation hedges** to above positions

---

## 2. Risk Factors ([[MAR_20260323.pdf#page=28|MAR21.11, page 28]])

### Delta
- **Underlying** credit spread curves (bond and CDS) — not tranche spreads
- Tenors: 0.5y, 1y, 3y, 5y, 10y
- Sensitivities computed with respect to **names underlying** the securitisation (MAR21.11(1))

### Vega
- Implied volatilities of options referencing CTP credit spreads
- One dimension: option maturity

### Curvature
- Underlying credit spread curves (bond and CDS treated as single curve)
- All tenors shifted in parallel

> [!note] Key Distinction
> Unlike non-CTP securitisation (where sensitivities are to the *tranche* spread), CTP sensitivities are to the *underlying name* spread.

---

## 3. Buckets & Risk Weights (MAR21.58–21.59)

### Bucket Structure
Same bucket structure as [[FRTB SA — CSR Non-Securitisation|CSR non-sec]] (MAR21.51), **except** no index buckets (17/18). Index CTP instruments are assigned to sector buckets based on 75% constituent mapping (FAQ1).

### Risk Weights ([[MAR_20260323.pdf#page=49|MAR21.59, page 49]])

| Bucket | Sector | RW |
|---|---|---|
| 1 | Sovereigns, central banks, MDBs | 4.0% |
| 2 | Local gov, gov-backed non-financials | 4.0% |
| 3 | Financials | 8.0% |
| 4 | Basic materials, energy, industrials | 5.0% |
| 5 | Consumer goods, transportation | 4.0% |
| 6 | Technology, telecom | 3.0% |
| 7 | Health care, utilities | 2.0% |
| 8 | Covered bonds | 6.0% |
| 9–16 | HY/NR equivalents | 13%–16% (see table) |

> [!warning] CTP risk weights are significantly **higher** than CSR non-sec to account for longer liquidity horizons and larger basis risk.

---

## 4. Intra-Bucket Correlations ([[MAR_20260323.pdf#page=50|MAR21.60, page 50]])

Same formula as [[FRTB SA — CSR Non-Securitisation]] (ρ_name × ρ_tenor × ρ_basis), with one modification:

| Parameter | CSR Non-Sec | CSR CTP |
|---|---|---|
| ρ_basis (same curves) | 99.90% | **99.00%** |

This lower basis correlation reflects the **larger basis risk** in the CTP.

---

## 5. Inter-Bucket Correlations ([[MAR_20260323.pdf#page=50|MAR21.61, page 50]])

Identical to [[FRTB SA — CSR Non-Securitisation]] cross-bucket correlations (MAR21.57).

---

## See Also

- [[FRTB SA — Sensitivities-Based Method]]
- [[FRTB SA — CSR Non-Securitisation]]
- [[FRTB SA — CSR Securitisation]]
- [[FRTB SA — Default Risk Charge]]
