# Plan to Initialize Obsidian_OPE for Operational Risk

This plan outlines the steps to initialize a new Obsidian Vault at `D:\MyApp\Obsidian_OPE` for **Operational Risk (OPE)**. It will replicate the structure and configuration of the Market Risk vault (`Obsidian_MAR`) while customizing the domain instructions and initial wiki structure for operational risk.

## User Review Required

> [!IMPORTANT]
> **Domain Adaptation**: The agent rules (`agent.md`) will be customized to focus on Operational Risk (Basel OPE, SMA, Loss Data, RCSAs, KRIs, Operational Resilience, DORA) instead of Market Risk (Basel MAR, FRTB, SbM, Expected Shortfall). Please review the proposed domain details below.

> [!NOTE]
> We will copy the Obsidian configuration (`.obsidian/` folder) and `.gitignore` from `Obsidian_MAR` to ensure plugins (`pdf-plus`, `cursor-integration`) and layout behaviors are preserved.

## Proposed Changes

### Configuration and Structure Setup
We will perform directory creation and file copies to set up the structural foundation.

#### [NEW] [raw](file:///D:/MyApp/Obsidian_OPE/raw)
- Create empty directory for raw sources.

#### [NEW] [outputs](file:///D:/MyApp/Obsidian_OPE/outputs)
- Create empty directory for Q&A and health check outputs.

#### [NEW] [.gitignore](file:///D:/MyApp/Obsidian_OPE/.gitignore)
- Copy from `d:\MyApp\Obsidian_MAR\.gitignore`.

#### [NEW] [.obsidian](file:///D:/MyApp/Obsidian_OPE/.obsidian)
- Copy all configuration and plugins from `d:\MyApp\Obsidian_MAR\.obsidian` (excluding `workspace.json` to keep the layout clean).

---

### Custom Agent and Index Setup

#### [NEW] [agent.md](file:///D:/MyApp/Obsidian_OPE/agent.md)
- Copy from `d:\MyApp\Obsidian_MAR\agent.md` and customize for Operational Risk.
- Focus domain on:
  - **Basel Framework for Operational Risk (OPE)**: Standardised Measurement Approach (SMA), Business Indicator Component (BIC), Internal Loss Multiplier (ILM).
  - **Risk Identification and Assessment**: Risk & Control Self-Assessment (RCSA), Key Risk Indicators (KRIs), Scenario Analysis.
  - **Loss Event Collection**: Basel/regulatory event types (Internal/External Fraud, Employment Practices, Clients & Products, Physical Assets, Business Disruption, Process Management).
  - **Operational Resilience**: Principles for Operational Resilience, Digital Operational Resilience Act (DORA).
  - **Reporting and Governance**: Loss database maintenance, governance structures, boundary between Operational Risk and Credit/Market Risk.

#### [NEW] [INDEX.md](file:///D:/MyApp/Obsidian_OPE/wiki/INDEX.md)
- Initialize a clean, structured table of contents for the Operational Risk wiki.
- Proposed thematic sections:
  1. **Regulatory Framework & Capital**: Basel OPE, SMA, Business Indicator calculation.
  2. **Risk Assessment Framework**: RCSAs, KRIs, Scenario Analysis.
  3. **Loss Event Management**: Internal loss data collections, Basel event categories, case studies.
  4. **Operational Resilience & IT Risk**: Principles for Operational Resilience, DORA compliance, Business Continuity Planning (BCP).
  5. **Data Standards & Reporting**: COREP tables, database schemas, risk taxonomies.

## Verification Plan

### Automated Verification
- Verify directories `raw/`, `wiki/`, and `outputs/` exist.
- Verify `agent.md` and `wiki/INDEX.md` are present.
- Verify the content of `agent.md` is customized for OPE and does not contain remaining Market Risk references (except where comparing boundaries).

### Manual Verification
- The user can open the Obsidian vault `D:\MyApp\Obsidian_OPE` to verify that the plugins (`pdf-plus`, etc.) load correctly and the default structure is clean.
