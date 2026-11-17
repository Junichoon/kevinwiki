---
title: "LLM Wiki（Karpathy 知識庫做法）"
---

# LLM Wiki（Karpathy 知識庫做法）

> 不用 RAG 每次重找資料，而是讓 AI 持續維護一份互相連結的 Markdown 百科。本 Wiki 就是用這個做法建的。

## 起源
- Andrej Karpathy 於 **2026 年 4 月**發表的 GitHub gist「LLM Wiki」
- 是一種做法（pattern），不是特定軟體

## 三層結構
1. **Raw sources 原始資料**：文章、論文、逐字稿；AI 只讀不改，是事實依據
2. **Wiki 本體**：AI 撰寫的 Markdown 頁面（摘要、人物、概念、比較），彼此連結；另有 `index.md`（目錄）與 `log.md`（時間軸）
3. **Schema 規則檔**：`CLAUDE.md` / `AGENTS.md`，規定怎麼整理、回答、維護

## 三個動作
- **Ingest**：加入新資料 → 更新相關頁面
- **Query**：從 Wiki 回答，好答案存回成新頁面
- **Lint**：找矛盾、過時資訊、孤兒頁面

## 規模
- Karpathy：只靠 `index.md` 目錄，約可撐 **~100 份資料、幾百頁**；更大時需要搜尋索引

## 架設方式比較

| 方式 | 說明 | 優點 | 缺點 |
|---|---|---|---|
| A. 純做法 | git + Markdown + AI 代理（如 Claude Code）| 最簡單、完全掌控、git 有版本紀錄 | 沒有現成網頁介面 |
| B. llmwiki 軟體 | 開源（★1.8k, Apache-2.0）；本機 SQLite 或自架 Postgres+S3；內建 MCP | 有網頁介面與搜尋 | 本機模式只聽 127.0.0.1；需 Python 3.11+ / Node 20+ |
| C. Obsidian + 同步 | VPS 放 Wiki，Syncthing / LiveSync 同步到各裝置 | 手機電腦都用 Obsidian 編輯 | 要多裝同步服務 |
| 託管服務 | Hjarni、llmwiki.app | 不用維護 | 資料不在自己手上 |

## 本環境的實作（方式 A）
- 位置：容器 `~/wiki/`（git 管理，`/home/node` 會保留）
- 同步：`./sync.sh` → git commit + 上傳 Google Drive `Claude下載/Wiki/`
- 操作入口：Telegram（OpenAB）對 Claude 下指令
- 參考案例：有人用 Hetzner VPS（2 核 4GB）+ Hermes Agent + Telegram 做出同樣架構

## 相關頁面
- [[infra/my-setup]]
- [[ai/notebooklm]]

## 來源
- raw/2026-11-15_llm-wiki_web-research.md

<!-- updated: 2026-11-15 -->
