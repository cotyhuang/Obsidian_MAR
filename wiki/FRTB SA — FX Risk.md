---
tags: [MAR, FRTB, SbM, FX, foreign-exchange]
sources:
  - "[[raw/MAR_20260323]]"
created: 2026-04-21
---
# FRTB SA — FX Risk

> [!info] Regulatory Reference
> Basel MAR21.14, MAR21.24, MAR21.86–21.89
> [[MAR_20260323.pdf#page=30|MAR21.14, page 30]] — [[MAR_20260323.pdf#page=60|MAR21.86–21.89, page 60]]

---

## 1. Risk Factors ([[MAR_20260323.pdf#page=30|MAR21.14, page 30]])

### Delta
All exchange rates between:
- The currency in which an instrument is denominated, and
- The bank's **reporting currency** (or approved base currency)

For cross-currency instruments (e.g. USD/JPY forward for a CAD-reporting bank), the risk factors are the exchange rates between the reporting currency and **both** referenced currencies (e.g. USD/CAD and JPY/CAD).

### Base Currency Approach (MAR21.14(1)(b)–(d))
Subject to supervisory approval, FX risk may be calculated relative to a **base currency** instead of the reporting currency. In this case, the bank must also capture the **translation risk** (FX risk between base and reporting currencies). The resulting capital is converted to reporting currency at the spot rate.

Conditions:
- Only **one** base currency allowed
- Must not inappropriately reduce capital requirements vs non-base approach

### Vega (MAR21.14(2))
Implied volatilities of FX options, defined along **one dimension** — option maturity: 0.5y, 1y, 3y, 5y, 10y.

### Curvature (MAR21.14(3))
Same definition as delta — exchange rates between denominated currency and reporting currency.

> [!note] No distinction between onshore and offshore variants of a currency, nor between deliverable and non-deliverable variants (MAR21.14(4), FAQ2).

---

## 2. Buckets ([[MAR_20260323.pdf#page=60|MAR21.86, page 60]])

Each exchange rate between a currency and the reporting currency constitutes a **separate bucket**.

---

## 3. Delta Risk Weight ([[MAR_20260323.pdf#page=60|MAR21.87–21.88, page 60]])

| Category | Risk Weight |
|---|---|
| **All FX sensitivities** (default) | **15%** |
| **Specified currency pairs** (see below) | 15% ÷ √2 ≈ **10.6%** |

### Specified Currency Pairs ([[MAR_20260323.pdf#page=60|MAR21.88, page 60]])

The following USD pairs qualify for the reduced risk weight:

> USD/EUR, USD/JPY, USD/GBP, USD/AUD, USD/CAD, USD/CHF, USD/MXN, USD/CNY, USD/NZD, USD/RUB, USD/HKD, USD/SGD, USD/TRY, USD/KRW, USD/SEK, USD/ZAR, USD/INR, USD/NOK, USD/BRL

**First-order crosses** of these pairs also qualify (e.g. EUR/AUD = cross of USD/EUR and USD/AUD).

---

## 4. Intra-Bucket Correlations ρ_{kl}

Not applicable — each FX bucket contains only **one** risk factor (one exchange rate per currency pair).

---

## 5. Inter-Bucket Correlation γ_{bc} ([[MAR_20260323.pdf#page=61|MAR21.89, page 61]])

$$\gamma = 60\%$$ (uniform across all FX buckets)

---

## 6. Sensitivity Definition ([[MAR_20260323.pdf#page=34|MAR21.24, page 34]])

$$s_k = \frac{V_i(1.01 \cdot FX_k) - V_i(FX_k)}{0.01}$$

A **1% relative shift** in the exchange rate.

---

## 7. Vega Risk Weight ([[MAR_20260323.pdf#page=60|MAR21.92, page 60]])

| Risk Class | Liquidity Horizon | Risk Weight |
|---|---|---|
| FX | 40 days | 100% |

---

## 8. Curvature Risk Weight ([[MAR_20260323.pdf#page=63|MAR21.98, page 63]])

The curvature risk weight = the **delta risk weight** = 15% (relative shift).

> [!tip] FX Curvature Scalar
> For options that do **not** reference the bank's reporting currency (or base currency) as an underlying, net curvature risk charges may be divided by **1.5** (MAR21.98).
> 
> Alternatively, with supervisory approval, a bank may apply the 1.5 scalar to **all** FX instruments provided curvature sensitivities are calculated for all currencies including the reporting currency.

---

## 9. Worked Example — FX Forward Delta Capital

> [!example] EUR/USD Forward — USD-reporting bank

**Setup**: A bank holds a EUR/USD FX forward. The bank reports in USD.

**Step 1 — Identify risk factor**: EUR/USD exchange rate → FX delta risk factor.

**Step 2 — Compute net sensitivity**: Assume the forward's delta sensitivity to a 1% shift in EUR/USD = +€5,000,000 (expressed in USD = $5,400,000 at spot 1.08).

**Step 3 — Apply risk weight**: Since EUR/USD is a specified pair, RW = 15% ÷ √2 ≈ 10.6%.
$$WS = 5{,}400{,}000 \times 10.6\% = 572{,}400$$

**Step 4 — Bucket aggregation**: Only one risk factor in this bucket, so:
$$K_{EUR} = |WS| = 572{,}400$$

**Step 5 — Cross-bucket aggregation**: If the bank only has EUR exposure:
$$\text{FX Delta Capital} = 572{,}400$$

If the bank also has, say, a JPY bucket with $K_{JPY} = 300{,}000$ and $S_{JPY} = -300{,}000$:
$$\text{FX Delta Capital} = \sqrt{572{,}400^2 + 300{,}000^2 + 2 \times 0.60 \times 572{,}400 \times (-300{,}000)}$$

**Step 6 — Three scenarios**: Repeat with γ = 60% (medium), 75% (high), 45% (low). Take the max.

---

## See Also

- [[FRTB SA — Sensitivities-Based Method]]
- [[FRTB SA — GIRR]]
- [[FRTB SA — Equity Risk]]
- [[FRTB SA — Commodity Risk]]
