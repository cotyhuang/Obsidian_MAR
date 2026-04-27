---
tags: [MAR, FRTB, SbM, SA, BaselFramework]
sources:
  - "[[raw/MAR_20260323]]"
  - "[[raw/CRR_20260101.pdf]]"
created: 2026-04-21
---
# FRTB SA — Sensitivities-Based Method

> [!info] Regulatory Reference
> Basel MAR21 — Standardised approach: sensitivities-based method (effective 01 Jan 2023).
> [[MAR_20260323.pdf#page=19|MAR21, page 19]]
> EU CRR3 Article 325e–325h, 325ay–325az, 325g
> [[CRR_20260101.pdf#page=474|CRR Art. 325e–325h, page 474]]

---

## 1. Overview

The **Sensitivities-Based Method (SBM)** is the core component of the FRTB [[FRTB Overview|Standardised Approach (SA)]] for market risk capital. It calculates capital requirements based on the sensitivities of instruments to prescribed risk factors across seven risk classes. ([[MAR_20260323.pdf#page=16|MAR20, page 16]] / [[CRR_20260101.pdf#page=466|CRR Art. 325(1)]])

The SA capital requirement is the **simple sum** of three components ([[MAR_20260323.pdf#page=17|MAR20.4, page 17]] / [[CRR_20260101.pdf#page=466|CRR Art. 325(1)]]):

$$\text{SA Capital} = \text{SBM} + \text{DRC} + \text{RRAO}$$

- **SBM** — Sensitivities-Based Method (this page)
- **[[FRTB SA — Default Risk Charge|DRC]]** — Default Risk Capital Requirement
- **[[FRTB SA — Residual Risk Add-On|RRAO]]** — Residual Risk Add-On

---

## 2. The Seven Risk Classes

The SBM defines seven risk classes ([[MAR_20260323.pdf#page=20|MAR21.1, page 20]] / [[CRR_20260101.pdf#page=474|CRR Art. 325e]]):

| # | Risk Class | Wiki Page | MAR Reference |
|---|---|---|---|
| 1 | General Interest Rate Risk (GIRR) | [[FRTB SA — GIRR]] | MAR21.8, 21.41–21.50 |
| 2 | Credit Spread Risk — Non-Securitisation | [[FRTB SA — CSR Non-Securitisation]] | MAR21.9, 21.51–21.57 |
| 3 | CSR — Securitisation (non-CTP) | [[FRTB SA — CSR Securitisation]] | MAR21.10, 21.62–21.71 |
| 4 | CSR — Securitisation (CTP) | [[FRTB SA — CSR CTP]] | MAR21.11, 21.58–21.61 |
| 5 | Equity Risk | [[FRTB SA — Equity Risk]] | MAR21.12, 21.72–21.80 |
| 6 | Commodity Risk | [[FRTB SA — Commodity Risk]] | MAR21.13, 21.81–21.85 |
| 7 | Foreign Exchange (FX) Risk | [[FRTB SA — FX Risk]] | MAR21.14, 21.86–21.89 |

---

## 3. Three Risk Measures

For each risk class, three risk measures are calculated (MAR20.4(1)):

| Risk Measure | Description | Applicable Instruments |
|---|---|---|
| **Delta** | Linear sensitivity to risk factors | All instruments subject to SBM |
| **Vega** | Sensitivity to implied volatility | Instruments with optionality |
| **Curvature** | Non-linear loss beyond delta | Instruments with optionality (may include all) |

---

## 4. Key Terminology ([[MAR_20260323.pdf#page=20|MAR21.1, page 20]] / [[CRR_20260101.pdf#page=474|CRR Art. 325d]])

- **Risk factor**: A variable (e.g. equity price, interest rate tenor) affecting instrument value
- **Bucket**: A set of risk factors grouped by common characteristics
- **Risk position**: The portion of instrument risk related to a risk factor
- **Weighted sensitivity (WS)**: Net sensitivity × risk weight

---

## 5. Delta & Vega Aggregation Formula

The step-by-step process for delta and vega ([[MAR_20260323.pdf#page=21|MAR21.4, page 21]] / [[CRR_20260101.pdf#page=475|CRR Art. 325f]]):

### Step 1 — Net Sensitivities
For each risk factor *k*, net all sensitivities across the portfolio:
$$s_k = \sum_i s_{k,i}$$

### Step 2 — Weighted Sensitivities
$$WS_k = s_k \times RW_k$$

### Step 3 — Intra-Bucket Aggregation
Aggregate within each bucket *b* using correlations ρ_{kl}:

$$K_b = \sqrt{\max\left(0,\;\sum_k WS_k^2 + \sum_{k \neq l} \rho_{kl} \cdot WS_k \cdot WS_l\right)}$$

### Step 4 — Cross-Bucket Aggregation
Aggregate across buckets using correlations γ_{bc}:

$$\text{Risk Class Capital} = \sqrt{\sum_b K_b^2 + \sum_{b \neq c} \gamma_{bc} \cdot S_b \cdot S_c}$$

Where:
- $S_b = \sum_k WS_k$ for all risk factors in bucket *b*
- $S_c = \sum_k WS_k$ for all risk factors in bucket *c*

> [!note] Alternative S_b Formula
> If the above produces a negative number under the square root, an alternative specification is used ([[MAR_20260323.pdf#page=22|MAR21.4(5), page 22]]):
> $$S_b = \max\left[\min\left(\sum_{k \in b} WS_k,\; K_b\right),\; -K_b\right]$$

---

## 6. Curvature Aggregation Formula

Curvature differs from delta/vega in that it applies **upward and downward shocks** ([[MAR_20260323.pdf#page=23|MAR21.5, page 23]] / [[CRR_20260101.pdf#page=477|CRR Art. 325g]]):

### Step 1 — Compute Curvature Risk Charges
For each curvature risk factor *k*, aggregate across all instruments *i* ([[MAR_20260323.pdf#page=24|MAR21.5(2), page 24]]):

$$CVR_k^{+} = -\sum_i \left\{ V_i\!\left(x_k^{RW^+}\right) - V_i(x_k) - RW_k^{curv} \cdot s_{ik} \right\}$$
$$CVR_k^{-} = -\sum_i \left\{ V_i\!\left(x_k^{RW^-}\right) - V_i(x_k) + RW_k^{curv} \cdot s_{ik} \right\}$$

Where:
- $x_k$ = current level of risk factor *k*
- $V_i(x_k)$ = price of instrument *i* at the current level
- $RW_k^{curv}$ = curvature risk weight (shock size)
- $s_{ik}$ = delta sensitivity of instrument *i* w.r.t. the delta risk factor corresponding to curvature risk factor *k*

### Step 2 — Intra-Bucket Aggregation ([[MAR_20260323.pdf#page=24|MAR21.5(3), page 24]])
$$K_b = \max(K_b^{+},\; K_b^{-})$$

Where each scenario is aggregated as:
$$K_b^{+} = \sqrt{\max\left(0,\;\sum_k \max(CVR_k^{+},\,0)^2 + \sum_{k \neq l} \rho_{kl}\, CVR_k^{+}\, CVR_l^{+}\, \psi(CVR_k^{+},\, CVR_l^{+})\right)}$$

The **ψ function** ([[MAR_20260323.pdf#page=24|MAR21.5(3), page 24]]):
$$\psi(x, y) = \begin{cases} 0 & \text{if } x < 0 \text{ and } y < 0 \\ 1 & \text{otherwise} \end{cases}$$

Correlations: $\rho_{kl}$ are the **squared** delta correlations ($\rho_{kl}^{delta}$)² for the corresponding risk class.

### Step 3 — Cross-Bucket Aggregation ([[MAR_20260323.pdf#page=24|MAR21.5(4), page 24]])
$$\text{Curvature Risk} = \sqrt{\max\left(0,\;\sum_b K_b^2 + \sum_{b \neq c} \gamma_{bc}\, S_b\, S_c\, \psi(S_b, S_c)\right)}$$

Where $S_b = \sum_k CVR_k^{+}$ (or $CVR_k^{-}$) for the selected scenario direction, and $\gamma_{bc}$ are the **squared** delta cross-bucket correlations.

---

## 7. Three Correlation Scenarios ([[MAR_20260323.pdf#page=25|MAR21.6–21.7, page 25]] / [[CRR_20260101.pdf#page=480|CRR Art. 325h]])

> [!important] This is a defining feature of the FRTB SA.

The final SBM capital is the **maximum** of three correlation scenarios:

| Scenario | ρ (intra-bucket) | γ (cross-bucket) |
|---|---|---|
| **Medium** | ρ as prescribed | γ as prescribed |
| **High** | min(1, ρ × 1.25) | min(1, γ × 1.25) |
| **Low** | ρ × 0.75 | γ × 0.75 |

$$\text{SBM Capital} = \max\left(\text{Capital}^{high},\; \text{Capital}^{medium},\; \text{Capital}^{low}\right)$$

Within each scenario, the bank sums delta + vega + curvature across all seven risk classes.

---

## 8. Sensitivity Definitions ([[MAR_20260323.pdf#page=29|MAR21.15–21.30, page 29]] / [[CRR_20260101.pdf#page=475|CRR Art. 325f]])

All sensitivities must be expressed in the bank's **reporting currency** ([[MAR_20260323.pdf#page=29|MAR21.15, page 29]]), and computed using the bank's **independent risk control unit's pricing models** ([[MAR_20260323.pdf#page=30|MAR21.17, page 30]]).

| Risk Measure | Sensitivity Definition |
|---|---|
| Delta GIRR | PV01 — shift interest rate by 1bp (MAR21.19) |
| Delta CSR | CS01 — shift credit spread by 1bp (MAR21.20) |
| Delta Equity | 1% relative shift in equity spot price (MAR21.21) |
| Delta Commodity | 1% relative shift in commodity spot price (MAR21.23) |
| Delta FX | 1% relative shift in exchange rate (MAR21.24) |
| Vega (all) | Multiply vega × implied volatility (MAR21.25) |

---

## 9. Vega Risk Weights ([[MAR_20260323.pdf#page=60|MAR21.92, page 60]] / [[CRR_20260101.pdf#page=525|CRR Art. 325ay]])

The vega risk weight formula (footnote 24):

$$RW_k = \min\left(RW_\sigma \cdot \frac{\sqrt{LH_{risk\_class}}}{\sqrt{10}},\; 100\%\right) \quad \text{where } RW_\sigma = 55\%$$

| Risk Class | LH (days) | Calculation | Risk Weight |
|---|---|---|---|
| GIRR | 60 | 55% × √(60/10) = 55% × 2.449 | 100% (capped) |
| CSR non-securitisation | 120 | 55% × √(120/10) = 55% × 3.464 | 100% (capped) |
| CSR securitisation (CTP) | 120 | 55% × √12 | 100% (capped) |
| CSR securitisation (non-CTP) | 120 | 55% × √12 | 100% (capped) |
| Equity (large cap & indices) | 20 | 55% × √(20/10) = 55% × 1.414 | **77.78%** |
| Equity (small cap & other) | 60 | 55% × √6 | 100% (capped) |
| Commodity | 120 | 55% × √12 | 100% (capped) |
| FX | 40 | 55% × √(40/10) = 55% × 2.0 | 100% (capped) |

---

## 10. Worked Example — FX Vega Capital

> [!example] EUR/USD 6-month option — USD-reporting bank

**Setup**: A bank holds a EUR/USD call option with 6-month maturity. Compute the vega capital charge.

**Step 1 — Identify risk factors**: FX Vega has a single dimension — option maturity. The option maps to the **0.5y** tenor point.

**Step 2 — Compute vega sensitivity** ([[MAR_20260323.pdf#page=32|MAR21.25, page 32]]):
$$s_k = \text{vega} \times \sigma_k$$

Assume:
- Vega (option greek) = 250,000 USD per 1% vol move
- Implied volatility $\sigma_k$ = 12% (0.12)

$$s_k = 250{,}000 \times 0.12 = 30{,}000$$

**Step 3 — Apply vega risk weight** (from §9 above):
FX vega risk weight = 100% (LH = 40 days, capped at 100%).

$$WS_k = s_k \times RW_k = 30{,}000 \times 100\% = 30{,}000$$

**Step 4 — Intra-bucket aggregation**: Each FX pair is its own bucket with one vega risk factor (at this tenor). If the bank has only one EUR/USD option:

$$K_{EUR} = |WS_k| = 30{,}000$$

If the bank has a second option (e.g. 1y maturity with $WS_{1y} = -15{,}000$), the intra-bucket correlation ρ between the 0.5y and 1y tenor points comes from MAR21.93:

$$\rho = \min\left(e^{-\alpha \cdot \frac{|T_k - T_l|}{\min(T_k, T_l)}},\; 1\right) \quad \alpha = 0.01$$

$$\rho = e^{-0.01 \times \frac{|0.5 - 1.0|}{0.5}} = e^{-0.01} \approx 0.99$$

$$K_{EUR} = \sqrt{30{,}000^2 + (-15{,}000)^2 + 2 \times 0.99 \times 30{,}000 \times (-15{,}000)}$$
$$= \sqrt{900{,}000{,}000 + 225{,}000{,}000 - 891{,}000{,}000} = \sqrt{234{,}000{,}000} \approx 15{,}297$$

**Step 5 — Cross-bucket aggregation**: With only EUR exposure:
$$\text{FX Vega Capital} = K_{EUR} = 15{,}297$$

**Step 6 — Three scenarios**: Repeat with ρ scaled by ×1.25 (high) and ×0.75 (low). Take the max.

> [!note] This example uses the FX risk class. The same aggregation logic applies to all seven risk classes — only the risk weights and correlations differ.

---

## 11. Curvature Risk Weights ([[MAR_20260323.pdf#page=63|MAR21.98–21.99, page 63]] / [[CRR_20260101.pdf#page=477|CRR Art. 325g]])

| Risk Class | Curvature Risk Weight |
|---|---|
| FX, Equity | Equal to the delta risk weight (relative shift) |
| GIRR, CSR, Commodity | Parallel shift using the **highest** delta risk weight in the bucket |

> [!note] FX Curvature Scalar
> For FX options that do not reference the bank's reporting currency, curvature risk charges may be divided by 1.5 (MAR21.98).

---

## 12. Treatment of Index Instruments ([[MAR_20260323.pdf#page=36|MAR21.31–21.34, page 36]] / [[CRR_20260101.pdf#page=480|CRR Art. 325i]])

- **Look-through** is the default for indices and multi-underlying options
- Banks may opt **not** to look through for listed, widely recognised equity/credit indices meeting criteria (≥20 constituents, no single name >25%, top 10% <60%, market cap ≥ USD 40bn) — [[MAR_20260323.pdf#page=37|MAR21.31, page 37]]
- When look-through is not applied, the index is assigned to a sector-specific bucket or an index bucket — [[MAR_20260323.pdf#page=38|MAR21.33, page 38]]

---

## See Also

- [[FRTB Overview]]
- [[FRTB SA — GIRR]]
- [[FRTB SA — CSR Non-Securitisation]]
- [[FRTB SA — CSR Securitisation]]
- [[FRTB SA — CSR CTP]]
- [[FRTB SA — Equity Risk]]
- [[FRTB SA — Commodity Risk]]
- [[FRTB SA — FX Risk]]
- [[FRTB SA — Default Risk Charge]]
- [[FRTB SA — Residual Risk Add-On]]
- [[FRTB SA — Basel vs CRR3 Comparison]]
- [[ISDA CRIF — FRTB-SA Data Standards]]
