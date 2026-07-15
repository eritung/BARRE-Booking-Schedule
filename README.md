# BARRE 出席確認表（Jennifer／2026 年 8–12 月）

這版已綁定以下 Google 試算表：

- Spreadsheet ID：`1bIXGJTm5rqydW_U1cjzgKa3Cmt7jcseAphwcRcvifrM`
- 工作表 gid：`905430503`
- 日期：2026/8/3 之後至 12 月底的每週三（8/5～12/30）
- 成員：Sunny、Jessica、Eri、Irene、Jennifer、Ally

## 為什麼之前存不進去

原始專案只有 `index.html`，沒有真正負責寫入 Google Sheets 的 `apps-script.gs`。只更新 GitHub Pages 前端，不會更新已部署的 Google Apps Script 後端；舊後端也不認得新的日期欄位。

## 必做：更新 Google Apps Script

1. 開啟指定試算表。
2. 點選「擴充功能」→「Apps Script」。
3. 將編輯器內原本程式全部刪除。
4. 貼上本資料夾 `apps-script.gs` 的完整內容並儲存。
5. 在上方函式選單選擇 `initSheet`，按「執行」，第一次需允許授權。
6. 點右上角「部署」→「管理部署作業」。
7. 編輯目前的網路應用程式部署，版本選「新版本」。
8. 確認：
   - 執行身分：我
   - 誰可以存取：所有人
9. 按「部署」。既有 Web App URL 可維持不變。

> 只按 Apps Script 的「儲存」還不夠，必須更新部署版本，線上網頁才會使用新程式。

## GitHub Pages

將 `index.html` 覆蓋 GitHub repository 裡原本的同名檔案即可。

## 後端行為

- 直接開啟指定 Spreadsheet ID 與 gid，不依賴「目前作用中的試算表」。
- 自動新增缺少的 2026/8–12 月週三欄位。
- 自動將 Lark 資料列改為 Jennifer；若兩列同時存在會合併勾選資料。
- 不刪除原本其他日期欄位。
- 每次儲存都會回傳明確錯誤，前端也會顯示後端實際訊息。
