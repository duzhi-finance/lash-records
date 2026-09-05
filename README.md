# EYELASH · 客戶紀錄管理

給獨立美睫師使用的客戶紀錄管理工具。單一靜態網頁，部署在 GitHub Pages 上即可使用，不需要後端伺服器或資料庫。

## ⚠️ 資料儲存方式（務必閱讀）

這個工具的所有客戶資料（客人狀況、服務紀錄、注意事項等）都只儲存在**你目前使用的這台裝置、這個瀏覽器**的 `localStorage` 裡：

- **換一台電腦或手機**：不會看到原本的資料，因為資料不會自動同步。
- **換一個瀏覽器**（例如從 Chrome 換到 Safari）：也不會看到原本的資料。
- **清除瀏覽器資料／快取／Cookie**，或是重灌瀏覽器、重灌系統：資料會**直接遺失，無法復原**。

網頁上方也會持續顯示這個提醒。

### 建議做法

請**定期使用畫面上方的「⭳ 匯出備份」按鈕**，把所有客戶紀錄匯出成一個 `.json` 備份檔案，存到雲端硬碟（Google Drive、iCloud 等）或其他安全的地方。

- 換裝置、換瀏覽器，或是重灌設備之前，請先匯出備份。
- 需要恢復資料時，用「⭱ 匯入備份」選擇備份檔案即可還原（匯入會覆蓋目前裝置上的所有資料，匯入前請先確認）。

## 部署到 GitHub Pages

專案已經包含 GitHub Actions 工作流程 `.github/workflows/deploy-pages.yml`，會在 push 到 `main` 分支時自動建置並部署到 GitHub Pages。

第一次啟用時，需要在 GitHub 專案設定裡手動開啟一次：

1. 到 repo 的 **Settings → Pages**
2. 在 **Build and deployment → Source** 選擇 **GitHub Actions**
3. 之後每次 push 到 `main` 分支，網站就會自動重新部署

部署完成後，可以在 **Settings → Pages** 頁面上方看到網站網址（通常是 `https://<你的帳號>.github.io/lash-records/`）。

## 銷售頁

`sales.html` 是給獨立美睫師看的產品介紹頁（痛點、功能亮點、價格與購買方式、常見問題），部署後可以在 `https://<你的帳號>.github.io/lash-records/sales.html` 看到。

**上架前務必更新**：頁面裡的價格與 LINE／IG 聯絡連結目前是佔位文字（標示為淺卡其色底），記得換成你自己的實際定價與帳號連結，否則客人點了會連到錯誤的網址。

## 本機開發

這是純前端的靜態網頁，不需要建置流程。本機測試可以直接用瀏覽器打開，或用簡單的靜態伺服器：

```bash
python3 -m http.server 8000
# 然後打開 http://localhost:8000（工具本體）或 http://localhost:8000/sales.html（銷售頁）
```

## 檔案結構

```
.
├── index.html                       # 主要應用程式（含所有 HTML/CSS/JS）
├── sales.html                       # 給美睫師看的產品銷售頁
├── .github/workflows/deploy-pages.yml  # 自動部署到 GitHub Pages 的工作流程
└── README.md
```
