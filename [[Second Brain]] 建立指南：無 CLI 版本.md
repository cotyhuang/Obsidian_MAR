---
tags: [obsidian, second-brain, ai, knowledge-management]
aliases: [Karpathy Second Brain Walkthrough, Antigravity AI Knowledge Base]
---
# 1 [[Second Brain]] 建立指南：無 CLI 版本

> [!info] 核心概念
> 這個系統的核心在於「簡單的資料夾結構」加上「明確的 Schema 規則檔」，而非必定依賴終端機工具。只要 AI 能讀寫檔案，就能達到相同效果。

## 1.1 Antigravity (Claude Ops) 與 Claude CLI 比較
- **[[Antigravity]] (Claude Ops)**：透過圖形化工作區操作。只要確保系統有讀寫權限，便能在背景閱讀 `raw/` 並生成 `wiki/`，適合偏好視覺化介面的使用者。
- **Claude CLI**：於本地端運行，直接存取檔案系統。文章中的自動爬蟲（如 `agent-browser`）即依賴此環境運行。

## 1.2 實作 Walkthrough (無 CLI)

### 1.2.1 建立基礎資料夾
在 [[Obsidian Vault]] 中建立三個全新資料夾：
- **`raw/`**：存放未經整理的原始素材（文章、筆記、截圖）。
- **`wiki/`**：存放 AI 整理好的維基百科區。
- **`outputs/`**：存放 AI 回答問題的報告與分析。

### 1.2.2 收集原始素材
- 手動複製貼上為 `.md` 檔，或使用 **MarkDownload** 等擴充功能下載網頁至 `raw/` 資料夾。
- > [!warning] 注意事項
  > 絕對不要手動整理、修改檔名或排版，保留原始混亂狀態，讓 AI 處理。

### 1.2.3 撰寫 [[Schema]] 檔
在根目錄建立 `CLAUDE.md` 或 `AGENTS.md`，作為 AI 的最高指導原則。
- 定義知識庫主題、資料夾架構規則。
- 設定 Wiki 規則（例如：使用 `[[主題名稱]]` 建立雙向連結、維護 `INDEX.md`）。

### 1.2.4 啟動 AI 編譯
在 [[Antigravity]] 開啟對應工作區，使用以下提示詞：
- 「請閱讀 `raw/` 中的所有內容。然後根據 `CLAUDE.md` 中的規則，在 `wiki/` 中編譯一個 wiki。請先建立 `INDEX.md`，然後為每個主要主題建立一個 `.md` 檔案。連結相關主題，並總結每個來源。」

### 1.2.5 提問與健康檢查
- **提問**：向知識庫提問，並將獲得的高品質解答存入 `outputs/`。
- **每月健康檢查**：定期要求 AI 檢查 `wiki/` 目錄，標記矛盾處、找出未解釋的盲點，並列出缺乏 `raw/` 來源支持的聲明，避免錯誤疊代。

#PKM #Obsidian #Antigravity #AI流程