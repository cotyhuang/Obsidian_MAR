---
tags: [MAR, FRTB, BaselFramework, market-risk]
sources:
  - "[[raw/Banking book Trading book comparison]]"
created: 2026-04-21
---
# FRTB Overview — Fundamental Review of the Trading Book

> [!note] Context
> The FRTB is the Basel Committee's comprehensive reform of the market risk framework, first published in January 2016 and revised in January 2019. It replaces the previous Basel 2.5 market risk standard.

---

## 1. What Is the FRTB?

The **Fundamental Review of the Trading Book** is a set of reforms that overhauls how banks calculate capital for **market risk** — the risk of loss from changes in market prices (interest rates, FX, equities, commodities, credit spreads).

Key motivations:
- The 2008 financial crisis revealed that the existing market risk framework was **insufficiently capitalised**
- Boundary between [[Banking Book vs Trading Book|banking and trading books]] was too porous
- Risk measures (Value-at-Risk) were deemed inadequate

## 2. Major Changes

### 2.1 Revised Boundary ([[Basel RBC25]])
- Stricter rules for assigning positions to the trading book
- Tighter controls on reclassification
- Mandatory [[Trading Intent]] documentation

### 2.2 New Risk Measures
- Replacement of **VaR** with **Expected Shortfall (ES)** as the primary risk measure
- Introduction of **liquidity horizons** — different risk factors have different holding periods
- Separate treatment of **default risk** via the Default Risk Charge (DRC)

### 2.3 Standardised Approach (SA)
- Completely redesigned, sensitivity-based method (**SbM**)
- Risk sensitivities: delta, vega, and curvature across defined risk classes
- Serves as both a **standalone capital calculation** and a **floor** for IMA banks

### 2.4 Internal Models Approach (IMA)
- Desk-level approval required (not bank-wide)
- **P&L attribution test** to validate model quality
- **Risk factor eligibility test** — only factors with sufficient real price data qualify for ES modelling
- Fallback to SA for desks that fail validation

## 3. Implementation Timeline

| Jurisdiction | Status |
|---|---|
| Basel (global) | Final standard: January 2019 |
| EU (CRR3) | Phased implementation; adapted timeline |
| US | Pending final rulemaking |
| UK | Post-Brexit separate implementation |

> [!warning] EU Divergence
> The EU's implementation through [[EBA CRR — Trading and Banking Book|CRR3]] includes deferrals and proportionality measures that depart from the Basel timeline. See [[Basel vs EBA — Boundary Comparison]] for details.

---

## See Also

- [[Banking Book vs Trading Book]]
- [[Basel RBC25]]
- [[EBA CRR — Trading and Banking Book]]
- [[Trading Intent]]
