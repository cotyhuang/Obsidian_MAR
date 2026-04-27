---
tags: [index, wiki, MAR]
created: 2026-04-21
updated: 2026-04-27
---
# Wiki Index — MAR Knowledge Base

> [!info] Navigation
> This is the master table-of-contents for all curated wiki pages in this vault.
> Each entry links to a detailed topic page compiled from sources in `raw/`.

---

## Regulatory Frameworks

- [[Banking Book vs Trading Book]] — Core definitions, boundary rules, and the distinction between positions held for trading intent vs long-term holding.
- [[Basel RBC25]] — Basel Committee framework chapter defining the boundary between the banking book and the trading book.
- [[EBA CRR — Trading and Banking Book]] — EU implementation of the boundary rules via CRR Articles 104, 104a, and 104b.
- [[Basel vs EBA — Boundary Comparison]] — Side-by-side comparison of how Basel RBC25 and EBA CRR define and manage the book boundary.
- [[FRTB Overview]] — The Fundamental Review of the Trading Book and its impact on market risk capital requirements.
- [[CRR3 Article Map]] — Navigable index of CRR3 Articles 325–325bp with page references and wiki cross-links.

---

## Standardised Approach (SA) — Sensitivities-Based Method

- [[FRTB SA — Sensitivities-Based Method]] — General SBM framework: aggregation formulas, three correlation scenarios, sensitivity definitions, Vega worked example.

### Risk Classes
- [[FRTB SA — GIRR]] — General Interest Rate Risk: risk-free yield curves, inflation, cross-currency basis.
- [[FRTB SA — CSR Non-Securitisation]] — Credit Spread Risk for non-securitisation: 18 buckets by credit quality × sector.
- [[FRTB SA — CSR Securitisation]] — CSR for securitisations (non-CTP): 25 buckets by seniority × asset class.
- [[FRTB SA — CSR CTP]] — CSR for the Correlation Trading Portfolio: underlying-name sensitivities, higher risk weights.
- [[FRTB SA — Equity Risk]] — Equity risk: 13 buckets by market cap × economy × sector.
- [[FRTB SA — Commodity Risk]] — Commodity risk: 11 buckets by commodity group.
- [[FRTB SA — FX Risk]] — Foreign exchange risk: specified currency pairs, worked example.

### Other SA Components
- [[FRTB SA — Default Risk Charge]] — DRC: jump-to-default risk, LGD, Hedge Benefit Ratio, risk weights by rating.
- [[FRTB SA — Residual Risk Add-On]] — RRAO: exotic underlyings (1.0%) and other residual risks (0.1%).

---

## Key Concepts

- [[Trading Intent]] — Definition and regulatory criteria for positions held with trading intent.
- [[Internal Risk Transfers]] — Rules governing the transfer of risk between the banking book and trading book.
- [[Structural FX Positions]] — Treatment of structural foreign-exchange positions under Basel and CRR.

---

## Comparisons & Analysis

- [[FRTB SA — Basel vs CRR3 Comparison]] — Basel IV vs EU CRR3 implementation: timeline, parameter, and structural differences for the SA.

---

## Data Standards

- [[ISDA CRIF — FRTB-SA Data Standards]] — ISDA Common Risk Interchange Format (CRIF) v1.9: field definitions, RiskType taxonomy, input variants, jurisdictional configuration flags.

---

## Utilities

- [[Git Status Icons in VSCode]] — Quick reference for Git status indicators in the VSCode explorer.

---

## Sources

All wiki content is distilled from raw materials in `raw/`:

| Raw Source | Content |
|---|---|
| [[raw/MAR_20260323]] | Official Basel MAR standard (PDF, 188 pages) — MAR20–23 |
| [[raw/CRR_20260101]] | EU CRR3 full regulation text (Regulation 2024/1623) |
| [[raw/CRR3 Market Risk Summary]] | CRR3 market risk provisions — web synthesis |
| [[raw/FRTB Impact Analysis]] | EBA benchmarking, capital impact estimates, global divergence |
| [[raw/FRTB_SA_Risk-Data-Standards_v1.9]] | ISDA FRTB-SA CRIF data standards v1.9 |
| [[raw/RBC25]] | Basel RBC25 — banking/trading book boundary |
| [[raw/Banking book Trading book comparison]] | Basel vs EBA boundary comparison notes |
| [[raw/MAR vs. CRR Market Risk Standardised Approach Comparison]] | MAR vs CRR SA methodology comparison |
| [[raw/crr_structure.txt]] | CRR3 article-to-page index |
