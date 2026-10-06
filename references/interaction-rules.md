# Interaction rules

## 操作建議：Age-friendly Recommendation

- 主要操作以實際 hit area 至少 44 × 44 CSS px 作起點，並兼顧間距、裝置及內容密度；不要只放大 icon。AA／AAA 界線見 [WCAG](wcag-2.2.md)。
- 主要與次要動作使用可理解的動詞和對象；熟悉位置維持穩定。危險操作不要與常用動作緊鄰且視覺相同。
- 高後果操作顯示對象、影響範圍與可否復原，按風險選擇預覽、確認、可撤銷或復原機制；避免每一步都跳確認。
- Selected、disabled、focus、hover 應可區分；觸控使用者不依賴 hover 才取得操作。停用時解釋原因與如何繼續。
- 等待時保留操作上下文，防止重複提交；回饋要足夠持久，避免只能在短暫 toast 讀取關鍵結果。沒有統一強制顯示秒數。

## Feedback 與規格狀態表

逐項標為「已定義／缺漏／不適用／待驗證」，不要要求所有頁面都有所有狀態。

| 狀態 | 規格或實作需要回答 |
| --- | --- |
| Loading | 正在載入什麼？內容尚未完成或真的沒有資料？等待中哪些操作可用？ |
| Processing | 是否已收到提交？是否防重複？背景處理如何查看結果？取消是否真的可行？ |
| Success | 完成了什麼、哪個對象、結果在哪？下一步或返回入口是什麼？ |
| Error | 哪裡出錯、如何修正？輸入是否保留？網路失敗能否重試？結果不明時先查狀態，避免重送產生重複資料。 |
| Empty | 首次無資料、搜尋無結果、權限不足是否分清？有清除篩選或建立資料入口嗎？ |
| Warning | 有什麼後果？可以如何避免？取消後回到哪裡且保留什麼？ |

視覺回饋、語意宣告與 focus 管理分開查；WCAG 4.1.3 適用範圍見 [WCAG](wcag-2.2.md)。

## Frontend code review

先追到實際 rendered DOM、共用元件、樣式與事件實作；React／Vue 元件名稱不能證明語意，Next.js／Nuxt 要留意 hydration 前後狀態與路由後焦點。只看局部片段時說明推論範圍。

| 檢查 | 需要的證據與修改方向 |
| --- | --- |
| Semantic HTML／button vs div | 找互動事件是否僅綁在 div/span；用原生 button 執行動作、a 導航。非原生元件需完整鍵盤、角色、名稱及狀態，單加 role 不夠。 |
| Label／form association | 檢查 id 與 for／htmlFor 或有效包覆；placeholder 不替代持續可見標籤。關聯提示、錯誤與欄位，ID 避免重複。 |
| Keyboard／focus | Tab 順序、Enter／Space、退出 dialog、關閉後回焦；檢查 outline 移除是否有替代 focus 樣式，固定區塊有無遮擋。 |
| ARIA | 優先原生語意；aria-label 不應與可見名稱互相矛盾。核對 expanded、pressed、selected、invalid 等是否與實際狀態同步。 |
| Disabled | 原生 disabled 與 aria-disabled 行為不同；後者不會自動阻止 click 或 keyboard。查實際防重複及阻擋邏輯，說明停用原因。 |
| Contrast／target | 解析繼承、theme、透明度、padding 與實際 hit area；程式碼無法決定有效值則 runtime 驗證。 |
| Error／status | 錯誤有文字、欄位關聯與修正建議；異步成功／失敗可讀且適當宣告，避免大量 assertive 訊息。 |
| Responsive／zoom | 查固定高度、overflow:hidden、絕對定位、min-width、文字省略與縮放限制，再驗證 200% resize／reflow。 |
| Destructive action | 追 handler 到實際後果、確認或撤銷、失敗與重試分支；不由按鈕外觀臆測不可逆。 |

每項 finding 提供現有檔案與精確位置，最小修正及驗證步驟。不要為套框架而改寫整個系統。Code 範例見 [frontend-code-review](../examples/frontend-code-review.md)。

## 來源與文件聲明

本文件含獨立整理的說明或參考 W3C 資料的摘要，非官方規範或授權翻譯，亦未獲 W3C／WAI 背書。來源、權利歸屬及適用授權條款見 [第三方聲明](../THIRD_PARTY_NOTICES.md)。
