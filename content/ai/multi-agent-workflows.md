---
title: "多 Agent 開發流程"
---

# 多 Agent 開發流程

> 把寫程式拆給多個分工的 AI 代理，並用「規格、檢查、獨立審查」把關。

## 共同概念
- **角色分工**：協調者、實作者、審查者、驗證者各司其職
- **隔離**：各 Agent 在獨立工作區或獨立對話中執行，避免互相干擾或「自己批改自己」
- **驗證**：獨立的審查角色過濾錯誤與偽陽性
- **成本**：多 Agent 同時跑，token / 用量明顯增加

## 實例比較

| | Google Antigravity Swarm | pi-charter |
|---|---|---|
| 平台 | Google Antigravity | Pi 程式設計代理（pi.dev）|
| 觸發 | `/swarm` 指令 | `/charter` 指令 |
| 規格 | 一句提示詞 | brief.md + spec.md（GIVEN/WHEN/THEN），使用者批准後鎖定 |
| 角色 | Coordinator、Backend、Injection、WebDev、Verifier、Monitor | implementer、auditor、refiner |
| 並行 | 多 Agent 同時 | auditor 可分片並行 |
| 把關 | Verifier 過濾偽陽性 | 程式碼強制：只有使用者能批准、auditor 不能改碼、測試沒過不進審計、refiner 超範圍自動回滾 |
| 成熟度 | Google 正式功能 | v0.1.0，作者自述尚未用真實模型實跑 |

## pi-charter 流程
```
你+AI 起草 brief/spec → 你批准（鎖定）→ implementer 實作
→ 跑 test/lint/typecheck（失敗自動修，有上限）
→ auditor 逐條驗收（可並行，不能改碼）
→ refiner 整理（可選，弄壞就回滾）→ report.md
```

## Claude Code 中的類似做法
- Plan 模式：先規劃，同意後才動手
- Subagent：分別負責實作與審查
- `/code-review`：獨立審查

## 相關頁面
- [[ai/google-antigravity-swarm]]

## 來源
- raw/2026-11-14_antigravity-swarm_notebooklm-report.md
- raw/2026-11-15_misc-sources.md（pi-charter 段落）
- https://github.com/win4r/pi-charter

<!-- updated: 2026-11-15 -->
