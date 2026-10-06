---
name: age-friendly-ui
description: Design, incrementally redesign, and review Web or administrative interfaces for older users, using screenshots, UI specifications, or frontend code. Use when age-friendly usability is requested; distinguish WCAG 2.2 requirements from recommendations about clarity, familiarity, feedback, and recovery. Not a general accessibility certification audit.
metadata:
  version: "0.1.0"
---

# Age-friendly UI

協助高齡使用者完成實際任務。優先順序：**看得懂 → 找得到 → 點得到 → 知道發生什麼 → 知道下一步 → 做錯可以恢復**。
不把年齡等同於能力；不以全面放大、粗框、高飽和配色或「老人模式」替代設計判斷。

## 核心約束

- 每項 finding 分開標示 `WCAG Requirement` 或 `Age-friendly Recommendation`。WCAG 須附 SC、等級、適用條件與官方連結；無法核對時不要猜條款。
- 預設以 WCAG 2.2 A／AA 為檢查基線；AAA 必須明標，不能當作 AA 要求。WCAG 有可測試條件，但並非每條都有數值門檻。
- 證據不足用「待驗證」；靜態截圖不能證明鍵盤行為、DOM 語意、讀屏宣告、實際點擊區或流程恢復能力。未呈現不等於不存在。
- 既有系統先保留資訊架構、主要功能位置、熟悉流程，再局部改善。若需要搬動或更換 pattern，說明任務阻礙與重新學習代價。
- Review 不自動授權修改或發佈。要求修正時才在指定範圍實作；不要宣稱一次 review 等於全站合規。

## 選擇模式與閱讀範圍

共用 [review-checklist.md](references/review-checklist.md) 的 workflow、severity 與輸出格式。
首次建立高齡使用情境時讀 [older-users.md](references/older-users.md)；遇到 WCAG 判定時查 [wcag-2.2.md](references/wcag-2.2.md)。其餘只讀當前問題相關章節。

| 模式 | 處理方式與 references |
| --- | --- |
| 1 Screenshot / UI Review | 檢視實際影像，標明畫面與區域；讀 [visual-rules](references/visual-rules.md)，按可見內容查 [interaction-rules](references/interaction-rules.md)、[cognitive-rules](references/cognitive-rules.md)。範例：[screenshot-review](examples/screenshot-review.md)。 |
| 2 Redesign Recommendation | 沿原任務流程改善 typography、contrast、hierarchy、spacing、button priority、feedback、error prevention、boundary。按需要讀上述三份規則；輸出「保留／調整／理由／驗證方式」，將必要流程變動單獨解釋。 |
| 3 UI Specification Review | 對 PRD、Markdown、guideline、user flow 查 [interaction-rules](references/interaction-rules.md) 的狀態表與 [cognitive-rules](references/cognitive-rules.md) 的規格問題；引用原文或段落。範例：[ui-spec-review](examples/ui-spec-review.md)。 |
| 4 Frontend Code Review | 適用 HTML、CSS、JS／TS、React／Vue、Next.js／Nuxt；讀 [interaction-rules](references/interaction-rules.md) 的 code review，按 CSS 與流程讀視覺／認知規則。指出檔案、行號或片段、原因、具體修正；必要時附 code。範例：[frontend-code-review](examples/frontend-code-review.md)。 |

## 完成條件

使用共用格式依 HIGH → MEDIUM → LOW 報告，明列證據與未測範圍；同一根因不要重複計數。
修改後重查受影響狀態與主要任務。建議必須能轉成具體調整與驗證步驟，並說明對高齡使用者的影響，而非只報 SC 編號。
