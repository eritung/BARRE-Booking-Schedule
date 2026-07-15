# BARRE 出席確認表（可驗證寫入版）

此版本包含前端與 Google Apps Script 後端，指定：

- Spreadsheet ID：`1bIXGJTm5rqydW_U1cjzgKa3Cmt7jcseAphwcRcvifrM`
- 工作表 gid：`905430503`
- 成員：Sunny、Jessica、Eri、Irene、Jennifer、Ally、巧雲、巧雲姐
- 日期：2026/7/27、7/29，以及 2026/8/5～2026/12/30 每週三

## 為什麼你剛傳的版本仍無法確認寫入

你上傳的 ZIP 只有 `index.html` 與 README，缺少 `apps-script.gs`。此外，`index.html` 仍固定使用舊 Web App URL；若你曾建立「新的部署作業」，新部署 URL 不會自動寫回 GitHub 的 HTML。

## 安裝步驟

1. 開啟指定 Google 試算表。
2. 點「擴充功能」→「Apps Script」。
3. 將編輯器中的程式完整替換為本資料夾的 `apps-script.gs`。
4. 儲存，選擇 `initSheet` 後按「執行」，完成授權。
5. 點「部署」→「管理部署作業」。
   - 有原本的 Web App：編輯該部署，版本選「新版本」。
   - 沒有原本部署：建立「網路應用程式」新部署。
6. 執行身分選「我」，存取權限選「所有人」。
7. 複製結尾為 `/exec` 的 Web App URL。
8. 將 `index.html` 放到 GitHub Pages。
9. 打開網頁，在最上方貼上新的 `/exec` URL，按「儲存並測試」。

## 如何判斷真的成功

新版不會只相信後端回傳的 success。按下儲存後，網頁會立刻重新讀取試算表；只有讀回內容與剛送出的日期完全一致，才顯示「已寫入並驗證」。

連線測試也會核對 Spreadsheet ID 與 gid，避免 Web App 寫進另一份試算表。
