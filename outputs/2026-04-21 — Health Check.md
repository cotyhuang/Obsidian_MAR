---
tags: [health-check, maintenance]
created: 2026-04-21
---
# Health Check — 2026-04-21

> [!info] Scope
> Automated + manual review of all 21 wiki pages per `agent.md` §6.

---

## 1. Contradictions

✅ **None found.** All risk weights, correlation parameters, and formulas are internally consistent across pages. Cross-references from the SBM hub page match the values in individual risk class pages.

---

## 2. Blind Spots — Topics Mentioned But No Own Page

| Topic Mentioned | Where | Priority |
|---|---|---|
| **IMA (Internal Models Approach)** | [[FRTB Overview]] §2.4 | 🔴 High — MAR30–33 are in the PDF but not yet documented |
| **P&L Attribution Test** | [[FRTB Overview]], [[FRTB SA — Basel vs CRR3 Comparison]] | 🟡 Medium — referenced but no detail page |
| **Risk Factor Eligibility Test** | [[FRTB SA — Basel vs CRR3 Comparison]] §4.3 | 🟡 Medium |
| **Expected Shortfall** | [[agent.md]] knowledge domain | 🟡 Medium — core IMA risk measure |
| **Simplified SA (MAR40)** | [[FRTB SA — Basel vs CRR3 Comparison]] §2 | 🟢 Low |
| **CRE40–44 (Securitisation framework)** | [[FRTB SA — Default Risk Charge]] §7 | 🟢 Low — banking book topic |

---

## 3. Unsupported Claims — Wiki Statements Without `raw/` Source

✅ All 20 topical wiki pages have `sources:` frontmatter linking to `[[raw/MAR_20260323]]` or other raw files.

**Exception:**
- `Untitled.md` — has no `sources:` field (this is a Git/VSCode reference note, not a MAR topic page; consider moving to `raw/` or deleting)

---

## 4. Stale Content

| Item | Status |
|---|---|
| Basel effective date (1 Jan 2023) | ✅ Current per MAR standard |
| CRR3 timeline (2025–2026) | ⚠️ May need update as EU phased implementation progresses |
| Specified currency pairs (MAR21.88) | ✅ Current — 19 USD pairs as per latest MAR |
| EBA RTS references | ⚠️ Check if EBA has published final RTS since June 2024 |

---

## 5. Structural Findings

### Link Graph
- **21 wiki pages**, all properly linked via `[[wikilinks]]`
- **INDEX.md** lists all FRTB SA pages
- No orphan FRTB pages (only `Untitled.md` is orphaned — not a MAR topic)

### Worked Examples Coverage
| Risk Measure | Examples | Page |
|---|---|---|
| Delta (FX) | ✅ | [[FRTB SA — FX Risk]] §9 |
| Delta (GIRR, multi-tenor) | ✅ | [[FRTB SA — GIRR]] §10 |
| DRC (non-sec, full pipeline) | ✅ | [[FRTB SA — Default Risk Charge]] §10 |
| Curvature (Equity) | ✅ | [[FRTB SA — Equity Risk]] §9 |
| Vega | ❌ None yet | — |

### PDF Citation Coverage
- 103+ deep-links to `[[MAR_20260323.pdf#page=X|...]]`
- All 11 FRTB SA pages have PDF citations
- Pre-existing pages (Banking Book, Basel RBC25, etc.) cite their own raw sources

---

## 6. Recommendations

1. **Create IMA pages** (MAR30–33) — this is the largest content gap
2. **Add a Vega worked example** — only risk measure without a numerical example
3. **Update CRR3 page** when EBA publishes final RTS
4. **Move `Untitled.md`** to `raw/` or rename to `Git Status Icons.md`
