---
title: "Google Antigravity Swarm 模式"
---

# Google Antigravity Swarm 模式

> Antigravity 的多 Agent 協同寫程式功能：一個 `/swarm` 指令，讓多個專職 AI 在隔離環境中同時規劃、寫碼、驗證。

## 基本資訊
- 產品：Google Antigravity（Google 的 AI 程式開發環境）
- 觸發方式：`/swarm <需求>`；控制面板：`/swarm board` 或點「Open the swarm UI」
- 核心賣點：取代「單一 AI」或「主 Agent 逐一派工」，多個 Agent **同時**工作且**隔離**，避免程式碼衝突

## 預設 Agent 角色

| 角色 | 職責 |
|---|---|
| **Coordinator** 協調員 | 預設啟動；架構規劃、任務調度，通知 Verifier / Injection / WebDev |
| **Backend** 後端 | 身分驗證、授權、Session、API 端點審查 |
| **Injection** 注入 | SQL 注入、命令注入、程式碼執行向量 |
| **WebDev** 前端 | XSS、資料清理、客戶端儲存、套件依賴漏洞 |
| **Verifier** 驗證員 | 對照原始碼驗證其他 Agent 的發現，過濾偽陽性，產出排序報告；其他 Agent 完成後才啟動 |
| **Monitor** 監控員 | 全程監控進度，防止流程停滯 |

## 模型配置策略
- 高階推理模型（影片舉例 Gemini 4 Carbon）→ 架構、協調、安全審計、驗證
- 快速輕量模型（影片舉例 Gemini 3.8 Flash Medium）→ 一般寫碼
- 代價：多 Agent 同時跑，**用量成本明顯增加**

## Live Board 介面
- 左側：成員、角色、狀態（Working / Waiting）
- 右側：Graph View，顯示 Agent 之間的通知關係
- 可點個別 Sub-agent 查看並**重播**（Replay）其執行過程

## 三種典型用法（提示詞骨架）
1. **全端開發**：`/swarm [應用描述] [技術棧] assign separate agents for front end, backend, database architecture, testing, and security auditing and coordinate their work deliver a fully working application`
2. **大型重構**：`/swarm analyze the entire codebase use parallel agents to investigate the different modules create a refactoring plan and implement the improvements`
3. **安全審計**：`/swarm perform a comprehensive security audit ... generate a prioritized report with reproducible findings do not perform the destructive action`

## 實用建議
- 不要全部用高價模型，依角色分級配置
- 安全審計一定加上 `do not perform the destructive action`
- 保留 Verifier 角色來過濾偽陽性
- 出問題時用 Live Board 的 Replay 除錯

## 已產出的資料
| 產出 | 檔案 |
|---|---|
| 🎧 Podcast（繁中，約 21 分） | [▶ Drive](https://drive.google.com/file/d/1g1IMjcW-NoRYBxJZmUn6HdMcSBtCAuOR/view) |
| 📄 報告 | [Google 文件](https://docs.google.com/document/d/1d2mhZMV2HiQj-SXKggYsXQcpL2t4J2astq9bePSlI40/edit) |
| 🖼️ 資訊圖表 | [Drive](https://drive.google.com/file/d/18q0VDpcBOSzim8piJQrYKdedwLWlc1m6/view) |

- 📁 [Drive 資料夾](https://drive.google.com/drive/folders/10TTCsz0HW32b0hdExloXbwxLHvz_FDlk)
- NotebookLM「AI研究」筆記本也看得到

## 相關頁面
- [[ai/multi-agent-workflows]]
- [[ai/notebooklm]]

## 來源
- raw/2026-11-14_antigravity-swarm_notebooklm-report.md
- YouTube「Google Antigravity Just Got Swarm Mode (One Prompt, Multiple AI Agents)」https://www.youtube.com/watch?v=zrN7DHDuWts

<!-- updated: 2026-11-15 -->
