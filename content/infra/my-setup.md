---
title: "我的 AI 工作環境"
---

# 我的 AI 工作環境

> Telegram 對話 → Claude（跑在 Oracle Cloud 容器）→ 下載、NotebookLM、Google Drive、家裡電腦。

## 架構
```
手機 Telegram
   │ (OpenAB)
   ▼
Claude Code（openab-claude Pod，Oracle Cloud，ARM64）
   ├── ~/bin 工具：yt-dlp、ffmpeg、rclone、uv、notebooklm、vdl
   ├── rclone ──────▶ Google Drive「Claude下載」
   ├── notebooklm ──▶ NotebookLM（Gemini Notebook）
   ├── Tavily MCP ──▶ 網路搜尋
   ├── openab-sb ───▶ 家裡 Windows 電腦（Kevin1981Legend）的瀏覽器
   └── ~/wiki ──────▶ 本知識庫
```

## 容器特性
- 架構：**aarch64（ARM64）**，Debian 13
- 使用者 `node`，**沒有 root / sudo / apt**
- **只有 `/home/node` 會保留**（Pod 重建也在）；`/tmp`、系統目錄會清空
- 新工具一律裝到 `~/bin`，要選 ARM64 版本
- `/home/node` 用的是主機開機碟（/dev/sda1），推測為 hostPath 或 local-path PVC：VM 壞掉資料就沒了 → 重要資料要備份到 Drive

## 工具

| 工具 | 用途 | 備註 |
|---|---|---|
| yt-dlp | 下載影片 | FB 自動帶 cookie；IG 需另給 cookie；YouTube 擋伺服器下載 |
| ffmpeg / ffprobe | 轉檔 | 7.0.2 靜態版；FB 常給 AV1，統一轉 H.264 |
| rclone | Google Drive | 使用自建 OAuth 用戶端 ID |
| notebooklm-py | NotebookLM | master token 登入 |
| uv | Python 管理 | Python 也裝在 /home/node |
| `vdl` | 一鍵下載 → 轉檔 → 分類上傳 Drive | `vdl <url> ["分類/檔名.mp4"]` |

## 家裡電腦（OpenAB Switchboard）
- Windows 11，1920×1080，代理程式 sb-win-daemon
- 可用 agent_browser 系列工具操作瀏覽器（獨立設定檔，未必登入各網站）
- 權限：螢幕錄影 ✅、輔助使用 ❌
- 需電腦開機且連上 Switchboard（`vm_status` 檢查）

## 已知限制
- OpenAB Telegram **不能傳檔案給使用者**（官方文件：outbound 尚不支援）→ 檔案改放 Google Drive；可另建 Telegram 機器人用 Bot API 傳（尚未設定）
- 部分 FB / IG 影片需登入才能下載

## Google Drive 分類
`Claude下載/` 底下：健身運動、AI科技（影片、NotebookLM_主題）、財經投資、美食探店、教學文件、Wiki

## 安全
- 主要 Google 帳號、Facebook 帳號的長期憑證存在容器內（使用者知情同意）
- 緊急撤銷：Google「安全性 → 你的裝置」移除陌生 Android 裝置或改密碼；Google「第三方存取」移除 rclone；Facebook「你登入的位置」登出

## 相關頁面
- [[tools/rclone-google-drive]]
- [[tools/video-download]]
- [[ai/notebooklm]]
- [[ai/llm-wiki]]

## 來源
- 對話紀錄（2026-11-13 ～ 11-15）

<!-- updated: 2026-11-15 -->
