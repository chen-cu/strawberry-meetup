# 草莓羽球團幫 — 臨打活動更新助理設定

## 專案說明

這是「草莓羽球團幫」羽球臨打活動的報名網站，主要檔案為 `index.html`。

## 宣傳週期說明

- **宣傳以「接下來要推的場次」為單位，不以日曆週為單位**。
- 每次宣傳列出當期所有場次，場次數不固定，可跨日曆週（例如同時推 7/3 與 7/6）。
- 場次卡在 `#info` 區塊內以 `.sessions` 網格並列，一場一卡，數量彈性。

## 工作規則

1. **不要重寫整個網站** — 只做最小必要的修改。
2. **不改版面與文案** — 除非使用者明確要求，否則不動任何樣式、排版或固定文字。
3. **只改活動資料**，包含：
   - 場次數量（`.sessions` 內的場次卡，可增減）
   - 各場日期 / 時間 / 地點 / 球場
   - 程度
   - 費用
   - 報名表單（連結或 Google Form）
   - 用球
   - 報名狀態
   - 小規矩
4. **改前先讀完整 `index.html`**，確認現有結構後再動手。
5. **改後確認**：
   - 檔案非空
   - HTML 結構完整（有開頭 `<!DOCTYPE html>` 與結尾 `</html>`）
6. **確認頁面仍包含**以下關鍵字串：
   - `草莓羽球團幫`
   - `我要報名`
   - `常見問題`
7. **確認無誤才 commit**，不提前 commit。
8. **Commit message 一律使用**：
   ```
   Update meetup event information
   ```

## 報名連結

- 目前表單：`https://forms.gle/vhVKnzUSwd9RN8P76`（含日期複選題，報名者可同時勾選多場）
- 表單連結出現於 Hero 區塊的「我要報名臨打」按鈕，以及 `#signup` 區塊的「我要報名臨打」按鈕。

## 日期同步規則（重要）

場次日期同時出現在以下多個位置，**改日期時必須全部同步**：

| 位置 | 說明 |
|------|------|
| `<title>` | 頁面標題，如 `07/03・07/06 草莓羽球團幫` |
| Hero badge | 頁面最上方的 `<span class='badge'>` |
| `#info` 場次卡 | `.sessions` 內各場次卡的日期欄 |
| `<script>` 倒數計時 `sessions` 陣列 | 底部倒數計時器的場次日期清單（格式：`YYYY-MM-DDTHH:MM:00+08:00`） |

倒數計時腳本會自動切換至下一個尚未開始的場次，無需手動指定最近場次。

## 場次卡結構

`#info` 區塊使用 `.sessions` 網格容納多個場次卡，每張卡格式如下（新增或減少場次時照此格式複製/刪除）：

```html
<div class='card'>
  <div class='session-head'>🗓️ 場次 N</div>
  <div class='info'>
    <div class='item'><div class='label'>📅 日期</div><div class='value'>YYYY/MM/DD（週）</div></div>
    <div class='item'><div class='label'>⏳ 時間</div><div class='value'>HH:MM - HH:MM</div></div>
    <div class='item'><div class='label'>⛩️ 地點</div><div class='value'>地點名稱</div></div>
    <div class='item'><div class='label'>🎯 球場</div><div class='value'>球場號或「待定」</div></div>
  </div>
</div>
```

共用資訊（程度、費用、用球、報名）放在 `.sessions` 之後的 `<div class='card info'>` 中。

## 缺省處理

使用者若未提供某欄位的新值，**保留原值不動**，不要自行填入預設值或清空。
