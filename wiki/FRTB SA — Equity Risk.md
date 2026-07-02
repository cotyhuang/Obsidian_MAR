---
tags: [MAR, FRTB, SbM, equity]
sources:
  - "[[raw/MAR_20260323]]"
  - "[[raw/CRR_20260101.pdf]]"
created: 2026-04-21
---
# FRTB SA — Equity Risk

> [!info] Regulatory Reference
> Basel MAR21.12, MAR21.21–21.22, MAR21.72–21.80
> [[MAR_20260323.pdf#page=29|MAR21.12, page 29]] — [[MAR_20260323.pdf#page=53|MAR21.72–21.80, page 53]]
> EU CRR3 Article 325p, 325ap–325ar
> [[CRR_20260101.pdf#page=490|CRR Art. 325p, page 490]] — [[CRR_20260101.pdf#page=519|CRR Art. 325ap–325ar, page 519]]

---

## 1. Risk Factors ([[MAR_20260323.pdf#page=29|MAR21.12, page 29]] / [[CRR_20260101.pdf#page=490|CRR Art. 325p]])

| Type | Delta | Vega | Curvature |
|---|---|---|---|
| **Equity spot price** | ✓ | ✓ (implied vol) | ✓ |
| **Equity repo rate** | ✓ | ✗ | ✗ |

### Vega Risk Factors
Implied volatilities of options referencing equity spot prices, along **one dimension** — option maturity: 0.5y, 1y, 3y, 5y, 10y.

---

## 2. Buckets ([[MAR_20260323.pdf#page=53|MAR21.72, page 53]] / [[CRR_20260101.pdf#page=519|CRR Art. 325ap]])

13 buckets along **market cap** × **economy** × **sector**:

| Bucket | Market Cap | Economy  | Sector                                           |
| ------ | ---------- | -------- | ------------------------------------------------ |
| 1      | Large      | Emerging | Consumer goods, healthcare, transport, utilities |
| 2      | Large      | Emerging | Telecom, industrials                             |
| 3      | Large      | Emerging | Basic materials, energy, agriculture, mining     |
| 4      | Large      | Emerging | Financials, real estate, technology              |
| 5      | Large      | Advanced | Consumer goods, healthcare, transport, utilities |
| 6      | Large      | Advanced | Telecom, industrials                             |
| 7      | Large      | Advanced | Basic materials, energy, agriculture, mining     |
| 8      | Large      | Advanced | Financials, real estate, technology              |
| 9      | Small      | Emerging | All sectors (buckets 1–4)                        |
| 10     | Small      | Advanced | All sectors (buckets 5–8)                        |
| 11     | —          | —        | Other sector                                     |
| 12     | —          | —        | Large cap, advanced economy indices              |
| 13     | —          | —        | Other equity indices                             |

### Key Definitions
- **Large cap**: market capitalisation ≥ **USD 2 billion** (MAR21.74)
- **Small cap**: market capitalisation < USD 2 billion
- **Advanced economies** (MAR21.75): Canada, US, Mexico, euro area, UK, Norway, Sweden, Denmark, Switzerland, Japan, Australia, New Zealand, Singapore, Hong Kong SAR

---

## 3. Delta Risk Weights ([[MAR_20260323.pdf#page=55|MAR21.77, page 55]] / [[CRR_20260101.pdf#page=519|CRR Art. 325ap]])

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

## 4. Intra-Bucket Correlations ρ ([[MAR_20260323.pdf#page=55|MAR21.78, page 55]] / [[CRR_20260101.pdf#page=520|CRR Art. 325aq]])

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

## 5. Inter-Bucket Correlations γ_{bc} ([[MAR_20260323.pdf#page=56|MAR21.80, page 56]] / [[CRR_20260101.pdf#page=521|CRR Art. 325ar]])

| Condition | γ |
|---|---|
| Both buckets in 1–10 | **15%** |
| Either bucket is 11 | **0%** |
| Buckets 12 and 13 (both are index buckets) | **75%** |
| Otherwise | **45%** |

---

## 6. Sensitivity Definitions

### Delta Equity Spot ([[MAR_20260323.pdf#page=32|MAR21.21, page 32]] / [[CRR_20260101.pdf#page=475|CRR Art. 325f]])
$$s_k = \frac{V_i(1.01 \cdot EQ_k) - V_i(EQ_k)}{0.01}$$

### Delta Equity Repo Rate ([[MAR_20260323.pdf#page=33|MAR21.22, page 33]] / [[CRR_20260101.pdf#page=475|CRR Art. 325f]])
$$s_k = \frac{V_i(RepoTS_k + 0.0001) - V_i(RepoTS_k)}{0.0001}$$

---

## 7. Vega Risk Weight ([[MAR_20260323.pdf#page=60|MAR21.92, page 60]] / [[CRR_20260101.pdf#page=525|CRR Art. 325ay]])

| Sub-class | Liquidity Horizon | Risk Weight |
|---|---|---|
| Large cap & indices (buckets 1–8, 12–13) | 20 days | 77.78% |
| Small cap & other (buckets 9–11) | 60 days | 100% |

---

## 8. Curvature Risk Weight ([[MAR_20260323.pdf#page=63|MAR21.98, page 63]] / [[CRR_20260101.pdf#page=477|CRR Art. 325g]])

The curvature risk weight = the **delta risk weight** for equity spot (relative shift). No curvature for equity repo rates.

---

## 9. Worked Example — Equity Curvature

> [!example] Two Equity Options — Bucket 8 (Large Cap, Advanced, Financials)

### Setup

A bank holds two options in bucket 8 (RW = 50%):

| Position | Underlying | Current Price | Delta Sensitivity | Option MV |
|---|---|---|---|---|
| Call option (long) | Stock X | $100 | s_X = +$2,000,000 | $5.2M |
| Put option (long) | Stock Y | $80 | s_Y = −$1,500,000 | $3.1M |

Both stocks are in bucket 8 (large cap, advanced economy, financials). The intra-bucket correlation for different issuers in bucket 8 is ρ = 25%.

### Step 1 — Apply Curvature Shocks ([[MAR_20260323.pdf#page=63|MAR21.98, page 63]])

For equity, the curvature risk weight = delta risk weight = **50%** (relative shift).

**Stock X** (shift ±50%):

| Scenario | Shocked Price | Repriced MV | ΔMV | Delta Offset | CVR |
|---|---|---|---|---|---|
| Up (+50%) | $150 | $28.5M | +$23.3M | −RW × s_X = −0.50 × 2.0M = −$1.0M | −(23.3 − 1.0) = **−22.3M** |
| Down (−50%) | $50 | $0.1M | −$5.1M | +RW × s_X = +0.50 × 2.0M = +$1.0M | −(−5.1 + 1.0) = **+4.1M** |

**Stock Y** (shift ±50%):

| Scenario | Shocked Price | Repriced MV | ΔMV | Delta Offset | CVR |
|---|---|---|---|---|---|
| Up (+50%) | $120 | $0.4M | −$2.7M | −RW × s_Y = −0.50 × (−1.5M) = +$0.75M | −(−2.7 + 0.75) = **+1.95M** |
| Down (−50%) | $40 | $18.2M | +$15.1M | +RW × s_Y = +0.50 × (−1.5M) = −$0.75M | −(15.1 − 0.75) = **−14.35M** |

> [!note] Formula reminder
> $CVR_k^{+} = -\{V(x^{up}) - V(x) - RW \cdot s_k\}$ — see [[FRTB SA — Sensitivities-Based Method#Step 1 — Compute Curvature Risk Charges|SBM §6]]

### Step 2 — Intra-Bucket Aggregation ([[MAR_20260323.pdf#page=24|MAR21.5(3), page 24]])

**Upward scenario** ($CVR^+$):
- $CVR_X^+ = -22.3$ (negative)
- $CVR_Y^+ = +1.95$ (positive)
- $\psi(CVR_X^+, CVR_Y^+) = 1$ (not both negative)

$$K_b^{+} = \sqrt{\max\left(0,\; \max(-22.3, 0)^2 + \max(1.95, 0)^2 + 2 \times 0.25 \times (-22.3) \times 1.95 \times 1\right)}$$
$$= \sqrt{\max\left(0,\; 0 + 3.80 + (-21.74)\right)} = \sqrt{\max(0,\; -17.94)} = \mathbf{0}$$

**Downward scenario** ($CVR^-$):
- $CVR_X^- = +4.1$ (positive)
- $CVR_Y^- = -14.35$ (negative)
- $\psi(CVR_X^-, CVR_Y^-) = 1$ (not both negative)

$$K_b^{-} = \sqrt{\max\left(0,\; 4.1^2 + 0 + 2 \times 0.25 \times 4.1 \times (-14.35) \times 1\right)}$$
$$= \sqrt{\max\left(0,\; 16.81 + (-29.44)\right)} = \sqrt{\max(0,\; -12.63)} = \mathbf{0}$$

### Step 3 — Bucket Capital

$$K_b = \max(K_b^+,\; K_b^-) = \max(0,\; 0) = \mathbf{0}$$

> [!tip] Interpretation
> Both scenarios produce **zero curvature capital** for this bucket. This happens because the long call (Stock X) and long put (Stock Y) are **natural hedges** — one gains under upward shocks while the other gains under downward shocks. The positive CVR from one offset the negative CVR from the other, and after the max(0,...) floor, the capital is zero.
>
> In practice, if both options were on the **same stock** (ρ = 99.9%), the netting would be even stronger. Conversely, if they were in **different buckets** (ρ → γ²), the hedge would be less effective.

---

## See Also

- [[FRTB SA — Sensitivities-Based Method]]
- [[FRTB SA — Commodity Risk]]
- [[FRTB SA — FX Risk]]
- [[FRTB SA — Default Risk Charge]]

