---
title: "NotebookLM（現名 Gemini Notebook）"
---

# NotebookLM（現名 Gemini Notebook）

> Google 的「只根據你給的資料回答」AI 筆記本；可產生 Podcast、報告、資訊圖表、心智圖等。

## 重要事實
- **2026-07-16 更名為 Gemini Notebook**，產品與舊連結不變
- **沒有官方 MCP 伺服器**；google/mcp 有人提需求，尚無回應
- **官方 API 只有企業版**（Gemini Notebook Enterprise，Google Cloud 授權）；免費版與 Google AI Pro 都不能用
- 社群工具靠模擬瀏覽器或未公開的內部 API，Google 改版可能失效

## 社群工具

| 工具 | 類型 | 原理 |
|---|---|---|
| **notebooklm-py**（teng-lin）| Python CLI + MCP + Claude skill | 內部 API；支援 master-token 無頭登入 ← **本環境使用中** |
| PleasePrompto/notebooklm-skill | Claude skill | 開 Chrome 模擬操作 |
| roomi-fields/notebooklm-mcp | MCP + REST API | 瀏覽器 + 內部 RPC |

## 本環境用法（notebooklm-py v0.8.6）
- 登入方式：master token（伺服器可自動續期 cookie，不必定期重登）
- 常用指令：
  - `notebooklm list`／`create "名稱"`
  - `notebooklm source add -n <ID> <URL>` → `source wait`
  - `notebooklm generate audio|report|infographic|mind-map ... --language zh_Hant`
  - `notebooklm download audio|report|infographic ...`
  - `notebooklm ask -n <ID> -s <來源ID> "問題" --save-as-note`
- **不支援**：Canvas（NotebookLM 有此功能，但工具尚未實作）
- 產出的 Podcast 是只有聲音的 .mp4，可無損轉 .m4a

## 筆記本
- **AI研究**（b37fdf4c…）：Antigravity Swarm、10 個免費 AI 模型

## 注意
- AI 產出可能前後不一致（例：同一影片的模型型號兩次答案不同），重要資訊要對照原始來源

## 相關頁面
- [[ai/google-antigravity-swarm]]
- [[ai/free-open-source-ai-models]]
- [[infra/my-setup]]

## 來源
- raw/2026-11-15_misc-sources.md

<!-- updated: 2026-11-15 -->
