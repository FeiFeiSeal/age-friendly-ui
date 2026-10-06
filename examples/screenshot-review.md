# Mode 1：Screenshot review 示範

這是教學用假想畫面描述，不是已執行的影像測試。真實使用時必須檢視使用者提供的影像；本例沒有可用 CSS 色值或像素比例。

輸入：預約管理畫面，標題「預約資料」，右側同列有三個同色同權重按鈕「返回」「儲存」「刪除」。欄位下方說明文字看起來很淡；未展示其他狀態。

任務：修改預約日期後儲存。保留既有欄位與操作區位置。

## Finding 1
### Issue
右側操作區三個按鈕視覺權重相同，儲存與刪除不易快速區分。
### Severity
MEDIUM — 增加選擇時間與誤觸風險；尚無證據表明刪除不可逆。
### Type
Age-friendly Recommendation
### Evidence
Confirmed — 在假想輸入中三者同色同權重；點擊後行為未知。
### Why it matters
精細動作不穩或需較長辨識時間的使用者，可能誤選刪除而中斷正在編輯的任務。
### Recommendation
保留操作區，突出「儲存變更」、將「返回」降為次要，將「刪除預約」與儲存明確分組。驗證使用者能指出儲存與刪除的差別，並補查實際刪除的確認／恢復流程。
### Reference
[Interaction rules](../references/interaction-rules.md)：主次操作與危險操作。這是設計建議，不等同 WCAG 要求只有一個 CTA。

## Finding 2
### Issue
欄位說明文字疑似對比不足。
### Severity
MEDIUM — 可讀性風險，尚未確認 WCAG 違規。
### Type
WCAG Requirement
### Evidence
Potential — 僅知道畫面中文字偏淡，缺有效色值、字級與呈現條件，不能宣稱 contrast ratio。
### Why it matters
較難辨識低對比文字的使用者可能錯過日期輸入格式，增加輸入失敗與重試。
### Recommendation
取得文字與背景實際色值及字級，依適用文字分類量測；若未達門檻，調整 token 後重測。若確認一般文字低於 4.5:1 且無例外，改列 HIGH／Confirmed。
### Reference
[SC 1.4.3 Contrast (Minimum), AA](https://www.w3.org/TR/WCAG22/#contrast-minimum)。目前未證明門檻未達。

未驗證：hit area、鍵盤與 focus、loading／success／error／empty／warning／processing、刪除可逆性。不能因截圖未展示就報告這些功能不存在。
