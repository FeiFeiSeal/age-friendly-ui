# Mode 4：Frontend code review 示範

教學輸入 `SaveAction.tsx`，完整互動片段（無其他事件代理或等效入口）：

```tsx
export function SaveAction({ onSave }: { onSave: () => void }) {
  return <div className="save" onClick={onSave}>儲存變更</div>;
}
```

### Issue
`SaveAction.tsx:2` 使用只有 click handler 的 div 執行儲存。
### Severity
HIGH — 鍵盤使用者無法啟動主要任務。
### Type
WCAG Requirement
### WCAG finding status
Confirmed violation（僅限本例明示的證據範圍）
### Evidence
Confirmed（所提供完整片段範圍）— 沒有可聚焦元素、鍵盤操作或等效入口。
### Why it matters
難以精準操作滑鼠而改用鍵盤的使用者，無法完成編輯後儲存。
### Recommendation
最小修正為原生 button，保留既有位置與文案：

```tsx
export function SaveAction({ onSave }: { onSave: () => void }) {
  return <button type="button" className="save" onClick={onSave}>儲存變更</button>;
}
```

檢查既有 `.save` 樣式在 button 上的呈現與 focus；用 Tab 抵達、Enter／Space 啟動，確認每次只觸發一次。此例是獨立動作；若既有設計為表單提交，使用 form 的 onSubmit 與 submit button，避免重複綁定。

額外 Age-friendly Recommendation：視情境將實際點擊區調至至少 44 × 44 CSS px，讓成功／失敗結果清楚可讀。這些不屬於 SC 2.1.1 的尺寸或視覺要求，未在本例聲稱已驗證。
### Reference
[SC 2.1.1 Keyboard, A](https://www.w3.org/TR/WCAG22/#keyboard)。儲存功能不涉及依賴移動路徑的例外。

未驗證：全域 CSS 的對比及焦點、API 儲存結果、異步防重複、表單上下文。這段修正不代表整頁通過 WCAG。
