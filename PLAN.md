# Wiki Update Plan — 2026-04-27

> [!info] Purpose
> This plan outlines the steps to bring the wiki up to date by compiling unprocessed raw materials, fixing structural issues identified in the last health check, and filling content gaps.

---

## Background

The vault currently has **21 wiki pages** and **15 raw source files**. The last health check (2026-04-21) identified several blind spots and structural issues. Since that check, no new raw files have been added, but two significant raw sources remain **uncompiled into wiki pages**:

| Raw Source | Size | Wiki Coverage |
|---|---|---|
| `FRTB_SA_Risk-Data-Standards_v1.9.md` | 36 KB | ❌ **None** — no wiki page exists |
| `CapitalCRIF_SACCR_Risk-Data-Standards_v1.9.md` | 11 KB | ❌ **None** — no wiki page exists |
| `CRR_20260101.md` | 2 MB | ⚠️ Partially covered via `FRTB SA — Basel vs CRR3 Comparison.md` and `EBA CRR — Trading and Banking Book.md`, but the full CRR extraction is not systematically indexed |
| `crr_structure.txt` | 4 KB | ⚠️ Used as reference but not compiled into its own page (utility file) |

---

## User Review Required

> [!IMPORTANT]
> **Scope decision**: The two ISDA CRIF data-standards documents are operational/technical specs for risk-data interchange, not pure regulatory text. They are highly relevant to FRTB implementation but represent a new sub-topic (data standards). Please confirm you want full wiki pages for these.

> [!WARNING]
> **IMA pages**: The health check flagged IMA (MAR30–33) as the largest content gap (🔴 High). Creating IMA pages would require reading large sections of `MAR_20260323.md` (~472 KB). This is included in the plan but is a significant token investment. Please confirm priority.

---

## Proposed Changes

### Phase 1 — New Wiki Pages from Uncompiled Raw Sources

#### [NEW] `wiki/ISDA CRIF — FRTB-SA Data Standards.md`
- Compile from `raw/FRTB_SA_Risk-Data-Standards_v1.9.md`
- Cover: CRIF format overview, field descriptions (RiskType, Qualifier, Bucket, Labels), input Variants (Vega, Curvature, DRC), RRAO encoding, configuration flags per jurisdiction
- Link to existing SBM, DRC, RRAO wiki pages

#### [NEW] `wiki/ISDA CRIF — SA-CCR Data Standards.md`
- Compile from `raw/CapitalCRIF_SACCR_Risk-Data-Standards_v1.9.md`
- Cover: SA-CCR CRIF format, field descriptions (RiskType for PFE/RC, HedgingSet, collateral parameters), portfolio structure
- Note: SA-CCR is adjacent to MAR (counterparty credit risk), but relevant to the vault's ISDA/CRIF focus

---

### Phase 2 — Fill Blind Spots from Health Check

#### [NEW] `wiki/FRTB IMA — Overview.md`
- Compile from `raw/MAR_20260323.md` (MAR30–33 sections)
- Cover: Expected Shortfall model, stressed ES, desk-level approval, P&L attribution test, risk factor eligibility test
- Will resolve 3 blind spots in one page: IMA, P&L Attribution, Risk Factor Eligibility

#### [NEW] `wiki/FRTB IMA — P&L Attribution Test.md`
- Detail the Spearman/KS test thresholds, traffic-light zones
- Source: MAR30 + CRR3 Article 325bg

#### [NEW] `wiki/FRTB IMA — Risk Factor Eligibility Test.md`
- Real price observation criteria, modellable vs non-modellable risk factors
- Source: MAR31 + CRR3 Article 325be

---

### Phase 3 — Add Missing Worked Example

#### [MODIFY] `wiki/FRTB SA — Sensitivities-Based Method.md` or a relevant risk-class page
- Add a **Vega worked example** (the only risk measure without a numerical example, per health check §5)
- Use GIRR Vega or FX Vega as the example risk class

---

### Phase 4 — Structural Fixes & INDEX Update

#### [MODIFY] `wiki/INDEX.md`
- Fix duplicate entries (lines 15–17 all point to `[[Trading Book vs Banking Book Boundary]]` instead of distinct pages like `Banking Book vs Trading Book`, `Basel RBC25`, `EBA CRR — Trading and Banking Book`)
- Add new pages from Phases 1–2 to the index
- Add a new section: **Data Standards** for CRIF pages
- Add `raw/` sources table entries for ISDA CRIF documents and CRR extraction
- Remove or relocate `Git Status Icons in VSCode.md` reference (non-MAR topic)

#### [MODIFY] `wiki/Git Status Icons in VSCode.md`
- Per health check recommendation: either move to `raw/` as a personal note, or leave in `wiki/` but mark as non-MAR utility. Awaiting user preference.

#### [MODIFY] `wiki/FRTB SA — Basel vs CRR3 Comparison.md`
- Update CRR3 timeline references if any are stale (health check §4 flagged CRR3 2025–2026 timeline as potentially needing update)

---

### Phase 5 — CRR Extraction Index (Optional)

#### [NEW] `wiki/CRR3 Article Map.md`
- Compile from `raw/crr_structure.txt` + `raw/CRR_20260101.md`
- Create a navigable article-to-page-number index for CRR3
- Link relevant articles to existing wiki pages (e.g., Art 325ae → GIRR, Art 325j → SBM correlations)

---

## Verification Plan

### Automated Checks
- After each new page: verify frontmatter has `sources:`, `tags:`, `created:` fields
- After INDEX update: verify all wiki pages are listed with wikilinks
- After all phases: run a link-graph check to confirm no orphan pages

### Manual Verification
- User reviews new pages for factual accuracy
- User confirms IMA coverage depth is sufficient

---

## Open Questions

1. **ISDA CRIF pages**: Should I create full wiki pages for both FRTB-SA and SA-CCR data standards, or only FRTB-SA (since SA-CCR is counterparty risk, not strictly market risk)?
2. **IMA depth**: Should the IMA pages be comprehensive (detailed formulas, ES calculation, desk approval criteria) or overview-level summaries?
3. **Git Status Icons page**: Delete from wiki, move to `raw/`, or keep as-is with a non-MAR tag?
4. **CRR3 Article Map**: Is the navigable CRR article index useful enough to justify a dedicated page?
