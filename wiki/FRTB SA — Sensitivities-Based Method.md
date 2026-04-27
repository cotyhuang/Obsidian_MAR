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

## 5. Conceptual Foundation — Why the Formulas Look This Way

> [!tip] For business users
> The SBM formulas may look complex, but they rest on a single, well-known idea from statistics: **portfolio variance**. If you understand that a diversified portfolio is less risky than the sum of its parts, you already understand the core logic.

### 5.1 The "Portfolio Standard Deviation" Analogy

In **Modern Portfolio Theory** (Markowitz, 1952), the risk of a portfolio of two assets is:

$$\sigma_{portfolio} = \sqrt{\sigma_A^2 + \sigma_B^2 + 2\,\rho_{AB}\,\sigma_A\,\sigma_B}$$

Where $\sigma_A$, $\sigma_B$ are individual risks (standard deviations) and $\rho_{AB}$ is the correlation between them.

**The SBM intra-bucket formula is exactly this** — just extended to *n* risk factors instead of two:

$$K_b = \sqrt{\sum_k WS_k^2 + \sum_{k \neq l} \rho_{kl} \cdot WS_k \cdot WS_l}$$

| Portfolio Theory | SBM Equivalent |
|---|---|
| Asset risk ($\sigma$) | Weighted sensitivity ($WS_k$) |
| Correlation ($\rho$) | Prescribed correlation ($\rho_{kl}$) |
| Portfolio std dev ($\sigma_p$) | Bucket capital ($K_b$) |

**What this means in practice:**
- If all your positions move in the same direction ($\rho = 1$), capital = the simple sum of all $WS_k$ → **no diversification benefit**.
- If positions move independently ($\rho = 0$), capital = $\sqrt{\text{sum of squares}}$ → **some diversification**.
- If positions offset each other ($\rho < 0$ or opposite-sign $WS$), capital shrinks → **hedging benefit**.

### 5.2 Why Square Root? Why Not Just Add Up Risks?

Adding risks linearly ($K = WS_1 + WS_2 + ...$) would assume **perfect correlation** — every risk factor moves in lockstep, all the time. This is overly conservative.

The square-root formula reflects a statistical reality: **independent risks don't fully stack**. Rolling two dice doesn't give you twice the uncertainty of rolling one. This is the mathematical basis for diversification.

### 5.3 Why the $\max(0, ...)$ Inside the Square Root?

