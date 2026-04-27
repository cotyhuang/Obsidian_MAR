---
tags: [CRIF, ISDA, FRTB-SA, data-standards, SbM, DRC, RRAO]
sources:
  - "[[raw/FRTB_SA_Risk-Data-Standards_v1.9]]"
  - "[[raw/FRTB_SA_Risk-Data-Standards_v1.9.pdf]]"
created: 2026-04-27
---
# ISDA CRIF — FRTB-SA Data Standards

> [!info] Overview
> The **Common Risk Interchange Format (CRIF)** is the ISDA-developed standard for describing FRTB-SA risk data on portfolios and trades. It provides a structured, column-based format for exchanging sensitivities, jump-to-default amounts, and residual-risk notionals between market participants, vendors, and regulators.

This page summarises ISDA FRTB-SA Risk Data Standards **v1.9** (originally v1.8, dated 26 January 2024).

---

## 1. Purpose & Use Cases

The CRIF was developed to support:

- **ISDA industry-wide benchmarking** — measuring variability in FRTB-SA implementations across banks
- **Risk data reconciliation** between counterparties
- **Third-party vendor services** — FRTB calculation engines, reporting tools
- **Unit testing & validation** — ISDA's own FRTB-SA Unit Test and Perun© calculator consume CRIF files directly
- **New firm on-boarding** — a standardised data contract for FRTB-SA implementation

> [!tip] ISDA Ecosystem
> ISDA's FRTB-SA Unit Test and the Perun© online calculator are both built around the CRIF standard. Users can upload CRIF files directly to compute FRTB-SA capital. [[raw/FRTB_SA_Risk-Data-Standards_v1.9|§9]]

---

## 2. Format Overview

The CRIF is a **column-based flat file** (Excel, CSV, or TXT). Each row represents a single risk factor for a trade or portfolio.

### Core Fields (Columns 1–12)

| # | Field | Type | Description |
|---|---|---|---|
| 1 | **PortfolioID** | String | Portfolio identifier |
| 2 | **TradeID** | String | Trade identifier |
| 3 | **Variant** | String | Input variant (relevant for Vega, Curvature, DRC) |
| 4 | **SensitivityID** | String | Risk factor identifier |
| 5 | **RiskType** | String | Risk class + measure combination (e.g. `GIRR_DELTA`, `FX_VEGA`, `DRC_NS`) |
| 6 | **Qualifier** | String | Risk factor detail — depends on RiskType (e.g. ISO currency for GIRR, issuer name for Equity) |
| 7 | **Bucket** | String | FRTB-SA bucket per regulations (e.g. currency liquidity category for GIRR) |
| 8 | **Label1** | String | Additional qualifier — option tenor (Vega) or CVR shift (Curvature) |
| 9 | **Label2** | String | Further qualifier — risk factor sub-type (e.g. tenor, seniority) |
| 10 | **Amount** | Float | Risk amount in local currency — meaning varies by RiskType/Variant |
| 11 | **AmountCurrency** | String | ISO currency code for Amount |
| 12 | **AmountUSD** | Float | Amount converted to USD |

### Extended Fields (Columns 13–18)

| # | Field | Type | Used For |
|---|---|---|---|
| 13 | **Label3** | String | Implied volatility (Vega Variant 2) or Notional (DRC_NS Variant 1) |
| 14 | **EndDate** | Date | Maturity date for DRC instruments (`YYYY-MM-DD`) |
| 15 | **CreditQuality** | String | Issuer rating (e.g. `AAA`, `CQS1`) or direct risk-weight input |
| 16 | **LongShortInd** | String | `L` or `S` — applies to DRC only |
| 17 | **CoveredBondInd** | String | `Y` or blank — DRC_NS only |
| 18 | **TrancheThickness** | Float | 0–1, for DRC_SNC Variant 1 (SEC-ERBA) |

---

## 3. RiskType Taxonomy

### Sensitivities-Based Method (SbM)

