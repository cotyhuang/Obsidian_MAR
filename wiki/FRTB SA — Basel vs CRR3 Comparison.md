---
tags: [MAR, FRTB, CRR3, EBA, BaselFramework, comparison]
sources:
  - "[[raw/MAR_20260323]]"
created: 2026-04-21
---
# FRTB SA — Basel vs CRR3 Comparison

> [!info] Context
> This page compares the Basel Committee's FRTB SA framework (MAR20–23) with the EU implementation via CRR3 (Regulation 2024/1623). CRR3 largely transposes Basel IV but introduces specific **national discretions, transitions, and divergences**.
> [[MAR_20260323.pdf#page=16|MAR20, page 16]] — [[MAR_20260323.pdf#page=19|MAR21, page 19]] — [[MAR_20260323.pdf#page=66|MAR22, page 66]] — [[MAR_20260323.pdf#page=80|MAR23, page 80]]

---

## 1. Implementation Timeline

| Milestone | Basel | EU (CRR3) |
|---|---|---|
| Final standard | January 2019 | June 2024 (Regulation published) |
| Effective date | 1 January 2023 | 1 January 2025 (SA reporting) / 1 January 2026 (binding) |
| IMA go-live | 1 January 2023 | Phased: 2026–2028 |

> [!warning] Key Divergence
> Basel intended FRTB to apply from Jan 2023; the EU deferred the binding capital requirement to **2025–2026**, with extended transition periods for some elements.

---

## 2. Structural Differences

| Aspect | Basel (MAR) | EU CRR3 |
|---|---|---|
| **SA Calculation frequency** | Monthly (MAR20.2) | Monthly (aligns with Basel) |
| **Simplified SA** | Available at national discretion (MAR11.7, MAR40) | Available with specific proportionality thresholds |
| **Correlation Trading Portfolio (CTP)** | Included from day one | Included, with technical standards by EBA |
| **IMA desk-level approval** | Yes (MAR30.4) | Yes, with EBA RTS specifying criteria |
| **SA as floor for IMA** | Yes | Yes with transitional adjustment factors |

---

## 3. Risk Weight & Parameter Differences

### 3.1 FX Risk — Specified Currency Pairs
- **Basel**: 19 specified USD pairs + first-order crosses → RW ÷ √2 ([[MAR_20260323.pdf#page=60|MAR21.88, page 60]])
- **CRR3**: Same mechanism, but the EU may add **EUR pairs** given EUR as the dominant reporting currency for EU banks — EBA to specify via RTS

### 3.2 GIRR — Specified Currencies
- **Basel**: EUR, USD, GBP, AUD, JPY, SEK, CAD + domestic currency → RW ÷ √2 ([[MAR_20260323.pdf#page=43|MAR21.44, page 43]])
- **CRR3**: Same list, but automatically includes **EUR** for all EU banks

### 3.3 Equity — Advanced Economy Definition
- **Basel**: Fixed list ([[MAR_20260323.pdf#page=54|MAR21.75, page 54]]) — Canada, US, Mexico, euro area, UK, etc.
- **CRR3**: Follows Basel's list but may update via delegated acts

### 3.4 Sovereign Treatment (DRC)
- **Basel**: Zero DRC risk weight for home sovereigns at national discretion ([[MAR_20260323.pdf#page=68|MAR22.7, page 68]])
- **CRR3**: EU member state sovereigns denominated in domestic currency — **zero risk weight** applied broadly (consistent with CRR credit risk treatment)

---

## 4. CRR3-Specific Provisions

### 4.1 Proportionality — Small Trading Book Exemption
- CRR3 retains the concept of **small trading book** derogation where institutions with limited trading activities (below defined thresholds) may use simplified approaches
- The thresholds are tighter than Basel's general guidance

### 4.2 Transitional Arrangements
- **SA Output Floor**: CRR3 phases in the output floor on IMA vs SA gradually (72.5% by 2030)
- **DRC**: Transitional provisions for the treatment of certain securitisation exposures under banking book equivalence mapping

### 4.3 EBA Technical Standards
CRR3 mandates EBA to develop binding technical standards (RTS/ITS) on:
- Risk factor eligibility test specifics
- P&L attribution test metrics and thresholds
- Definition of specified currency pairs
- Look-through approach for funds

---

## 5. Per-Risk-Class Summary of Key Differences

| Risk Class                                          | Basel                                                       | CRR3 Notable Difference                                            |
| --------------------------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------ |
| [[FRTB SA — GIRR\|GIRR]]                            | Standard risk weights; √2 discount for specified currencies | Same; EUR automatically specified for EU banks                     |
| [[FRTB SA — CSR Non-Securitisation\|CSR Non-Sec]]   | 18 buckets, standard RWs                                    | Aligned; EBA to clarify sector classification via RTS              |
| [[FRTB SA — CSR Securitisation\|CSR Sec (non-CTP)]] | Banking book equivalence for RWs                            | Specific EU hierarchy of approaches (SEC-IRBA → SEC-SA → SEC-ERBA) |
| [[FRTB SA — CSR CTP\|CSR CTP]]                      | Higher RWs vs non-sec                                       | EU may phase in CTP treatment; EBA to issue RTS                    |
| [[FRTB SA — Equity Risk\|Equity]]                   | 13 buckets; advanced economy list                           | Same; economy list may be updated via delegated acts               |
| [[FRTB SA — Commodity Risk\|Commodity]]             | 11 buckets                                                  | Aligned                                                            |
| [[FRTB SA — FX Risk\|FX]]                           | 15% RW; specified pairs                                     | EU may add EUR pairs via RTS                                       |
| [[FRTB SA — Default Risk Charge\|DRC]]              | Sovereign zero-RW at national discretion                    | Broad zero-RW for EUR-denominated EU sovereign debt                |
| [[FRTB SA — Residual Risk Add-On\|RRAO]]            | 1.0% / 0.1%                                                 | Same; supervisor may adjust under Pillar 2                         |

---

## 6. Impact Studies

> [!note] Open Area
> Consulting reports (Oliver Wyman, McKinsey, EBA QIS) have estimated that FRTB SA produces capital increases of **40–70%** compared to Basel 2.5 for the average trading book, with significant variation by asset class. EU-specific impact is shaped by the transitional provisions and proportionality measures in CRR3.

---

## See Also

- [[FRTB Overview]]
- [[Basel vs EBA — Boundary Comparison]]
- [[FRTB SA — Sensitivities-Based Method]]
- [[EBA CRR — Trading and Banking Book]]
