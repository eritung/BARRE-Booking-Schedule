# 出席確認表 2026 🗓️

讓 Sunny、Jessica、Eri、Irene、Jennifer、Ally 勾選 2026/8/3 之後至 12 月底，每個週三無法出席的日期。  
資料儲存在 Google Sheets，網頁架設在 GitHub Pages。

> 本版本已加入舊資料相容處理：畫面只會顯示 Jennifer，但仍可讀取並更新原本 Lark 對應的試算表資料列，不必重建既有資料。

---

## 📁 檔案說明

| 檔案 | 說明 |
|------|------|
| `index.html` | 前端網頁，放到 GitHub Pages |
| `apps-script.gs` | Google Apps Script 後端，部署為 Web App |

---

## 🚀 設定步驟

### Step 1 — 建立 Google Sheets

1. 前往 [Google Sheets](https://sheets.google.com)，新建一個試算表
2. 記住這個試算表的 URL（等一下要用）

---

### Step 2 — 設定 Google Apps Script

1. 在剛才的試算表中，點選上方選單 **「擴充功能」→「Apps Script」**
2. 刪除編輯器中預設的程式碼
3. 將 `apps-script.gs` 的全部內容貼入
4. 點選 **「儲存」**（Ctrl+S）
5. 在函式下拉選單選擇 `initSheet`，點選 **「執行」**
   - 第一次執行會要求授權，請允許
   - 這會自動在試算表建立表頭和日期欄位

---

### Step 3 — 部署為網路應用程式

1. 點選右上角 **「部署」→「新增部署作業」**
2. 類型選 **「網路應用程式」**
3. 設定如下：
   - **說明**：任意（例：出席確認表）
   - **執行身分**：`我`（以你的帳號執行）
   - **誰可以存取**：`所有人`（Anyone）
4. 點選 **「部署」**
5. 複製產生的 **網路應用程式 URL**（格式類似 `https://script.google.com/macros/s/AKfy.../exec`）

> ⚠️ 若之後修改了 Apps Script 程式碼，必須重新部署（選「管理部署作業」→「編輯」→升版本）才會生效

---

### Step 4 — 部署到 GitHub Pages

1. 在 GitHub 新建一個 repository（Public）
2. 將 `index.html` 上傳進去
3. 前往 **Settings → Pages**
4. Source 選 **Deploy from a branch**，Branch 選 `main`，資料夾選 `/root`
5. 儲存後等約 1 分鐘，網址會顯示在 Pages 設定頁

---

### Step 5 — 連結 Apps Script URL

1. 開啟你的 GitHub Pages 網址
2. 頁面頂部會出現黃色設定區塊
3. 將 Step 3 複製的 **Apps Script URL** 貼入，點「儲存」
4. 完成！URL 會記在瀏覽器 localStorage 中

> 每位使用者第一次打開網頁都需要輸入一次 URL。  
> 若想避免這步，可以直接把 URL 寫死在 `index.html` 的 `scriptUrl` 變數中：
> ```javascript
> let scriptUrl = 'https://script.google.com/macros/s/YOUR_ID/exec';
> ```

---

## 📋 使用方式

1. 開啟網頁
2. 從下拉選單選擇自己的名字
3. 勾選**無法出席**的週三日期
4. 點選「儲存我的回覆」
5. 下方總覽會顯示所有人的出席狀況

---

## 🗓️ 涵蓋日期（週三）

| 八月 | 九月 | 十月 | 十一月 | 十二月 |
|------|------|------|--------|--------|
| 8/5  | 9/2  | 10/7 | 11/4   | 12/2   |
| 8/12 | 9/9  | 10/14 | 11/11 | 12/9   |
| 8/19 | 9/16 | 10/21 | 11/18 | 12/16  |
| 8/26 | 9/23 | 10/28 | 11/25 | 12/23  |
|      | 9/30 |       |       | 12/30  |
