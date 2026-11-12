---
tags: [MAR, FRTB, look-through, MAR21, MAR22, CIU, EIIF, CRR3, raw-source]
source: web search synthesis (bis.org, eba.europa.eu, eur-lex.europa.eu, isda.org, kpmg.com, decode-finance.com)
captured: 2026-11-12
---
# Basel MAR Look-Through Approach (LTA) — Web Resources & Regulatory Synthesis

## 1. Official Regulatory Links

### Basel Committee on Banking Supervision (BCBS / BIS)
- **MAR10 — Market risk terminology (MAR10.8 Definition of Look-Through Approach)**:
  [https://www.bis.org/basel_framework/chapter/MAR/10.htm](https://www.bis.org/basel_framework/chapter/MAR/10.htm?inforce=20230101&published=20200327)
- **MAR11 — Definitions and application of market risk (MAR11.9 SA requirement for non-look-through funds)**:
  [https://www.bis.org/basel_framework/chapter/MAR/11.htm](https://www.bis.org/basel_framework/chapter/MAR/11.htm)
- **MAR21 — Standardised approach: sensitivities-based method (MAR21.31–21.38 Indices, multi-underlying options & equity investments in funds)**:
  [https://www.bis.org/basel_framework/chapter/MAR/21.htm](https://www.bis.org/basel_framework/chapter/MAR/21.htm?inforce=20230101&published=20240705)
- **MAR22 — Standardised approach: default risk capital requirement (MAR22.5 Derivative look-through, MAR22.8 Fund DRC, MAR22.39 Securitisation decomposition)**:
  [https://www.bis.org/basel_framework/chapter/MAR/22.htm](https://www.bis.org/basel_framework/chapter/MAR/22.htm?inforce=20230101&published=20200327)
- **MAR23 — Standardised approach: residual risk add-on (MAR23.6(5) RRAO for indices and unrated bucket 11 funds)**:
  [https://www.bis.org/basel_framework/chapter/MAR/23.htm](https://www.bis.org/basel_framework/chapter/MAR/23.htm)
- **MAR31 — Internal models approach: model requirements (MAR31.11 Look-through requirement for funds in IMA desks)**:
  [https://www.bis.org/basel_framework/chapter/MAR/31.htm](https://www.bis.org/basel_framework/chapter/MAR/31.htm)
- **MAR50 — Credit valuation adjustment framework (MAR50.49–50.50, MAR50.64 Qualified index vs look-through in BA-CVA / SA-CVA)**:
  [https://www.bis.org/basel_framework/chapter/MAR/50.htm](https://www.bis.org/basel_framework/chapter/MAR/50.htm)
- **RBC25 — Boundary between the banking book and the trading book (RBC25.8(5) Trading book eligibility for equity investments in funds)**:
  [https://www.bis.org/basel_framework/chapter/RBC/25.htm](https://www.bis.org/basel_framework/chapter/RBC/25.htm)
- **CRE60 — Equity investments in funds (Banking Book LTA / MBA / FBA hierarchy referenced by MAR21.36(2)(b))**:
  [https://www.bis.org/basel_framework/chapter/CRE/60.htm](https://www.bis.org/basel_framework/chapter/CRE/60.htm)

### European Union (CRR3 / EBA)
- **Regulation (EU) 2024/1623 (CRR3) — Articles 325i (Index instruments) & 325j (Collective Investment Undertakings / CIUs)**:
  [https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202401623](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202401623)
- **EBA Interactive Single Rulebook — Article 325i (Treatment of index instruments and other multi-underlying instruments)**:
  [https://www.eba.europa.eu/regulation-and-policy/single-rulebook/interactive-single-rulebook/12191](https://www.eba.europa.eu/regulation-and-policy/single-rulebook/interactive-single-rulebook/12191)
- **European Commission Delegated Act on Market Risk Alternative Standardised Approach**:
  [https://finance.ec.europa.eu/system/files/2019-10/2019-market-risk-alternative-specific-proposed-delegated-act_en.pdf](https://finance.ec.europa.eu/system/files/2019-10/2019-market-risk-alternative-specific-proposed-delegated-act_en.pdf)

### Industry & Practitioner Analyses
- **Decode Finance — FRTB MAR21 Series: SBM Mechanics & Look-Through Approach**:
  [https://decode-finance.com/frtb-mar21-series8d-sbm-mechanics-look-through/](https://decode-finance.com/frtb-mar21-series8d-sbm-mechanics-look-through/)
- **ISDA & IIF — Response to European Commission's Consultation on the Market Risk Prudential Framework (CIU & Index Look-Through Analysis)**:
  [https://www.isda.org/a/vgfgE/ISDA-IIF-Response-to-ECs-Consultation-on-the-Market-Risk-Prudential-Framework.pdf](https://www.isda.org/a/vgfgE/ISDA-IIF-Response-to-ECs-Consultation-on-the-Market-Risk-Prudential-Framework.pdf)
- **KPMG — Basel 4 Publications: FRTB Standardised Approach & CIU Treatment**:
  [https://assets.kpmg.com/content/dam/kpmgsites/xx/pdf/2022/08/basel-4-publications.pdf.coredownload.inline.pdf](https://assets.kpmg.com/content/dam/kpmgsites/xx/pdf/2022/08/basel-4-publications.pdf.coredownload.inline.pdf)

---

## 2. Core Summary of the Basel MAR Look-Through Approach

### 2.1 Definition (MAR10.8)
The **Look-Through Approach (LTA)** is an approach in which a bank determines the relevant market risk capital requirements for a position that has multiple underlyings (such as an **index instrument**, **multi-underlying option**, or an **equity investment in a fund (EIIF / CIU)**) **as if the underlying positions were held directly by the bank**, taking into account the bank's proportionate share of the fund/index and any embedded leverage.

### 2.2 Which Risk Classes Apply?
1. **When Full Look-Through Is Applied (MAR21.31, MAR21.34, MAR21.35, MAR22.5)**:
   - Because the underlying constituents of the fund, index, or basket are treated as **directly held positions**, sensitivities are decomposed and mapped into **any and all of the 7 SBM Risk Classes** corresponding to the underlying constituents:
     1. **GIRR** (General Interest Rate Risk)
     2. **CSR Non-Securitisation** (Credit Spread Risk — Non-Securitisation)
     3. **CSR Securitisation (non-CTP)**
     4. **CSR Securitisation (CTP)** — *Note: Index CTP instruments themselves cannot be broken down into constituents (MAR21.34(2)).*
     5. **Equity Risk**
     6. **Commodity Risk**
     7. **FX Risk** (including currency mismatches of underlying fund/index assets relative to the bank's reporting currency)
   - In addition, decomposed credit and equity constituents enter the **Default Risk Charge (DRC, MAR22.5)**, where JTD positions are computed per constituent legal entity.
2. **When the "No Look-Through" Opt-Out Is Used for Qualified Listed Indices / Index-Tracking Funds (MAR21.31, MAR21.33, MAR21.35(2), MAR21.38)**:
   - Applies specifically to **2 SBM Risk Classes**:
     1. **Equity Risk** — Mapped to a specific equity sector bucket (Buckets 1–11 if >75% of index weight is in one sector) or **Equity Index Buckets (Bucket 12: Large cap & advanced economy indices, RW = 15%; Bucket 13: Other equity indices, RW = 25%)**.
     2. **CSR Non-Securitisation** — Mapped to a specific CSR sector bucket (Buckets 1–16 if >75% of index weight is in one sector) or **CSR Index Buckets (Bucket 17: IG indices, RW = 1.5%; Bucket 18: HY indices, RW = 5.0%)**.
3. **When Look-Through Is Not Possible for Funds (Fallback Approaches — MAR21.36)**:
   - **Mandate-Based / Hypothetical Portfolio Approach (MAR21.36(2))**: Mapped across the **relevant SBM Risk Classes** permitted by the fund's mandate (assuming maximum investment in the highest capital-consuming assets on a stand-alone basis), plus DRC and RRAO.
   - **Unrated "Other Sector" Equity Approach (MAR21.36(3))**: Mapped to **Equity Risk Bucket 11 ("Other sector", RW = 70%, zero correlation recognition)** for SBM, plus **DRC (MAR22.8 — unrated equity 15% RW or maximum mandate-implied HY/defaulted RW)** and **RRAO (MAR23.6(5) — maximum mandate-implied exotic 1.0% / other residual 0.1% RW)**.
   - **CVA Risk Framework (MAR50.50)**: Optional qualified index treatment (vs mandatory look-through) applies to **Counterparty Credit Spread Risk**, **Reference Credit Spread Risk**, and **Equity Risk**.