Sometimes, heavily hedged positions can produce a **negative number** inside the square root (variance). Since negative variance has no physical meaning (you can't take the square root of a negative), the formula floors it at zero. This is a regulatory safeguard — it says: "even if your hedge looks perfect on paper, your minimum capital is zero, not negative."

### 5.4 Two-Level Aggregation — A Tree Structure

The SBM uses a **two-level tree**:

```
Risk Class Capital
├── Bucket 1 (K₁)    ← intra-bucket: correlate risk factors within
├── Bucket 2 (K₂)    ← intra-bucket: correlate risk factors within
├── ...
└── Bucket n (Kₙ)
    └── Cross-bucket: correlate buckets using γ
```

**Level 1 (intra-bucket)**: Group similar risk factors (e.g. all EUR interest rate tenors) and aggregate them using within-group correlations ($\rho$).

**Level 2 (cross-bucket)**: Treat each bucket's capital as a single "super-asset" and aggregate across buckets using between-group correlations ($\gamma$). The maths is the same portfolio variance formula, just applied at a higher level.

---

## 6. Delta & Vega Aggregation Formula

The step-by-step process for delta and vega ([[MAR_20260323.pdf#page=21|MAR21.4, page 21]] / [[CRR_20260101.pdf#page=475|CRR Art. 325f]]):

### Step 1 — Net Sensitivities
For each risk factor *k*, net all sensitivities across the portfolio:
$$s_k = \sum_i s_{k,i}$$

### Step 2 — Weighted Sensitivities
$$WS_k = s_k \times RW_k$$

> [!tip] Intuition
> Think of **sensitivity** ($s_k$) as *how exposed you are* to a risk factor, and the **risk weight** ($RW_k$) as *how volatile the regulator believes that factor is*. Multiplying them gives you the **capital-at-risk** for that factor — your exposure scaled by its assumed severity. It's like saying: "If interest rates move by the amount the regulator considers a bad day, how much would I lose?"

### Step 3 — Intra-Bucket Aggregation
Aggregate within each bucket *b* using correlations ρ_{kl}:

$$K_b = \sqrt{\max\left(0,\;\sum_k WS_k^2 + \sum_{k \neq l} \rho_{kl} \cdot WS_k \cdot WS_l\right)}$$

> [!tip] Intuition — Portfolio Standard Deviation
> This is the **Markowitz portfolio variance formula** (see §5.1 above). Each $WS_k$ is treated like an asset's risk contribution. The $\rho_{kl}$ terms capture how risk factors move together. If you hold a long EUR 5Y position and a short EUR 2Y position, the high correlation between these tenors means they partially offset — giving you a **lower $K_b$** than simply adding the two $|WS|$ values.
>
> **Numeric intuition**: two risk factors with $WS = 100$ each:
> - Perfect correlation ($\rho = 1$): $K = \sqrt{100^2 + 100^2 + 2(1)(100)(100)} = 200$ → no benefit
> - Zero correlation ($\rho = 0$): $K = \sqrt{100^2 + 100^2} \approx 141$ → 29% less capital
> - Perfect offset ($\rho = 1$, opposite signs $+100, -100$): $K = 0$ → fully hedged

### Step 4 — Cross-Bucket Aggregation
Aggregate across buckets using correlations $γ_{bc}$:

$$\text{Risk Class Capital} = \sqrt{\sum_b K_b^2 + \sum_{b \neq c} \gamma_{bc} \cdot S_b \cdot S_c}$$

Where:
- $S_b = \sum_k WS_k$ for all risk factors in bucket *b*
- $S_c = \sum_k WS_k$ for all risk factors in bucket *c*

> [!tip] Intuition — Same Formula, Higher Level
> This is the **same portfolio variance logic** applied one level up. Now each *bucket* is an "asset" with:
> - Its own risk ($K_b$) — from Step 3
> - Its net direction ($S_b$) — the sum of weighted sensitivities (are you net long or net short in this bucket?)
>
> The $\gamma_{bc}$ correlations capture cross-bucket diversification. For example, if your equity energy bucket ($b$) and commodity oil bucket ($c$) are highly correlated ($\gamma = 0.4$), losses in one are likely to accompany losses in the other — so the formula grants less diversification benefit.
>
> **Why use $S_b$ instead of $K_b$ in the cross-terms?** Because $K_b$ is always positive (it's a magnitude), but cross-bucket diversification depends on **direction** — are you long or short? $S_b$ preserves the sign, allowing opposite-directional buckets to offset each other.

> [!note] Alternative S_b Formula
> If the above produces a negative number under the square root, an alternative specification is used ([[MAR_20260323.pdf#page=22|MAR21.4(5), page 22]]):
> $$S_b = \max\left[\min\left(\sum_{k \in b} WS_k,\; K_b\right),\; -K_b\right]$$
>
> **Why cap $S_b$ at $\pm K_b$?** This prevents a single bucket's hedging benefit from exceeding its own standalone risk. In plain English: "a bucket can't reduce the total capital by more than the amount of risk it contains."

---

## 7. Curvature Aggregation Formula

Curvature differs from delta/vega in that it applies **upward and downward shocks** ([[MAR_20260323.pdf#page=23|MAR21.5, page 23]] / [[CRR_20260101.pdf#page=477|CRR Art. 325g]]):

> [!tip] Intuition — Why Curvature Exists (Taylor Series / Convexity)
> **Delta** captures the *first-order* (linear) effect of a market move. But many instruments — especially **options** — have curved payoffs: a 10% drop in the underlying hurts more than a 10% rise helps. Delta alone misses this asymmetry.
>
> Mathematically, this comes from the **Taylor series expansion** of a price function:
>
> $$V(x + \Delta x) \approx V(x) + \underbrace{\frac{\partial V}{\partial x} \cdot \Delta x}_{\text{Delta (1st order)}} + \underbrace{\frac{1}{2} \frac{\partial^2 V}{\partial x^2} \cdot (\Delta x)^2}_{\text{Curvature (2nd order)}} + \cdots$$
>
> In options language, the second-order term is **gamma** — how much delta itself changes as the market moves. Curvature capital captures this *additional* loss beyond what delta predicts.
>
> **Business analogy**: If you drive at 60 km/h, delta tells you *where you'll be in one hour* (60 km away). But if you're *accelerating*, the actual distance is greater. Curvature captures that acceleration.

### Step 1 — Compute Curvature Risk Charges
For each curvature risk factor *k*, aggregate across all instruments *i* ([[MAR_20260323.pdf#page=24|MAR21.5(2), page 24]]):

$$CVR_k^{+} = -\sum_i \left\{ V_i\!\left(x_k^{RW^+}\right) - V_i(x_k) - RW_k^{curv} \cdot s_{ik} \right\}$$
$$CVR_k^{-} = -\sum_i \left\{ V_i\!\left(x_k^{RW^-}\right) - V_i(x_k) + RW_k^{curv} \cdot s_{ik} \right\}$$

Where:
- $x_k$ = current level of risk factor *k*
- $V_i(x_k)$ = price of instrument *i* at the current level
- $RW_k^{curv}$ = curvature risk weight (shock size)
- $s_{ik}$ = delta sensitivity of instrument *i* w.r.t. the delta risk factor corresponding to curvature risk factor *k*

> [!tip] What the CVR Formula is Actually Doing
> In plain English, the formula says:
> 1. **Bump the market up** (or down) by the curvature risk weight
> 2. **Reprice the instrument** at the bumped level → this is the "full revaluation" P&L
> 3. **Subtract the delta prediction** → what delta *thought* the P&L would be
> 4. **The difference is the curvature loss** → the part delta missed
>
> If the difference is small, the instrument is approximately linear (like a forward) and curvature adds little. If the difference is large, the instrument has significant non-linearity (like a deep out-of-the-money option) and curvature captures that extra risk.

### Step 2 — Intra-Bucket Aggregation ([[MAR_20260323.pdf#page=24|MAR21.5(3), page 24]])
$$K_b = \max(K_b^{+},\; K_b^{-})$$

Where each scenario is aggregated as:
$$K_b^{+} = \sqrt{\max\left(0,\;\sum_k \max(CVR_k^{+},\,0)^2 + \sum_{k \neq l} \rho_{kl}\, CVR_k^{+}\, CVR_l^{+}\, \psi(CVR_k^{+},\, CVR_l^{+})\right)}$$

The **ψ function** ([[MAR_20260323.pdf#page=24|MAR21.5(3), page 24]]):
$$\psi(x, y) = \begin{cases} 0 & \text{if } x < 0 \text{ and } y < 0 \\ 1 & \text{otherwise} \end{cases}$$

> [!tip] Intuition — Why the ψ Function?
> The ψ function is a **conservative guard against false diversification**. If two positions are *both losing money* (both CVR values are negative), the regulator says: "don't assume correlation will help you — just treat them independently." Only when at least one position is profitable does the formula allow the correlation term to operate.
>
> **Business analogy**: In a market crash, everything tends to fall together. The ψ function embodies this: when both positions are hurting, you can't count on diversification to save you.

Correlations: $\rho_{kl}$ are the **squared** delta correlations ($\rho_{kl}^{delta}$)² for the corresponding risk class.

> [!tip] Intuition — Why Squared Correlations?
> Curvature is a **second-order** effect (it depends on the *square* of the move). Since the correlation of squared moves is related to the square of the correlation of first-order moves, the formula squares the delta correlations. This also makes curvature correlations *lower* than delta correlations — reflecting the reality that non-linear risks diversify less reliably than linear ones.

### Step 3 — Cross-Bucket Aggregation ([[MAR_20260323.pdf#page=24|MAR21.5(4), page 24]])
$$\text{Curvature Risk} = \sqrt{\max\left(0,\;\sum_b K_b^2 + \sum_{b \neq c} \gamma_{bc}\, S_b\, S_c\, \psi(S_b, S_c)\right)}$$

Where $S_b = \sum_k CVR_k^{+}$ (or $CVR_k^{-}$) for the selected scenario direction, and $\gamma_{bc}$ are the **squared** delta cross-bucket correlations.

---

## 8. Three Correlation Scenarios ([[MAR_20260323.pdf#page=25|MAR21.6–21.7, page 25]] / [[CRR_20260101.pdf#page=480|CRR Art. 325h]])

> [!important] This is a defining feature of the FRTB SA.

> [!tip] Intuition — Why Stress Correlations?
> Correlations are **not constant** — they change under stress. During the 2008 financial crisis, assets that appeared uncorrelated in normal times suddenly moved together. Conversely, some hedges that were expected to move together broke apart.
>
> The three-scenario approach is the regulator's way of saying: "we don't know what correlations will look like in a crisis, so show us the worst case." This is a form of **model uncertainty** or **correlation ambiguity** — acknowledging that our correlation estimates may be wrong.
>
> | Scenario | What it stress-tests |
> |---|---|
> | **High ρ** | A "herd behaviour" crisis — everything moves together, diversification breaks down |
> | **Medium ρ** | Normal market conditions — calibrated correlations hold |
> | **Low ρ** | A "basis risk" crisis — hedges fail, previously correlated assets decouple |
>
> By taking the **maximum**, the regulator ensures capital covers the worst of all three worlds. This is conceptually similar to **stress testing** but applied specifically to the correlation structure of the portfolio.

The final SBM capital is the **maximum** of three correlation scenarios:

| Scenario | ρ (intra-bucket) | γ (cross-bucket) |
|---|---|---|
| **Medium** | ρ as prescribed | γ as prescribed |
| **High** | min(1, ρ × 1.25) | min(1, γ × 1.25) |
| **Low** | ρ × 0.75 | γ × 0.75 |

$$\text{SBM Capital} = \max\left(\text{Capital}^{high},\; \text{Capital}^{medium},\; \text{Capital}^{low}\right)$$

Within each scenario, the bank sums delta + vega + curvature across all seven risk classes.

---

## 9. Sensitivity Definitions ([[MAR_20260323.pdf#page=29|MAR21.15–21.30, page 29]] / [[CRR_20260101.pdf#page=475|CRR Art. 325f]])

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

## 10. Vega Risk Weights ([[MAR_20260323.pdf#page=60|MAR21.92, page 60]] / [[CRR_20260101.pdf#page=525|CRR Art. 325ay]])

The vega risk weight formula (footnote 24):

$$RW_k = \min\left(RW_\sigma \cdot \frac{\sqrt{LH_{risk\_class}}}{\sqrt{10}},\; 100\%\right) \quad \text{where } RW_\sigma = 55\%$$

> [!tip] Intuition — What Drives Vega Risk Weights?
> The formula scales a **base volatility shock** ($RW_\sigma = 55\%$) by how long it would take to exit the position (the **Liquidity Horizon**, LH).
>
> The idea is simple: if a risk takes longer to unwind, a bank is exposed to volatility for longer, so the risk weight should be higher. The square root reflects the statistical principle that **risk scales with the square root of time** (from Brownian motion / random walk theory — the same reason daily VaR is scaled by $\sqrt{10}$ to get 10-day VaR).
>
> The cap at 100% prevents extreme scenarios where the formula would imply implied volatility could more than double.

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

## 11. Worked Example — FX Vega Capital

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

## 12. Curvature Risk Weights ([[MAR_20260323.pdf#page=63|MAR21.98–21.99, page 63]] / [[CRR_20260101.pdf#page=477|CRR Art. 325g]])

| Risk Class | Curvature Risk Weight |
|---|---|
| FX, Equity | Equal to the delta risk weight (relative shift) |
| GIRR, CSR, Commodity | Parallel shift using the **highest** delta risk weight in the bucket |

> [!note] FX Curvature Scalar
> For FX options that do not reference the bank's reporting currency, curvature risk charges may be divided by 1.5 (MAR21.98).

---

## 13. Treatment of Index Instruments ([[MAR_20260323.pdf#page=36|MAR21.31–21.34, page 36]] / [[CRR_20260101.pdf#page=480|CRR Art. 325i]])

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
