---
tags: [MAR, FRTB, look-through, CIU, EIIF, Q&A]
sources:
  - "[[raw/MAR_20260323]]"
  - "[[raw/RBC25]]"
  - "[[raw/CRR_20260101]]"
  - "[[raw/Basel MAR Look-Through Approach Resources]]"
created: 2026-11-12
---
# Q&A — 什麼是 Basel MAR Look-Through Approach？適用在哪個 Risk Class？

> [!info] 對應 Wiki 專頁與 Raw 資源
> - **Wiki 專頁**：[[FRTB SA — Look-Through Approach]]
> - **Raw 外部連結與資源整理**：[[raw/Basel MAR Look-Through Approach Resources]]

---

## 1. 什麼是 Basel MAR Look-Through Approach（穿透法）？

根據巴塞爾市場風險框架 **MAR10.8**（[[MAR_20260323.pdf#page=8|MAR10.8, page 8]]）之官方定義：

> **Look-Through Approach (LTA，穿透法)** 是指銀行在計算具有多個底層標的（underlyings）之部位（例如：**指數工具 index instruments**、**多標的選擇權 multi-underlying options**，或**基金股權投資 equity investments in a fund / CIUs**）的市場風險資本計提時，**將其底層部位視為由銀行直接持有（as if the underlying positions were held directly by the bank）**來計算風險敏感度與資本計提的方法。

### 核心運作原則
1. **依持股比例與槓桿拆解（MAR21.35）**：針對基金投資（EIIFs / CIUs），銀行必須按其持有該基金之權益比例（proportional share）以及基金結構內含之任何槓桿（leverage），將基金底層持倉拆解為個別資產部位。
2. **無限制單一標的互抵（Unrestricted Single-Name Netting, MAR21.34(1)）**：一旦採用穿透法（Index CTP 除外），從指數、多標的選擇權或基金拆解出來的個別成分風險因子敏感度，**可以與銀行直接持有的單一發行人（single-name）部位無限制互抵（netting）**。
3. **Delta 與 Curvature 一致性（MAR21.32）**：對同一工具，無論是否採用穿透法，Delta 與 Curvature 風險計算所使用的敏感度輸入必須一致。
4. **時間一致性（MAR21.34(3)）**：一旦對特定指數之工具選擇採用穿透法，必須隨時間一致適用，若要改回「不穿透（no look-through）」必須取得監理機關核准。

---

## 2. Look-Through Approach 是用在哪個 Risk Class（風險類別）？

這需要區分 **「(A) 執行完全穿透拆解」**、**「(B) 合格指數/追蹤指數基金選擇不穿透（No Look-Through Opt-Out）」** 與 **「(C) 無法穿透之基金替代法（Fallbacks）」** 三種情境：

| 情境 | 適用之 SBM Risk Classes 與資本計提模組 | 法規依據 |
|---|---|---|
| **情境 A：執行完全穿透法（Full Look-Through）**<br>*(可穿透基金、客製化籃子、非合格指數、或自願穿透之合格指數)* | **涵蓋全部 7 個 SBM Risk Classes + DRC + RRAO**（視底層資產實際屬性而定）：<br>1. **[[FRTB SA — GIRR\|GIRR（一般利率風險）]]**：底層債券、利率衍生品、基金現金部位之無風險殖利率曲線<br>2. **[[FRTB SA — CSR Non-Securitisation\|CSR Non-Securitisation（非證券化信用利差）]]**：底層公司債、主權債、CDS<br>3. **[[FRTB SA — CSR Securitisation\|CSR Securitisation (non-CTP)]]**：底層證券化部位<br>4. **[[FRTB SA — CSR CTP\|CSR Securitisation (CTP)]]**：*(註：MAR21.34(2) 規定 Index CTP 本身不得拆解為成分)*<br>5. **[[FRTB SA — Equity Risk\|Equity Risk（股權風險）]]**：底層個別股票成分<br>6. **[[FRTB SA — Commodity Risk\|Commodity Risk（商品風險）]]**：底層大宗商品部位<br>7. **[[FRTB SA — FX Risk\|FX Risk（外匯風險）]]**：底層資產計價幣別與銀行報導幣別不同之匯率暴險<br>• **[[FRTB SA — Default Risk Charge\|DRC（違約風險）]]**：信用與股權衍生品強制穿透至單一發行人計算 JTD（MAR22.5） | MAR10.8, MAR21.31, MAR21.34, MAR21.35, MAR22.5 |
| **情境 B：選擇「不穿透」（No Look-Through Opt-Out）**<br>*(符合 MAR21.31 五大條件之上市廣泛認可指數，或年化追蹤誤差 $<1\%$ 之指數型基金/ETF)* | **僅限於 2 個 SBM Risk Classes**（計算單一指數敏感度）：<br>1. **[[FRTB SA — Equity Risk\|Equity Risk（股權風險）]]**：若單一產業權重 $>75\%$ 歸入該產業 Bucket (1–11)；否則歸入 **Equity Index Buckets（Bucket 12 大型已開發市場指數 $\text{RW}=15\%$；Bucket 13 其他股權指數 $\text{RW}=25\%$）**<br>2. **[[FRTB SA — CSR Non-Securitisation\|CSR Non-Securitisation（非證券化信用利差）]]**：若單一產業權重 $>75\%$ 歸入該產業 Bucket (1–16)；否則歸入 **CSR Index Buckets（Bucket 17 投資等級 IG 指數 $\text{RW}=1.5\%$；Bucket 18 高收益 HY 指數 $\text{RW}=5.0\%$）**<br>*(註：DRC 仍須依 MAR22.5 對成分發行人進行穿透計算)* | MAR21.31, MAR21.33, MAR21.35(2), MAR21.38 |
| **情境 C1：不可穿透基金 — 授權法 / 假設投資組合法（Mandate-Based Hypothetical Portfolio）** | **涵蓋基金投資授權（Mandate）允許之所有 SBM Risk Classes**：<br>• 經監理機關核准，假設基金在 Mandate 上限內優先投資於 SBM 資本計提最高之資產與最大風險權重，且必須**獨立計算（stand-alone）**，不可與銀行其他部位互抵。<br>• 衍生品之 CCR 與 CVA 依銀行簿 CRE60.7(c) 簡化法計算。 | MAR21.36(2), CRR3 Art. 325j(1)(b)(ii) & (4) |
| **情境 C2：不可穿透基金 — 未評等「其他產業」權益法（Unrated "Other Sector" Equity Fallback）** | • **SBM**：強制歸入 **[[FRTB SA — Equity Risk\|Equity Risk]] — Bucket 11 ("Other sector")**（$\text{Delta RW} = 70\%$，無相關性抵減）<br>• **[[FRTB SA — Default Risk Charge\|DRC]]（MAR22.8）**：視為未評等股票（$\text{LGD}=100\%$，$\text{RW}=15\%$）；若 Mandate 允許投資高收益或違約債，須按 Mandate 最大可能比例依序假設投資 Defaulted ($100\%$) $\to$ CCC ($50\%$) $\to$ B ($30\%$) $\to$ BB ($15\%$) 計算有效平均風險權重，且不得互抵<br>• **[[FRTB SA — Residual Risk Add-On\|RRAO]]（MAR23.6(5)）**：假設在 Mandate 最大允許範圍內暴險於奇異標的（$1.0\%$）與其他殘餘風險（$0.1\%$） | MAR21.36(3), MAR22.8, MAR23.6(5), CRR3 Art. 325j(1)(b)(i) |
| **情境 D：SA-CVA / BA-CVA 風險框架** | **3 個 CVA Risk Classes** 可選擇引入合格指數風險因子（如 Bucket 8）或強制穿透（Buckets 1–7）：<br>• Counterparty Credit Spread Risk<br>• Reference Credit Spread Risk<br>• Equity Risk | MAR50.49–50.50, MAR50.64 |

---

## 3. 合格指數「免穿透（No Look-Through）」之 5 大條件（MAR21.31 / CRR3 Art. 325i）

唯有同時滿足下列 5 項條件的上市且廣泛認可之股權或信用指數，銀行才可選擇**不穿透**：
1. **成分透明**：指數成分與權重已知（具備可穿透性）；
2. **成分數量**：至少包含 **20 檔**成分標的；
3. **單一成分集中度**：單一成分權重不超過指數總體的 **$25\%$**；
4. **前段成分集中度**：最大的前 $10\%$ 成分權重合計小於指數總體的 **$60\%$**；
5. **總市值門檻**：所有成分總市值不低於 **USD 40 billion**（歐盟 CRR3 Art. 325i(3)(e) 為 **EUR 40 billion**）。

---

## 4. 網路資源連結（已收錄至 `raw/Basel MAR Look-Through Approach Resources.md`）

1. **BIS Basel Framework — MAR10 (Market Risk Terminology, MAR10.8)**:
   [https://www.bis.org/basel_framework/chapter/MAR/10.htm](https://www.bis.org/basel_framework/chapter/MAR/10.htm?inforce=20230101&published=20200327)
2. **BIS Basel Framework — MAR21 (Sensitivities-Based Method, MAR21.31–21.38)**:
   [https://www.bis.org/basel_framework/chapter/MAR/21.htm](https://www.bis.org/basel_framework/chapter/MAR/21.htm?inforce=20230101&published=20240705)
3. **BIS Basel Framework — MAR22 (Default Risk Capital Requirement, MAR22.5 & MAR22.8)**:
   [https://www.bis.org/basel_framework/chapter/MAR/22.htm](https://www.bis.org/basel_framework/chapter/MAR/22.htm?inforce=20230101&published=20200327)
4. **BIS Basel Framework — RBC25 (Boundary Between Banking Book and Trading Book, RBC25.8(5))**:
   [https://www.bis.org/basel_framework/chapter/RBC/25.htm](https://www.bis.org/basel_framework/chapter/RBC/25.htm)
5. **EBA Interactive Single Rulebook — CRR Article 325i (Index & Multi-Underlying Instruments)**:
   [https://www.eba.europa.eu/regulation-and-policy/single-rulebook/interactive-single-rulebook/12191](https://www.eba.europa.eu/regulation-and-policy/single-rulebook/interactive-single-rulebook/12191)
6. **EUR-Lex — Regulation (EU) 2024/1623 (CRR3 Articles 325i & 325j)**:
   [https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202401623](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202401623)
7. **Decode Finance — FRTB MAR21 Series 8D: SBM Mechanics & Look-Through**:
   [https://decode-finance.com/frtb-mar21-series8d-sbm-mechanics-look-through/](https://decode-finance.com/frtb-mar21-series8d-sbm-mechanics-look-through/)
8. **ISDA & IIF — Response to EC Consultation on Market Risk Prudential Framework (CIUs & Indices)**:
   [https://www.isda.org/a/vgfgE/ISDA-IIF-Response-to-ECs-Consultation-on-the-Market-Risk-Prudential-Framework.pdf](https://www.isda.org/a/vgfgE/ISDA-IIF-Response-to-ECs-Consultation-on-the-Market-Risk-Prudential-Framework.pdf)
9. **KPMG — Basel 4 Publications: FRTB Standardised Approach & CIU Treatment**:
   [https://assets.kpmg.com/content/dam/kpmgsites/xx/pdf/2022/08/basel-4-publications.pdf.coredownload.inline.pdf](https://assets.kpmg.com/content/dam/kpmgsites/xx/pdf/2022/08/basel-4-publications.pdf.coredownload.inline.pdf)

