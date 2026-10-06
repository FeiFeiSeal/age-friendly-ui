# Mode 3：UI specification review 示範

教學輸入（假想規格 §2）：
> 第一步顯示本次申請流水號。第二步須手動重新輸入該流水號，畫面不再顯示且無選取／帶入方式。它僅供一般對照，不涉及安全或必要的記憶測試，且本次流程仍有效。按送出後顯示成功。

## Finding 1
### Issue
§2 要求在同一流程回憶並重填剛提供的流水號。
### Severity
HIGH — 依規格已確認與 AA 合規所需的 A 級要求衝突。
### Type
WCAG Requirement
### WCAG finding status
Confirmed violation（僅限本例明示的證據範圍）
### Evidence
Confirmed（規格層面）— 明確要求重填且排除了本例的必要、安全與失效例外；未驗證實作。
### Why it matters
短期記憶負擔使使用者容易漏字或反覆返回，可能放棄申請。
### Recommendation
驗收文字：「第二步自動帶入本次流水號，或提供可選取資訊，無須回憶重填。」測試跨步驟後值仍正確，回上一步不丟失有效輸入。
### Reference
[SC 3.3.7 Redundant Entry, A](https://www.w3.org/TR/WCAG22/#redundant-entry)。

## Finding 2
### Issue
§2 沒有定義送出等待、失敗或結果不明時如何繼續。
### Severity
MEDIUM — 增加等待不確定感與重複提交風險。
### Type
Age-friendly Recommendation
### Evidence
Confirmed（規格缺漏）— 不代表實作一定沒有處理。
### Why it matters
使用者無法判斷是否收到申請，可能重複按送出或離開後重填。
### Recommendation
驗收文字：「送出後顯示『正在送出申請』並防重複操作；成功後顯示申請對象、結果與查看入口；失敗保留輸入並提供可行下一步；結果不明先查詢提交狀態，再決定是否重試。」實作策略由團隊確認，測試慢速網路及結果不明分支。
### Reference
[Feedback 狀態表](../references/interaction-rules.md)。這是狀態完整性建議，不因缺少此段文字直接判 SC 4.1.3 違規。
