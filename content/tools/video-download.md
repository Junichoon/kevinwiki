---
title: "社群影片下載方法"
---

# 社群影片下載方法

> 各平台影片怎麼下載：伺服器（Claude）能做的，與手機自己做的。

## 各平台狀況總表

| 平台 | 伺服器 `vdl`（Claude） | 手機自己下載 |
|---|---|---|
| Facebook | ✅ 已設定登入 cookie，受限影片也可 | fdown 等網站 |
| Instagram | ❌ 需 IG 登入 cookie（尚未提供） | iPhone IG 下載捷徑、snapinsta |
| YouTube | ❌ 伺服器被要求「確認不是機器人」 | YouTube 下載捷徑、cobalt |
| Threads | ❌ yt-dlp 不支援 Threads | **iPhone《Threads 下載器》捷徑**（見下方）|
| X / TikTok | 未測試（yt-dlp 有支援） | X 下載捷徑、SaveTik+ |

> YouTube 雖不能下載影片，但 **NotebookLM 可直接讀 YouTube 連結**，分析、做 Podcast 不受影響。

## 伺服器流程（Claude 執行）
- `vdl <網址> ["分類/中文檔名.mp4"]`
  1. yt-dlp 下載最佳畫質（FB 自動帶 cookie）
  2. 若是 AV1 編碼 → ffmpeg 轉 H.264（各裝置都能播）
  3. 上傳 Google Drive `Claude下載/分類/`
- FB 標題常只有「Facebook」→ 擷取畫面判斷內容再命名

## iPhone《Threads 下載器》捷徑
- 捷徑：https://www.icloud.com/shortcuts/daeb495fe0af40d09e33c78b914d337a
- **先裝**：Scriptable、a-Shell mini（不裝會出錯）；iOS 15 以上
- 用法：Threads 貼文 → 紙飛機 → 往左滑「分享到」→「檢視較多」→《Threads 下載器》
- 多張照片/影片可選擇；下載後在「照片」App
- 有更新會提示，可略過；Meta 改版可能失效，需等作者更新
- 下載後若想歸檔：上傳到 Drive `Claude下載`，Claude 可再分類、轉檔、丟 NotebookLM

## 其他工具（蘋果仁文章提到，未實測）
- **cobalt**：網頁版萬用下載器（YouTube / IG / FB / TikTok / X）
- SaveTik+、fdown、y2meta、noTube

## 相關頁面
- [[infra/my-setup]]

## 來源
- raw/2026-11-15_threads-download-shortcut_applealmond.md
- 蘋果仁〈2026 最新《Threads 影片、照片下載捷徑》腳本分享與使用教學〉https://applealmond.com/posts/252201
- raw/2026-11-15_misc-sources.md

<!-- updated: 2026-11-15 -->
