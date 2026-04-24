---
tags: [schema, agent, pkm-rules]
aliases: [AGENTS, CLAUDE, Schema Rules]
---
# Agent Schema — Obsidian MAR Knowledge Base

> [!info] Purpose
> This file is the **highest-level instruction set** for any AI agent operating inside this Obsidian vault.
> It defines the knowledge domain, folder conventions, wiki formatting rules, and maintenance workflows.

---

## 1. Knowledge Domain

This vault focuses on **Market Risk (MAR)** and related prudential banking regulation, including but not limited to:

- Basel Framework — Minimum capital requirements for market risk (MAR 10–99)
- Fundamental Review of the Trading Book (FRTB)
- Banking book vs Trading book boundary (RBC 25)
- EBA CRR / CRR3 implementation in the EU
- Standardised Approach (SA) and Internal Models Approach (IMA)
- Risk measures: Expected Shortfall, Stressed ES, Default Risk Charge (DRC)
- Sensitivity-Based Method (SbM), risk factor eligibility, P&L attribution

---

## 2. Folder Architecture

| Folder | Purpose | Who writes |
|---|---|---|
| `raw/` | Unprocessed source material — articles, PDFs, web clippings, personal notes. **Never modify these files.** | Human |
| `wiki/` | Curated, interlinked wiki pages distilled from `raw/`. | AI agent |
| `outputs/` | Q&A reports, analysis documents, and health-check results generated on request. | AI agent |

### Rules

1. **Never delete or edit files in `raw/`.**  Raw material is the single source of truth.
2. **All wiki pages live in `wiki/`.** Do not create topic pages at the vault root.
3. **All generated reports live in `outputs/`.** Name reports with a date prefix: `YYYY-MM-DD — <title>.md`.

---

## 3. Wiki Formatting Rules

### 3.1 INDEX.md

- `wiki/INDEX.md` is the **master table-of-contents** for the entire wiki.
- It must list every wiki page with a `[[wikilink]]` and a one-line description.
- Group entries by thematic section.

### 3.2 Individual Wiki Pages

- **Filename**: use the topic name in plain English, e.g. `Banking Book vs Trading Book.md`.
- **Frontmatter** (YAML):

  ```yaml
  ---
  tags: [<relevant tags>]
  sources:
    - "[[raw/<source filename>]]"
  created: YYYY-MM-DD
  ---
  ```

- **Wikilinks**: use `[[Topic Name]]` to create bidirectional links between related concepts.
- **Source attribution**: every factual claim should reference its `raw/` source via `[[raw/filename]]`.
- **Heading structure**: use a single `# H1` title, then `## H2` sections. Keep headings concise.
- **Tables**: prefer markdown tables for comparisons and structured data.
- **Callouts**: use Obsidian callout syntax (`> [!note]`, `> [!warning]`, etc.) for important distinctions.

### 3.3 Linking Convention

- Always check existing wiki pages before creating a new one — avoid duplicates.
- When a concept is mentioned that has its own wiki page, wrap it in `[[double brackets]]`.
- Maintain a `## See Also` section at the bottom of each page listing related wiki pages.

---

## 4. AI Compilation Workflow

When prompted to compile or update the wiki:

1. **Token Optimization (Read `.md` first)**: When processing files in `raw/`, if a source exists as both a `.md` (text extraction) and a `.pdf` with the same filename, **always read the `.md` file first**.
2. **Conditional PDF Parsing**: Only read the corresponding `.pdf` file if the `.md` lacks sufficient detail, if you need to verify a specific regulatory table/formula (e.g., IMA calculations), or if the user explicitly asks for details not found in the text.
3. **Identify** distinct topics and key concepts from the read materials.
4. **Create or update** `wiki/INDEX.md` first.
5. **Create one `.md` page per major topic** in `wiki/`, following the formatting rules above.
6. **Interlink** related pages using `[[wikilinks]]`.
7. **Summarise** each raw source, preserving factual accuracy and regulatory references.

---

## 5. Q&A Workflow

When the user asks a question:

1. Search `wiki/` and `raw/` for relevant information.
2. Compose a well-structured answer with citations.
3. Save the answer to `outputs/YYYY-MM-DD — <question summary>.md`.

---

## 6. Monthly Health Check

When prompted for a health check:

1. **Contradictions**: flag any conflicting statements across wiki pages.
2. **Blind spots**: identify topics mentioned but not yet explained in their own page.
3. **Unsupported claims**: list statements in `wiki/` that lack a corresponding `raw/` source.
4. **Stale content**: flag pages that reference outdated regulatory dates or superseded rules.
5. Save the report to `outputs/YYYY-MM-DD — Health Check.md`.

---

## 7. General Principles

- **Accuracy over volume**: prefer concise, correct summaries over exhaustive reproduction.
- **Preserve original language** for regulatory definitions and article references.
- **Be explicit about uncertainty**: if a raw source is ambiguous, note it with `> [!warning]`.
- **Token Efficiency (MD over PDF)**: To conserve context window, always prioritize reading `.md` files over `.pdf` files. If `raw/Basel_FRTB.md` and `raw/Basel_FRTB.pdf` both exist, read the `.md` first. Only parse the PDF if deep regulatory specifics are missing from the markdown version.

---

## 8. State Management & Persistence

To ensure work continuity across sessions and quota refills, the agent must adhere to the following:

1. **Mirror Artifacts**: The agent must always maintain a copy of the internal system artifacts in the workspace root:
   - `implementation_plan.md` -> `PLAN.md`
   - `task.md` -> `TASKS.md`
2. **Auto-Resume Protocol**: At the start of every session or after a quota refill, the agent must read `TASKS.md` and `PLAN.md` to synchronize its state and identify pending items.
3. **Execution Continuity**: If a task is interrupted, the agent will refer to `TASKS.md` to pick up exactly where it left off without requiring the user to re-explain the context.
4. **Synchronization**: Any change to the internal `task.md` or `implementation_plan.md` must be mirrored to the workspace files immediately before ending a turn.
5. **Task Archiving**: When a task is confirmed as "Complete" or "Finalized" by the user:
   - Mirror the final state to `outputs/`.
   - Name the archived files using the format: `outputs/YYYY-MM-DD — <Task Name> — PLAN/TASKS.md`.
   - Delete the root `PLAN.md` and `TASKS.md` to clear the workspace for new missions.