| RiskType | Risk Class | Measure |
|---|---|---|
| `GIRR_DELTA` | [[FRTB SA — GIRR\|General Interest Rate Risk]] | Delta |
| `GIRR_VEGA` | GIRR | Vega |
| `GIRR_CURV` | GIRR | Curvature |
| `CSR_NS_DELTA` | [[FRTB SA — CSR Non-Securitisation\|CSR Non-Sec]] | Delta |
| `CSR_NS_VEGA` | CSR Non-Sec | Vega |
| `CSR_NS_CURV` | CSR Non-Sec | Curvature |
| `CSR_SNC_DELTA` | [[FRTB SA — CSR Securitisation\|CSR Sec (non-CTP)]] | Delta |
| `CSR_SNC_VEGA` | CSR Sec (non-CTP) | Vega |
| `CSR_SNC_CURV` | CSR Sec (non-CTP) | Curvature |
| `CSR_SC_DELTA` | [[FRTB SA — CSR CTP\|CSR CTP]] | Delta |
| `CSR_SC_VEGA` | CSR CTP | Vega |
| `CSR_SC_CURV` | CSR CTP | Curvature |
| `EQ_DELTA` | [[FRTB SA — Equity Risk\|Equity]] | Delta |
| `EQ_VEGA` | Equity | Vega |
| `EQ_CURV` | Equity | Curvature |
| `COMM_DELTA` | [[FRTB SA — Commodity Risk\|Commodity]] | Delta |
| `COMM_VEGA` | Commodity | Vega |
| `COMM_CURV` | Commodity | Curvature |
| `FX_DELTA` | [[FRTB SA — FX Risk\|FX]] | Delta |
| `FX_VEGA` | FX | Vega |
| `FX_CURV` | FX | Curvature |

### Default Risk Charge (DRC)

| RiskType | Description |
|---|---|
| `DRC_NS` | [[FRTB SA — Default Risk Charge\|DRC]] — Non-Securitisation |
| `DRC_SNC` | DRC — Securitisation (non-CTP) |
| `DRC_SC` | DRC — Securitisation (CTP) |

### Residual Risk Add-On (RRAO)

| RiskType | Risk Weight | Description |
|---|---|---|
| `RRAO_1_PERCENT` | 1.0% | Exotic underlyings |
| `RRAO_01_PERCENT` | 0.1% | Other residual risks |

> For RRAO, the **Amount** column contains the position's **notional**. See [[FRTB SA — Residual Risk Add-On]].

---

## 4. Input Variants

Since bank infrastructure varies, the CRIF supports multiple equivalent input representations for Vega, Curvature, and DRC.

### 4.1 Vega Variants

| Variant | Amount Contains | Label3 Contains | Notes |
|---|---|---|---|
| **1** | Vega risk sensitivity $s_k = \text{vega} \times \text{implied vol}$ | Blank | Direct sensitivity input |
| **2** | Vega (greek) | Implied volatility | Engine computes $s_k$ internally |

**Example**: $s_k = -100 = -400 \times 0.25$ (Variant 2 decomposes into vega and implied vol).

### 4.2 Curvature Variants

| Variant | Amount Contains | Notes |
|---|---|---|
| **1a** | $CVR^+$ and $CVR^-$ (delta-stripped) | Two rows per sensitivity; shift size in Label1 |
| **2a** | Full revaluation P&L (not delta-stripped) | Delta in first row; engine strips delta internally |

**Formula** (recovering CVR from Variant 2a):
$$CVR_{1a}^{+} = -(P\&L_{up} - \text{Delta} \times \frac{\text{shift}}{0.01})$$

### 4.3 DRC_NS Variants

| Variant | Amount Contains | Label3 | EndDate |
|---|---|---|---|
| **1** (M2M) | Market Value | Notional | Required |
| **2** (JTD) | Jump-to-Default (maturity-unscaled) | Blank | Required |
| **3** (Scaled JTD) | JTD (maturity-scaled) | Blank | Not required |

### 4.4 DRC_SNC Variants

| Variant | Approach | CreditQuality | TrancheThickness |
|---|---|---|---|
| **1** | SEC-ERBA (not available for US-NPR) | Rating (e.g. `AAA`) | Required |
| **2** | Risk-weight as direct input | Float risk-weight | Not required |

### 4.5 DRC_SC Variants

| Variant | Approach | CreditQuality |
|---|---|---|
| **1** | Banking Book approach | Direct risk-weight input |
| **2** | Decomposition approach | Rating; uses DRC_NS rules |

