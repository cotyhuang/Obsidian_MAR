---
tags: [MAR, FRTB, SA, RRAO]
sources:
  - "[[raw/MAR_20260323]]"
created: 2026-04-21
---
# FRTB SA — Residual Risk Add-On (RRAO)

> [!info] Regulatory Reference
> Basel MAR23 — Standardised approach: residual risk add-on (effective 01 Jan 2023).
> [[MAR_20260323.pdf#page=80|MAR23, page 80]]

---

## 1. Purpose ([[MAR_20260323.pdf#page=81|MAR23.1, page 81]])

The RRAO captures market risks that are **not adequately covered** by the [[FRTB SA — Sensitivities-Based Method|SBM]] or [[FRTB SA — Default Risk Charge|DRC]]. It is calculated **in addition to** and **independently of** the other SA components.

---

## 2. Instruments Subject to RRAO ([[MAR_20260323.pdf#page=81|MAR23.2, page 81]])

Two categories:

### A. Instruments with Exotic Underlyings ([[MAR_20260323.pdf#page=81|MAR23.3, page 81]])
Trading book instruments whose underlying exposure falls **outside the scope** of delta/vega/curvature in any SBM risk class, and outside DRC.

Examples of exotic underlyings:
- Longevity risk
- Weather
- Natural disasters
- Future realised volatility (confirmed in FAQ1)

### B. Instruments Bearing Other Residual Risks ([[MAR_20260323.pdf#page=81|MAR23.4, page 81]])
Instruments subject to vega/curvature that have **payoffs not replicable** as a finite linear combination of vanilla options, **or** instruments in the CTP (excluding recognised hedges).

Types of residual risks (non-exhaustive, [[MAR_20260323.pdf#page=81|MAR23.5, page 81]]):

| Risk Type | Description | Example Instruments |
|---|---|---|
| **Gap risk** | Significant vega change from small underlying moves | Barrier options, Asian options, digital options |
| **Correlation risk** | Change in correlation parameter | Basket options, best-of, spread options, quanto options |
| **Behavioural risk** | Exercise/prepayment decisions driven by non-financial factors | Fixed rate mortgages with retail prepayment options |

---

## 3. Exemptions ([[MAR_20260323.pdf#page=82|MAR23.6, page 82]])

The following risks, **by themselves**, do not cause RRAO to apply:
1. Cheapest-to-deliver risk
2. Smile risk
3. Correlation risk from multi-underlying **European or American plain vanilla options** (including index options)
4. Dividend risk from derivatives whose underlying is not solely dividends
5. Index instruments treated under MAR21.31–21.32

---

## 4. Exclusions ([[MAR_20260323.pdf#page=82|MAR23.7, page 82]])

| Exclusion | Condition |
|---|---|
| **Back-to-back trades** | Both legs of a perfectly matched third-party transaction are excluded |
| **Listed / centrally clearable** | Instruments listed or eligible for central clearing are excluded from RRAO for *other residual risks* (but NOT for exotic underlyings) |

---

## 5. Calculation ([[MAR_20260323.pdf#page=82|MAR23.8, page 82]])

$$\text{RRAO} = \sum_i \text{Notional}_i \times \text{Risk Weight}_i$$

A simple **gross notional sum** (no netting, no diversification):

| Category | Risk Weight |
|---|---|
| Instruments with exotic underlyings (MAR23.3) | **1.0%** |
| Instruments bearing other residual risks (MAR23.4) | **0.1%** |

> [!warning] Pillar 2
> Where the bank cannot satisfy the supervisor that the RRAO is sufficiently prudent, the supervisor may impose a **conservative additional capital charge** under Pillar 2 (footnote 2).

---

## 6. No Impact on SBM Scope ([[MAR_20260323.pdf#page=82|MAR23.8(1), page 82]])

The instruments subject to RRAO **do not change** the scope of risk factors in the SBM or DRC — i.e. being in the RRAO does not exempt an instrument from delta/vega/curvature/DRC calculations, nor does it add new risk factors.

---

## See Also

- [[FRTB SA — Sensitivities-Based Method]]
- [[FRTB SA — Default Risk Charge]]
- [[FRTB Overview]]
