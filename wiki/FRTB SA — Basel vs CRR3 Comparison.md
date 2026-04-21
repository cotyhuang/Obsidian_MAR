---
tags: [MAR, FRTB, CRR3, EBA, BaselFramework, comparison]
sources:
  - "[[raw/MAR_20260323]]"
  - "[[raw/CRR3 Market Risk Summary]]"
  - "[[raw/FRTB Impact Analysis]]"
  - "[[raw/CRR_20260101.pdf]]"
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
| Effective date | 1 January 2023 | 1 January 2025 (SA reporting) / **1 January 2027** (binding capital) |
| IMA go-live | 1 January 2023 | Phased: 2027–2029 |
| Output floor fully phased | 72.5% from 2023 | Phased: 50% (2025) → 72.5% (2030) |

> [!warning] Key Divergence
> Basel intended FRTB to apply from Jan 2023. The EU initially targeted 2025–2026 but has exercised **Article 461a** to defer binding capital requirements to **1 January 2027**, to preserve level playing field with non-EU jurisdictions (US & UK also delayed). During the deferral, institutions continue using existing (pre-FRTB) methodologies.

---

## 2. Structural Differences

| Aspect                                  | Basel (MAR)                                       | EU CRR3                                            |
| --------------------------------------- | ------------------------------------------------- | -------------------------------------------------- |
| **SA Calculation frequency**            | Monthly (MAR20.2)                                 | Monthly (aligns with Basel)                        |
| **Simplified SA**                       | Available at national discretion (MAR11.7, MAR40) | Available with specific proportionality thresholds |
| **Correlation Trading Portfolio (CTP)** | Included from day one                             | Included, with technical standards by EBA          |
| **IMA desk-level approval**             | Yes (MAR30.4)                                     | Yes, with EBA RTS specifying criteria              |
| **SA as floor for IMA**                 | Yes                                               | Yes with transitional adjustment factors           |

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
- **SA Output Floor**: Phased in from 50% (2025) to 72.5% by 2030
- **Transitional multipliers**: EC consulted on temporary ceilings to neutralise capital volatility upon FRTB go-live (up to 3-year period until 2029)
- **DRC**: Transitional provisions for the treatment of certain securitisation exposures under banking book equivalence mapping
- **Disclosure**: Deferred to align with the 2027 binding application date

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

### Capital Impact Estimates

| Category | Estimated SA Capital Increase vs Basel 2.5 |
|---|---|
| Average trading book | +40–70% |
| Diversified banks | +50–60% |
| GIRR-heavy banks | +30–50% (benefit from specified currency discount) |
| Equity-heavy banks | +60–100% |
| Exotic/structured desks | +100%+ (RRAO adds 1% of notional) |

### EBA 2024 Benchmarking Key Findings
- SbM Own Funds Requirements show **significantly lower dispersion** than traditional VaR/sVaR — improved consistency
- Areas of inconsistency: DRC application, RRAO scoping, risk factor bucketing
- Data quality directly impacts capital consumption (incorrect complexity flags → unnecessary RRAO charges)

### Global Implementation Divergence (as of April 2026)

| Jurisdiction | FRTB Capital Status | Timeline |
|---|---|---|
| Basel Committee | Effective 1 Jan 2023 | — |
| **EU (CRR3)** | Reporting from 2025; binding deferred to **2027** | Output floor phased to 2030 |
| **UK (PRA)** | Binding from **1 Jan 2027** | Aligned with EU delay |
| US (Basel III Endgame) | Significantly delayed / uncertain | Political headwinds |
| Japan | Implemented 2024 | — |
| Singapore (MAS) | Implemented 2023 | — |
| Hong Kong (HKMA) | Implemented 2024 | — |

> [!note] Sources: [[raw/CRR3 Market Risk Summary]], [[raw/FRTB Impact Analysis]]

---

## See Also

- [[FRTB Overview]]
- [[Basel vs EBA — Boundary Comparison]]
- [[FRTB SA — Sensitivities-Based Method]]
- [[EBA CRR — Trading and Banking Book]]
