---
tags: [MAR, FRTB, SA, DRC, default-risk]
sources:
  - "[[raw/MAR_20260323]]"
created: 2026-04-21
---
# FRTB SA — Default Risk Charge (DRC)

> [!info] Regulatory Reference
> Basel MAR22 — Standardised approach: default risk capital requirement (effective 01 Jan 2023).
> [[MAR_20260323.pdf#page=66|MAR22, page 66]]

---

## 1. Purpose ([[MAR_20260323.pdf#page=67|MAR22.1, page 67]])

The DRC captures **jump-to-default (JTD) risk** — the risk of sudden default — which may not be fully captured by credit spread shocks in the [[FRTB SA — Sensitivities-Based Method|SBM]].

Key concepts:
- **Offsetting**: netting of long/short exposures to the **same obligor** (full offset permitted, subject to seniority rules)
- **Hedging**: partial benefit from short exposures to **different obligors** within the same bucket (via the Hedge Benefit Ratio)

---

## 2. Scope ([[MAR_20260323.pdf#page=67|MAR22.2, page 67]])

DRC is calculated separately for three portfolios, with **no diversification** between them ([[MAR_20260323.pdf#page=67|MAR22.4, page 67]]):

| # | Portfolio | MAR Reference |
|---|---|---|
| 1 | Non-securitisation | MAR22.9–22.26 |
| 2 | Securitisation (non-CTP) | MAR22.27–22.35 |
| 3 | Securitisation (CTP) | MAR22.36–22.45 |

---

## 3. Step-by-Step Calculation ([[MAR_20260323.pdf#page=67|MAR22.3, page 67]])

```
Step 1: Compute Gross JTD per exposure
Step 2: Offset long/short to same obligor → Net JTD
Step 3: Allocate Net JTD to buckets
Step 4: Compute Hedge Benefit Ratio (HBR) per bucket
Step 5: Apply risk weights → Aggregate within bucket
Step 6: Sum across buckets (no diversification)
```

---

## 4. Gross JTD ([[MAR_20260323.pdf#page=68|MAR22.11, page 68]])

$$\text{JTD}_{long} = \max\left(\text{LGD} \times \text{Notional} + \text{P\&L},\; 0\right)$$
$$\text{JTD}_{short} = \min\left(\text{LGD} \times \text{Notional} + \text{P\&L},\; 0\right)$$

Where:
- **Notional** = bond-equivalent face value (positive for long, negative for short)
- **P&L** = Market Value − Notional (cumulative mark-to-market gain/loss)

### LGD Assignments ([[MAR_20260323.pdf#page=69|MAR22.12, page 69]])

| Instrument Type | LGD |
|---|---|
| Equity & non-senior debt | **100%** |
| Senior debt | **75%** |
| Covered bonds | **25%** |
| Price not linked to recovery | No LGD multiplication |

### Maturity Scaling ([[MAR_20260323.pdf#page=69|MAR22.15, page 69]], [[MAR_20260323.pdf#page=70|MAR22.18, page 70]])
- Exposures with maturity **< 1 year**: JTD scaled by maturity/1 year
- Exposures with maturity **≥ 1 year**: no scaling
- **Floor**: minimum scaling = **3 months** (i.e. 0.25)
- Cash equities: assigned maturity of either **>1 year** or **3 months**, at bank's discretion (MAR22.16)

---

## 5. Net JTD — Offsetting Rules ([[MAR_20260323.pdf#page=72|MAR22.19, page 72]])

Long and short exposures to the **same obligor** may offset, subject to:

| Rule | Condition |
|---|---|
| Seniority constraint | Short must have **same or lower** seniority than the long (e.g. short equity can offset long bond, but NOT vice versa) |
| Same maturity band | Both >1y: full offset. Mix of <1y and >1y: short scaled by its maturity fraction |
| Both <1y | Scaling applied to **both** legs |

---

## 6. DRC for Non-Securitisations ([[MAR_20260323.pdf#page=73|MAR22.22–22.26, page 73]])

### Buckets
| Bucket | Obligor Type |
|---|---|
| 1 | Corporates |
| 2 | Sovereigns |
| 3 | Local governments & municipalities |

### Risk Weights by Credit Quality ([[MAR_20260323.pdf#page=73|MAR22.24, page 73]])

| Rating | RW |
|---|---|
| AAA | 0.5% |
| AA | 2% |
| A | 3% |
| BBB | 6% |
| BB | 15% |
| B | 30% |
| CCC | 50% |
| Unrated | 15% |
| Defaulted | 100% |

### Hedge Benefit Ratio ([[MAR_20260323.pdf#page=73|MAR22.23, page 73]])

$$\text{HBR} = \frac{\sum \text{Net Long JTD}}{\sum \text{Net Long JTD} + \sum |\text{Net Short JTD}|}$$

The HBR acts as a **discount factor** on short positions — reflecting that hedging across different obligors is imperfect.

### Bucket-Level DRC ([[MAR_20260323.pdf#page=74|MAR22.25, page 74]])

$$\text{DRC}_b = \max\left[\sum_{i \in \text{Long}} RW_i \cdot \text{netJTD}_i - \text{HBR} \times \sum_{i \in \text{Short}} RW_i \cdot |\text{netJTD}_i|,\; 0\right]$$

### Total Non-Sec DRC
$$\text{DRC}_{non\text{-}sec} = \sum_b \text{DRC}_b$$

Simple sum — **no hedging** across buckets (MAR22.26).

---

## 7. DRC for Securitisations (Non-CTP) ([[MAR_20260323.pdf#page=74|MAR22.27–22.35, page 74]])

### Key Differences from Non-Sec DRC:
- **LGD not applied**: JTD = market value of the tranche position (MAR22.27), since LGD is embedded in the risk weights
- **Offsetting**: limited to the **same securitisation exposure** (same underlying pool + same tranche) (MAR22.29)
- **Risk weights**: derived from the **banking book securitisation framework** (CRE40–44) with maturity component set to zero (MAR22.34)
- **Buckets**: defined by asset class × region (MAR22.31)
- **No cross-bucket hedging**: simple sum (MAR22.35)

---

## 8. DRC for Securitisations (CTP) ([[MAR_20260323.pdf#page=76|MAR22.36–22.45, page 76]])

### Key Features:
- Each **index** is its own bucket (e.g. CDX.NA.IG, iTraxx Europe IG) (MAR22.40)
- Non-securitisation hedges are included in CTP DRC and removed from non-sec DRC (MAR22.6)
- **Offsetting** within index: same family, same series, same tranche can offset across maturities (MAR22.39)
- **HBR** is calculated across **all CTP indices combined** (not per-index) (MAR22.44)
- Bucket-level DRC **can be negative** (unlike non-sec) (MAR22.44)

### Aggregation ([[MAR_20260323.pdf#page=79|MAR22.45, page 79]])
$$\text{DRC}_{CTP} = \max\left[\sum_b \left(\max(DRC_b,\,0) + 0.5 \cdot \min(DRC_b,\,0)\right),\; 0\right]$$

> [!note] The 0.5× term accounts for **basis risk** in cross-index hedges — the hedge benefit from short positions is discounted twice (first by HBR, then by the 0.5 factor).

---

## 9. Sovereign Treatment ([[MAR_20260323.pdf#page=68|MAR22.7, page 68]])

Claims on sovereigns, PSEs and MDBs may at **national discretion** carry a **zero** default risk weight, consistent with the credit risk standard (CRE20.7–20.15).

---

## 10. Worked Example — Non-Sec DRC

> [!example] Corporate Bond & CDS Portfolio

### Setup

A bank holds 5 credit exposures, all in the **Corporate bucket**:

| # | Instrument | Obligor | Rating | Seniority | Notional | Market Value | Maturity |
|---|---|---|---|---|---|---|---|
| 1 | Bond (long) | Firm A | BBB | Senior | +100M | 95M | 3y |
| 2 | CDS (short) | Firm A | BBB | Senior | −80M | −82M | 5y |
| 3 | Bond (long) | Firm B | BB | Senior | +50M | 48M | 2y |
| 4 | Equity (long) | Firm C | A | Equity | +30M | 30M | >1y |
| 5 | CDS (short) | Firm D | BBB | Senior | −40M | −38M | 6m |

---

### Step 1 — Gross JTD ([[MAR_20260323.pdf#page=68|MAR22.11, page 68]])

$$\text{JTD} = \text{LGD} \times \text{Notional} + \text{P\&L}$$

| # | LGD | LGD × Notional | P&L (MV − Notional) | JTD (raw) | Long/Short? |
|---|---|---|---|---|---|
| 1 | 75% (senior) | +75M | 95 − 100 = −5M | +70M | Long (max with 0) |
| 2 | 75% (senior) | −60M | −82 − (−80) = −2M | −62M | Short (min with 0) |
| 3 | 75% (senior) | +37.5M | 48 − 50 = −2M | +35.5M | Long |
| 4 | 100% (equity) | +30M | 30 − 30 = 0 | +30M | Long |
| 5 | 75% (senior) | −30M | −38 − (−40) = +2M | −28M | Short |

### Step 2 — Maturity Scaling ([[MAR_20260323.pdf#page=69|MAR22.15, page 69]])

Exposures < 1 year: scale by max(maturity, 3 months) / 1 year.

| # | Maturity | Scale Factor | Scaled JTD |
|---|---|---|---|
| 1 | 3y (≥ 1y) | 1.0 | +70.0M |
| 2 | 5y (≥ 1y) | 1.0 | −62.0M |
| 3 | 2y (≥ 1y) | 1.0 | +35.5M |
| 4 | >1y | 1.0 | +30.0M |
| 5 | 6m (< 1y) | 0.5 | **−14.0M** |

### Step 3 — Net JTD by Obligor ([[MAR_20260323.pdf#page=72|MAR22.19, page 72]])

Offset long/short positions to the **same obligor** (same or lower seniority):

| Obligor | Long JTD | Short JTD | Offset? | Net JTD |
|---|---|---|---|---|
| **Firm A** | +70.0M (bond, senior) | −62.0M (CDS, senior) | ✅ Same seniority | **+8.0M** (net long) |
| **Firm B** | +35.5M | — | No short | **+35.5M** (net long) |
| **Firm C** | +30.0M | — | No short | **+30.0M** (net long) |
| **Firm D** | — | −14.0M | No long | **−14.0M** (net short) |

### Step 4 — Hedge Benefit Ratio ([[MAR_20260323.pdf#page=73|MAR22.23, page 73]])

$$\text{HBR} = \frac{\sum \text{Net Long JTD}}{\sum \text{Net Long JTD} + \sum |\text{Net Short JTD}|}$$

$$\text{HBR} = \frac{8.0 + 35.5 + 30.0}{(8.0 + 35.5 + 30.0) + 14.0} = \frac{73.5}{87.5} = \mathbf{0.840}$$

### Step 5 — Risk-Weighted & Bucket DRC ([[MAR_20260323.pdf#page=74|MAR22.25, page 74]])

| Obligor | Net JTD | Rating | RW | RW × Net JTD |
|---|---|---|---|---|
| Firm A | +8.0M | BBB | 6% | +0.48M |
| Firm B | +35.5M | BB | 15% | +5.325M |
| Firm C | +30.0M | A | 3% | +0.90M |
| Firm D | −14.0M | BBB | 6% | 0.84M (absolute) |

$$\text{DRC}_{corp} = \max\left[\underbrace{(0.48 + 5.325 + 0.90)}_{\text{Weighted long}} - \underbrace{0.840 \times 0.84}_{\text{HBR} \times \text{weighted short}},\; 0\right]$$

$$\text{DRC}_{corp} = \max\left[6.705 - 0.706,\; 0\right] = \mathbf{5.999M}$$

### Step 6 — Total Non-Sec DRC

If the bank has no sovereign or local government bucket exposures:

$$\text{DRC}_{non\text{-}sec} = \text{DRC}_{corp} + \text{DRC}_{sov} + \text{DRC}_{local} = 5.999 + 0 + 0 = \mathbf{5.999M}$$

> [!tip] Key Observations
> 1. **Firm A offset**: The CDS short (−62M) largely offset the bond long (+70M), reducing Firm A's net JTD from 70M to just 8M — a **significant hedge benefit** from having both legs on the same obligor.
> 2. **HBR < 1**: The Firm D short (−14M) gets only 84% recognition as a hedge against different obligors. If the portfolio were 100% long, HBR would be 1.0 (no shorts).
> 3. **Simple sum across buckets**: No diversification across corporate/sovereign/local government buckets.

---

## See Also

- [[FRTB SA — Sensitivities-Based Method]]
- [[FRTB SA — Residual Risk Add-On]]
- [[FRTB SA — CSR Non-Securitisation]]
- [[FRTB Overview]]