---

## 5. Configuration Flags (Jurisdictional Divergences)

The CRIF supports **configuration flags** to handle divergences between Basel (MAR), CRR2/CRR3, and UK-PRA rulesets.

### 5.1 `CRR2_RW_INFL_XCCY`

Controls whether GIRR Inflation/XCCY risk weights for liquid currencies are divided by $\sqrt{2}$.

| Alt | Treatment |
|---|---|
| **Alt 1** | INFL and XCCY risk weights divided by $\sqrt{2}$ for liquid currencies |
| **Alt 2** | Division does **not** apply to INFL/XCCY (read as non-risk-free tenors) |

### 5.2 `VEGA_CORR_INFL_XCCY`

Controls GIRR Vega intra-bucket correlation for INFL and XCCY.

| Alt | $\rho_{\text{XCCY,INFL}}$ | $\rho_{\text{XCCY},i}$ | $\rho_{\text{INFL},i}$ |
|---|---|---|---|
| **Alt 1** | 0 | 0 | 0.4 |
| **Alt 2** | 1 | 1 | 1 |
| **Alt 3** | Per MAR21.93 with $T_{\text{INFL}} = T_{\text{XCCY}} = 0.5$ years | — | — |

### 5.3 `CSR_NS_INDX_BUCKET_NAME_CORRELATION`

| Alt | $\rho_{\text{name}}$ for index buckets | Applicable To |
|---|---|---|
| **Alt 1** | 35% (CRR2 Article 325ai) | CRR2 buckets 19–20 |
| **Alt 2** | 80% (Basel MAR21.55) | Basel buckets 17–18; also UK-PRA |

> [!warning] Known Basel–CRR2 Gap
> The CRR2 name correlation of 35% for index buckets (vs Basel's 80%) has not been corrected by the EU regulator. Alt 2 reflects the expectation that this gap will be bridged. [[raw/FRTB_SA_Risk-Data-Standards_v1.9|§9.2.3]]

### 5.4 `DRC_NS_COVERED_SENIORITY`

| Alt | Treatment of Covered Bonds |
|---|---|
| **Alt 1** | Override LGD to 0.25; bond stays in its Label2 seniority class |
| **Alt 2** | Covered is a separate seniority class: EQUITY < NON-SENIOR < SENIOR < COVERED |

### 5.5 `CRR2_CSR_NS_INDX_RATING_CORR`

Controls inter-bucket $\gamma_{\text{rating}}$ for CSR NS index buckets.

| Alt | $\gamma_{\text{rating}}$ | Resulting $\gamma$ |
|---|---|---|
| **Alt 1** | 0.5 | $0.5 \times 0.75 = 0.375$ |
| **Alt 2** | 1.0 | $1.0 \times 0.75 = 0.75$ |

UK-PRA follows Alt 1 ($\gamma_{\text{rating}} = 0.5$).

---

## 6. Key GIRR Tenors

| Risk Measure | Tenors |
|---|---|
| **GIRR Delta** | 0.25, 0.5, 1, 2, 3, 5, 10, 15, 20, 30, INFL, XCCY |
| **GIRR Vega — Option maturity** | 0.5, 1, 3, 5, 10 |
| **GIRR Vega — Underlying** | Same as Delta tenors |
| **CSR Tenor** | 0.5, 1, 3, 5, 10 |
| **FX Vega — Option maturity** | 0.5, 1, 3, 5, 10 |

---

## 7. Date Format

All dates in CRIF files must use **ISO 8601**: `YYYY-MM-DD` (e.g. `2016-09-01`).

---

## See Also

- [[FRTB SA — Sensitivities-Based Method]] — aggregation formulas consuming CRIF sensitivities
- [[FRTB SA — Default Risk Charge]] — DRC methodology behind Variants 1–3
- [[FRTB SA — Residual Risk Add-On]] — RRAO encoding in CRIF
- [[FRTB SA — GIRR]] — GIRR tenor structure and risk weights
- [[FRTB SA — Basel vs CRR3 Comparison]] — jurisdictional differences addressed by config flags
- [[FRTB Overview]] — broader context for the FRTB framework
