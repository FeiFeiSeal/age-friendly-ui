# Review workflow、severity 與輸出

## Workflow

1. **範圍**：確認模式、素材、主要任務、使用者情境與裝置；缺少資料列假設，先處理已有證據。
2. **沿任務走查**：看懂資訊 → 找操作 → 啟動 → 讀取回饋 → 下一步 → 錯誤恢復。Screenshot 只走可見部分；spec 查定義與分支；code 查實作及可重現行為。
3. **按問題查 references**：visual、interaction、cognitive；有 WCAG 主張時核對 SC、level、門檻與例外，不靠印象配號。
4. **記錄證據**：畫面區域、規格引文、檔案行號、量測條件或重現步驟。標 `Confirmed`（在提供範圍內可證）、`Potential`（有風險待驗證）或 `Not assessable`（缺素材）。純未測項目放「未驗證範圍」，不灌成問題數量。
5. **分類排序**：Type 與 Severity 是兩條軸；Age-friendly recommendation 也可能 HIGH。合併同根因，不把同一問題的多個 SC 當多個 finding。
6. **可執行修正**：優先最小範圍改善，具體到文案、狀態、元件、流程或 code；附驗證方式。重構模式補充保留／調整／理由／驗證。
7. **結尾**：列最優先修正、待驗證與已知限制。完成修改後只重查受影響流程及狀態，不以工具分數宣稱合規。

## Severity

| 等級 | 判準 |
| --- | --- |
| HIGH | 主要任務無法完成、高機率誤操作、重要狀態／關鍵資訊不可辨識、不可逆風險；或已確認違反 WCAG 2.2 A／AA、因而阻礙 AA 合規。 |
| MEDIUM | 明顯增加認知負擔、操作時間、誤觸、學習或狀態判讀成本。 |
| LOW | 視覺一致性、次要資訊 hierarchy、輕度可讀性與 UX polish。 |

A／AA 已確認違規列 HIGH 是本 skill 的 review 政策，不是 WCAG 官方 severity。AAA 不符合依實際影響分級。待驗證問題可以因任務後果列 HIGH，但明寫「風險分級；尚未確認違規」，不可從疑似色淡直接推定 HIGH WCAG violation。

## 每項問題格式

### Issue
清楚問題標題與具體位置；必要時引用 code／spec。
### Severity
HIGH / MEDIUM / LOW；一句任務影響理由。
### Type
WCAG Requirement **或** Age-friendly Recommendation。一個 finding 只用一個主要 Type；額外建議明標，避免混成同一要求。
### Evidence
Confirmed / Potential；依據、範圍與未知。不能確認的視覺數值不寫成實測。
### Why it matters
說明高齡使用者如何受影響，例如誤觸、忘記資訊、重送、無法恢復。
### Recommendation
具體可執行修改與驗證方式。若含額外 UX 改善，明確標為推薦而非 SC 必要作法。
### Reference
WCAG：SC 編號、名稱、等級及官方連結，寫明適用條件／例外判斷。
Recommendation：對應本 skill rule／guidance，說明為設計建議。SC 尚不確定則寫「WCAG 對應待確認」，不能猜。

## 證據界線

| 輸入 | 可處理 | 常需補驗證 |
| --- | --- | --- |
| Screenshot／mockup | 可見層級、文案、分組、狀態線索、疑似視覺風險 | CSS px、實際色值、hit area、鍵盤／focus、ARIA、未呈現狀態及恢復流程 |
| PRD／spec | 流程與規則矛盾、缺漏狀態、沒有定義的後果 | 實作是否與規格一致、實際可用性 |
| Code | 語意、事件、表單關聯、明確樣式和流程問題 | cascade、共用元件、runtime、讀屏、zoom、API 結果與伺服器行為 |

若沒有可支持的問題，直接說在目前範圍未發現問題並列未測部分，不必湊 HIGH／MEDIUM／LOW 各一項。
