# WCAG 2.2：要求與判定界線

本檔是與本 skill 相關的選錄，不是完整合規清單。Normative 依據是 [WCAG 2.2 正式標準](https://www.w3.org/TR/WCAG22/)，核對版本為 2024-12-12 Recommendation，查閱日 2026-10-06。Understanding 文件用於解釋，並不新增要求。以下皆為摘要，判定邊界案例時讀連結中的完整條款、定義和例外。

## 有數值門檻的常見要求

### 1.4.3 Contrast (Minimum) — AA

一般文字至少 4.5:1；large-scale text 至少 3:1。Large text 通常為至少 18pt（24 CSS px），或 14pt 粗體（約 18.67 CSS px）；其他文字系統要考量等效字級定義。**18px 一般內文不是 large text**。Inactive control 內文字、純裝飾、不可見或圖片中附帶文字及 logo 等有例外。

取有效前景／背景色，考慮透明度與背景；不可將 4.49 四捨五入為通過。截圖受縮放、壓縮、抗鋸齒影響，取樣只作估計，不冒充 CSS 測量。
[SC 1.4.3](https://www.w3.org/TR/WCAG22/#contrast-minimum) · [Understanding](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html)

### 1.4.11 Non-text Contrast — AA

辨識元件及其狀態所需的視覺資訊，以及理解內容所需圖形，與相鄰色至少 3:1。Inactive、未經作者修改的瀏覽器原生外觀、圖形不可替代的特定呈現有相關例外。

不是所有 border 都必須 3:1，也不要求所有元件加框。先確認該線條是否為辨識控制項所必需；有其他充分辨識線索時，裝飾邊線不能直接判違規。此條不是要求不同時間的 hover/default 色彼此達 3:1。
[SC 1.4.11](https://www.w3.org/TR/WCAG22/#non-text-contrast) · [Understanding](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html)

### 1.4.4 Resize Text — AA

除字幕與文字圖片外，文字能不依賴輔助科技放大至 200%，且不失去內容或功能。這不是要求預設字級 200%，也不強制網站自建字級切換器。檢查放大後欄位、按鈕文字與錯誤訊息是否被裁切。
[SC 1.4.4](https://www.w3.org/TR/WCAG22/#resize-text) · [Understanding](https://www.w3.org/WAI/WCAG22/Understanding/resize-text.html)

### 1.4.10 Reflow — AA

垂直捲動內容於相當 320 CSS px 寬、水平捲動內容於相當 256 CSS px 高時，不丟失資訊／功能且不需要雙向捲動；必須二維排版才能理解或使用的部分有例外。例外可能適用資料表，不代表整頁都能免除 reflow。1280 CSS px 寬視窗放大到 400% 是常見驗證方式之一。
[SC 1.4.10](https://www.w3.org/TR/WCAG22/#reflow) · [Understanding](https://www.w3.org/WAI/WCAG22/Understanding/reflow.html)

### 2.5.8 Target Size (Minimum) — AA

Pointer target 至少 24 × 24 CSS px，**或符合例外**。小於門檻時，spacing 例外要求：各不足尺寸目標的 bounding box 中心所放直徑 24 CSS px 圓，不與其他 target 或另一不足尺寸目標的圓相交。另有同頁等效控制項、inline／受非目標文字行高限制、未修改的 user-agent control、必要或法律指定呈現等例外。

量實際可啟用區而非 icon 圖像大小；截圖像素不等於 CSS px。不要把 spacing 例外簡化成固定 24px gap，也不要看到 20px icon 就判 HIGH。
[SC 2.5.8](https://www.w3.org/TR/WCAG22/#target-size-minimum) · [Understanding](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html)

### 2.5.5 Target Size (Enhanced) — AAA

44 × 44 CSS px 是此 AAA SC 的門檻，仍有等效、inline、user-agent、essential 例外。在 A／AA review 中「主要操作建議至少 44 × 44」屬 age-friendly recommendation；只有明確檢查 AAA 時才按此 SC 判定。不要將 AAA 不符合稱為 AA violation。
[SC 2.5.5](https://www.w3.org/TR/WCAG22/#target-size-enhanced)

## 非純數值要求：依證據對應條款

以下每個連結均為正式 SC；摘要不是完整適用條件。避免只因採用某個 HTML tag 或缺少某個 ARIA 屬性就直接判違規，要確認可觀察結果。

| SC／等級 | 檢查焦點 |
| --- | --- |
| [1.3.1 Info and Relationships](https://www.w3.org/TR/WCAG22/#info-and-relationships) A | 視覺關聯可由程式判定或有文字說明，如表單 label、分組、表格標頭。 |
| [1.4.1 Use of Color](https://www.w3.org/TR/WCAG22/#use-of-color) A | 不只用顏色表達資訊、動作或區別；例：紅色搭配錯誤文字。 |
| [2.1.1 Keyboard](https://www.w3.org/TR/WCAG22/#keyboard) A | 功能可用鍵盤完成；依移動路徑而非端點的輸入有例外。 |
| [2.4.7 Focus Visible](https://www.w3.org/TR/WCAG22/#focus-visible) AA | 鍵盤操作有可見焦點；不能因截圖未見 focus 就判失敗。 |
| [2.4.11 Focus Not Obscured (Minimum)](https://www.w3.org/TR/WCAG22/#focus-not-obscured-minimum) AA | 鍵盤焦點元件不被作者內容完全遮住；部分遮擋仍可能有 UX 風險。 |
| [3.2.3 Consistent Navigation](https://www.w3.org/TR/WCAG22/#consistent-navigation) AA | 跨頁重複導航相對順序一致，使用者主動改變除外。不是所有 CTA 都強制相同座標。 |
| [3.2.4 Consistent Identification](https://www.w3.org/TR/WCAG22/#consistent-identification) AA | 同組頁面內相同功能元件一致識別。 |
| [3.3.1 Error Identification](https://www.w3.org/TR/WCAG22/#error-identification) A | 自動偵測的輸入錯誤需指出項目並以文字描述。 |
| [3.3.2 Labels or Instructions](https://www.w3.org/TR/WCAG22/#labels-or-instructions) A | 需要使用者輸入時提供標籤或指示。 |
| [3.3.3 Error Suggestion](https://www.w3.org/TR/WCAG22/#error-suggestion) AA | 已知修正方式時提供建議，安全或目的衝突除外。 |
| [4.1.2 Name, Role, Value](https://www.w3.org/TR/WCAG22/#name-role-value) A | 元件名稱、角色與相關狀態可由程式取得，變化可傳達給輔助科技。 |

### 3.3.4 Error Prevention (Legal, Financial, Data) — AA

適用法律承諾、金融交易、修改／刪除儲存的使用者可控資料或提交測驗答案。須提供可逆、檢查並能修正、或完成前檢視／確認／修正機制中至少一種。不是每次儲存都必須確認彈窗；不能僅憑「沒有 modal」判定失敗。
[SC 3.3.4](https://www.w3.org/TR/WCAG22/#error-prevention-legal-financial-data) · [Understanding](https://www.w3.org/WAI/WCAG22/Understanding/error-prevention-legal-financial-data.html)

### 3.3.7 Redundant Entry — A

同一流程已輸入或已提供、又要求輸入的資訊需自動填入或可供選取；必要、安全、原資訊失效有例外。不等於所有跨頁資訊都必須保留，也不要求跨 session 儲存。
[SC 3.3.7](https://www.w3.org/TR/WCAG22/#redundant-entry) · [Understanding](https://www.w3.org/WAI/WCAG22/Understanding/redundant-entry.html)

### 4.1.3 Status Messages — AA

符合 status message 定義的訊息需可由程式判定角色或屬性，使輔助科技無須移動焦點即可呈現。不是所有 toast 都要 assertive，不是每個 loading 都強制跳焦點；視覺回饋是否清楚要另行判斷。
[SC 4.1.3](https://www.w3.org/TR/WCAG22/#status-messages) · [Understanding](https://www.w3.org/WAI/WCAG22/Understanding/status-messages.html)

## 遇到其他情境

拖曳、逾時、登入、文字間距、焦點順序或彈出內容等，查正式 SC 後再引用；本選錄未列出不代表無規範。不能確認適用 SC 時記錄「WCAG 對應待確認」，不要杜撰；有獨立 UX 根據才另列 recommendation。

## 來源與文件聲明

本文件含獨立整理的說明或參考 W3C 資料的摘要，非官方規範或授權翻譯，亦未獲 W3C／WAI 背書。來源、權利歸屬及待確認的授權事項見 [第三方聲明](../THIRD_PARTY_NOTICES.md)。
