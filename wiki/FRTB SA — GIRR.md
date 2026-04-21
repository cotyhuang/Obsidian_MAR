---
tags: [MAR, FRTB, SbM, GIRR, interest-rate]
sources:
  - "[[raw/MAR_20260323]]"
created: 2026-04-21
---
# FRTB SA — GIRR (General Interest Rate Risk)

> [!info] Regulatory Reference
> Basel MAR21.8(1)–(6), MAR21.19, MAR21.41–21.50
> [[MAR_20260323.pdf#page=26|MAR21.8, page 26]] — [[MAR_20260323.pdf#page=42|MAR21.41–21.50, page 42]]

---

## 1. Risk Factors & Buckets

**Each currency** constitutes a separate GIRR bucket ([[MAR_20260323.pdf#page=42|MAR21.41, page 42]]).

### Delta Risk Factors ([[MAR_20260323.pdf#page=26|MAR21.8, page 26]])
Three types of GIRR delta risk factors:

| Risk Factor                | Dimensions                                           | Term Structure                                             |
| -------------------------- | ---------------------------------------------------- | ---------------------------------------------------------- |
| **Risk-free yield curves** | Per currency × per curve (OIS, BOR, etc.)            | 10 tenors: 0.25y, 0.5y, 1y, 2y, 3y, 5y, 10y, 15y, 20y, 30y |
| **Inflation**              | One flat curve per currency                          | No term structure                                          |
| **Cross-currency basis**   | One of two bases per currency (Curr/USD or Curr/EUR) | No term structure (flat)                                   |

> [!note] Curve Construction
> - OIS and BOR swap curves are considered **two different curves** (MAR21.8(1)(c))
> - BOR curves at different maturities (e.g. 3M Euribor vs 6M Euribor) are **two different curves**
> - Onshore and offshore currency curves are **two different curves**

### Vega Risk Factors (MAR21.8(4))
Implied volatilities of GIRR options defined along **two dimensions**:
- Option maturity: 0.5y, 1y, 3y, 5y, 10y
- Residual maturity of underlying: 0.5y, 1y, 3y, 5y, 10y

Inflation and cross-currency basis vega is considered along the **single dimension** of option maturity only (FAQ4).

### Curvature Risk Factors ([[MAR_20260323.pdf#page=27|MAR21.8(5), page 27]])
- One dimension only: the constructed risk-free yield curve per currency
- **All curves** in a currency are shifted simultaneously (e.g. Eonia + 3M Euribor + 6M Euribor shifted together)
- All tenors shifted in **parallel**
- **No curvature** for inflation or cross-currency basis

---

## 2. Delta Risk Weights ([[MAR_20260323.pdf#page=42|MAR21.42–21.44, page 42]])

### Risk-Free Yield Curve Tenors

| Tenor | 0.25y | 0.5y | 1y | 2y | 3y | 5y | 10y | 15y | 20y | 30y |
|---|---|---|---|---|---|---|---|---|---|---|
| **RW** | 1.7% | 1.7% | 1.6% | 1.3% | 1.2% | 1.1% | 1.1% | 1.1% | 1.1% | 1.1% |

### Other GIRR Risk Factors

| Risk Factor | Risk Weight |
|---|---|
| Inflation | 1.6% |
| Cross-currency basis | 1.6% |

> [!tip] Specified Currency Discount
> For **EUR, USD, GBP, AUD, JPY, SEK, CAD** and the bank's domestic reporting currency, all GIRR risk weights may be divided by **√2** ≈ 0.707, at the bank's discretion ([[MAR_20260323.pdf#page=43|MAR21.44, page 43]]).

---

## 3. Intra-Bucket Correlations $ρ_{kl}$ ([[MAR_20260323.pdf#page=43|MAR21.45–21.49, page 43]])

Three correlation rules within a GIRR bucket:

### Same Tenor, Different Curves
ρ = **99.90%** (MAR21.45)

### Different Tenor, Same Curve ([[MAR_20260323.pdf#page=43|MAR21.46, page 43]])
The correlation formula (footnote 13):
$$\rho_{kl} = \max\left(e^{-\theta \cdot \frac{|T_k - T_l|}{\min(T_k,\, T_l)}},\; 40\%\right) \quad \text{where } \theta = 3\%$$

| | 0.25y | 0.5y | 1y | 2y | 3y | 5y | 10y | 15y | 20y | 30y |
|---|---|---|---|---|---|---|---|---|---|---|
| **0.25y** | 100% | 97.0% | 91.4% | 81.1% | 71.9% | 56.6% | 40.0% | 40.0% | 40.0% | 40.0% |
| **0.5y** | — | 100% | 97.0% | 91.4% | 86.1% | 76.3% | 56.6% | 41.9% | 40.0% | 40.0% |
| **1y** | — | — | 100% | 97.0% | 94.2% | 88.7% | 76.3% | 65.7% | 56.6% | 41.9% |
| **2y** | — | — | — | 100% | 98.5% | 95.6% | 88.7% | 82.3% | 76.3% | 65.7% |
| **3y** | — | — | — | — | 100% | 98.0% | 93.2% | 88.7% | 84.4% | 76.3% |
| **5y** | — | — | — | — | — | 100% | 97.0% | 94.2% | 91.4% | 86.1% |
| **10y** | — | — | — | — | — | — | 100% | 98.5% | 97.0% | 94.2% |
| **15y** | — | — | — | — | — | — | — | 100% | 99.0% | 97.0% |
| **20y** | — | — | — | — | — | — | — | — | 100% | 98.5% |
| **30y** | — | — | — | — | — | — | — | — | — | 100% |

### Different Tenor, Different Curves
ρ = (same-curve correlation) × **99.90%** (MAR21.47)

### Inflation vs Yield Curve
ρ = **40%** (MAR21.48)

### Cross-Currency Basis vs Anything Else
ρ = **0%** (MAR21.49) — zero correlation to yield curves, inflation, and other cross-currency basis.

---

## 4. Inter-Bucket Correlation $γ_{bc}$ ([[MAR_20260323.pdf#page=44|MAR21.50, page 44]])

Cross-currency correlation: γ = **50%**

---

## 5. Three Correlation Scenarios

| Scenario | ρ (intra-bucket) | γ (inter-bucket) |
|---|---|---|
| Medium | As prescribed above | 50% |
| High | min(1, ρ × 1.25) | min(1, 62.5%) |
| Low | ρ × 0.75 | 37.5% |

---

## 6. Sensitivity Definition — PV01 ([[MAR_20260323.pdf#page=31|MAR21.19, page 31]])

$$s_{k,r_t} = \frac{V_i(r_t + 0.0001, cs_t) - V_i(r_t, cs_t)}{0.0001}$$

Where:
- $r_t$ = risk-free yield curve at tenor *t*
- $cs_t$ = credit spread curve at tenor *t*
- $V_i$ = market value of instrument *i*

> [!note] The sensitivity is computed holding credit spreads constant — isolating the pure interest rate component.

---

## 7. Vega Risk Weight ([[MAR_20260323.pdf#page=60|MAR21.92, page 60]])

| Risk Class | Liquidity Horizon | Risk Weight |
|---|---|---|
| GIRR | 60 days | 100% |

Vega sensitivity definition: $\text{Vega}_{k} = vega \times \sigma_{implied}$ (MAR21.25)

---

## 8. Curvature Risk Weight ([[MAR_20260323.pdf#page=64|MAR21.99, page 64]])

The curvature risk weight for GIRR is the **highest delta risk weight** in the bucket = **1.7%** (the 0.25y tenor weight), applied as a parallel shift to all tenors of all risk-free yield curves in that currency.

---

## 9. Vega Intra-Bucket Correlations ([[MAR_20260323.pdf#page=61|MAR21.93, page 61]])

GIRR vega correlations are derived from **two dimensions** — option maturity and underlying maturity:

$$\rho_{kl} = \min\left(\rho_{kl}^{(\text{option})} \times \rho_{kl}^{(\text{underlying})},\; 1\right)$$

### Option Maturity Correlation
$$\rho_{kl}^{(\text{option})} = e^{-\alpha \cdot \frac{|T_k - T_l|}{\min(T_k,\, T_l)}} \quad \text{where } \alpha = 1\%$$

- $T_k$, $T_l$ = maturities of the options, expressed in years

### Underlying Maturity Correlation
$$\rho_{kl}^{(\text{underlying})} = e^{-\alpha \cdot \frac{|T_k^U - T_l^U|}{\min(T_k^U,\, T_l^U)}} \quad \text{where } \alpha = 1\%$$

- $T_k^U$, $T_l^U$ = maturities of the underlying **after** the option maturity, expressed in years

> [!note] Non-GIRR Vega Correlations (MAR21.94)
> For equity, CSR, commodity, and FX risk classes, the vega correlation is:
> $$\rho_{kl} = \min\left(\rho_{kl}^{(\text{delta})} \times \rho_{kl}^{(\text{option})},\; 1\right)$$
> where $\rho_{kl}^{(\text{delta})}$ is the delta correlation for the corresponding risk factors.

---

## 10. Worked Example — GIRR Delta Capital (Medium Scenario)

> [!example] EUR Interest Rate Swap Portfolio — EUR-reporting bank

### Setup

A bank holds three EUR-denominated interest rate positions. EUR is a specified currency, so risk weights are divided by √2 ([[MAR_20260323.pdf#page=43|MAR21.44, page 43]]).

The bank uses a **single risk-free curve** (€STR OIS).

#### Net Sensitivities (PV01, in EUR thousands)

| Tenor            | 2y   | 5y   | 10y  |
| ---------------- | ---- | ---- | ---- |
| **$s_k$ (PV01)** | +500 | −300 | +200 |

_(All other tenors have zero sensitivity)_

---

### Step 1 — Risk Weights (with √2 discount)

| Tenor | Base RW | Adjusted RW |
|---|---|---|
| 2y | 1.3% | 1.3% ÷ √2 = **0.919%** |
| 5y | 1.1% | 1.1% ÷ √2 = **0.778%** |
| 10y | 1.1% | 1.1% ÷ √2 = **0.778%** |

### Step 2 — Weighted Sensitivities

$$WS_{2y} = 500 \times 0.919\% = 4.596$$
$$WS_{5y} = -300 \times 0.778\% = -2.333$$
$$WS_{10y} = 200 \times 0.778\% = 1.556$$

### Step 3 — Correlations (Same Curve)

From the correlation table (MAR21.46):

| Pair | ρ |
|---|---|
| (2y, 5y) | 95.6% |
| (2y, 10y) | 88.7% |
| (5y, 10y) | 97.0% |

### Step 4 — Intra-Bucket Aggregation

$$K_{EUR}^2 = WS_{2y}^2 + WS_{5y}^2 + WS_{10y}^2 + 2\rho_{2,5}\,WS_{2y}\,WS_{5y} + 2\rho_{2,10}\,WS_{2y}\,WS_{10y} + 2\rho_{5,10}\,WS_{5y}\,WS_{10y}$$

| Term | Calculation | Value |
|---|---|---|
| $WS_{2y}^2$ | 4.596² | 21.13 |
| $WS_{5y}^2$ | (−2.333)² | 5.44 |
| $WS_{10y}^2$ | 1.556² | 2.42 |
| $2\rho_{2,5}\,WS_{2y}\,WS_{5y}$ | 2 × 0.956 × 4.596 × (−2.333) | −20.49 |
| $2\rho_{2,10}\,WS_{2y}\,WS_{10y}$ | 2 × 0.887 × 4.596 × 1.556 | 12.69 |
| $2\rho_{5,10}\,WS_{5y}\,WS_{10y}$ | 2 × 0.970 × (−2.333) × 1.556 | −7.06 |
| **Sum** | | **14.13** |

$$K_{EUR} = \sqrt{\max(0,\; 14.13)} = \sqrt{14.13} = \mathbf{3.758}$$

### Step 5 — Cross-Bucket (Single Currency)

Since we only have one currency (EUR), no cross-bucket aggregation:

$$\text{GIRR Delta Capital (medium)} = K_{EUR} = \mathbf{3.758 \text{ (EUR thousands)}}$$

### Step 6 — Three Correlation Scenarios

In practice, repeat steps 3–5 with adjusted correlations:

| Scenario | ρ adjusted | $K_{EUR}$ | Capital |
|---|---|---|---|
| **Medium** | ρ as above | 3.758 | 3,758 |
| **High** | min(1, ρ × 1.25) | 3.818 | 3,818 |
| **Low** | ρ × 0.75 | 4.224 | **4,224** |

$$\text{GIRR Delta Capital} = \max(3{,}758,\; 3{,}818,\; 4{,}224) = \mathbf{4{,}224 \text{ EUR}}$$

> [!tip] Interpretation
> The **low correlation scenario** produces the highest capital here because the portfolio has offsetting positions (long 2y/10y, short 5y). Lower correlations reduce the hedging benefit between these tenors, increasing the capital requirement.

---

## See Also

- [[FRTB SA — Sensitivities-Based Method]]
- [[FRTB SA — CSR Non-Securitisation]]
- [[FRTB SA — FX Risk]]
- [[FRTB Overview]]

