---
title: "rclone 連接 Google Drive"
---

# rclone 連接 Google Drive

> 在沒有瀏覽器的伺服器上存取 Google Drive；需自建 OAuth 用戶端 ID。

## 為什麼要自建用戶端 ID
- rclone 內建的共用用戶端 ID **將在 2026 年內停用**
- 自建後連線不受影響，且在 Google 帳號的第三方存取清單中顯示為灰色預設圖示（官方共用版有藍色 rclone 標誌）

## 流程摘要
1. Google Cloud Console 建專案 → 啟用 Google Drive API
2. OAuth 同意畫面：外部、新增三個範圍（`docs`、`drive`、`drive.metadata.readonly`）→ **儲存**
3. 目標對象：加測試使用者 → **發布應用程式**（停在「測試中」會每 7 天失效）
4. 建立「電腦版應用程式」用戶端 → 記下 ID 與密鑰
5. Windows：`rclone authorize "drive" "用戶端ID" "密鑰"` → 瀏覽器登入（「未驗證」警告點進階繼續）
6. 把 token 交給伺服器端設定

## 無瀏覽器伺服器的授權技巧
- 伺服器跑 `rclone authorize "drive" --auth-no-open-browser`，把 Google 登入網址給使用者
- 使用者登入後瀏覽器跳到 `http://127.0.0.1:53682/?state=...&code=...`（顯示無法連線屬正常），把整串網址貼回
- 注意：code 綁定產生它的那次 rclone 工作階段，且很快過期

## 常用指令
- `rclone copy 本地 gdrive:資料夾`
- `rclone moveto gdrive:舊 gdrive:新`（伺服器端搬移）
- `rclone copy x.md gdrive:... --drive-import-formats md --drive-export-formats md` → 上傳並轉成 Google 文件
- `rclone about gdrive:` 查容量

## 撤銷
- Google 帳號 → 安全性 → 第三方存取 → 移除 rclone

## 相關頁面
- [[infra/my-setup]]

## 完整教學
- 📄 [Google 文件：rclone 連接 Google Drive 自建用戶端 ID 教學](https://docs.google.com/document/d/1_H5tueEp3_SJppdce4iALzdK9E-BbS-IEyXyjxH3xxQ/edit)

## 來源
- raw/2026-11-14_rclone-gdrive-own-client-id.md
- https://rclone.org/drive/

<!-- updated: 2026-11-15 -->
