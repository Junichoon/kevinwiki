---
title: "Blender Agent Skills"
---

# Blender Agent Skills

> 28 個讓 AI 代理（Claude Code 等）操作 Blender 的技能包，涵蓋建模、UV、材質、烘焙、綁骨、動畫、匯出到遊戲引擎、算圖與品質檢查。

## 基本資訊

| 項目 | 內容 |
|---|---|
| GitHub | [EL4CTEO/blender-skills](https://github.com/EL4CTEO/blender-skills) |
| 熱度 | ★1,149、fork 111（2026-11-15）|
| 授權 | MIT |
| 版本 | v1.3.1（2026-11-14）；2026-10-14 才建立，更新很勤 |
| 支援代理 | Claude Code、Codex、OpenCode、Gemini CLI、GitHub Copilot、Cursor |
| 需求 | **Blender 5.2 LTS 以上**，建議 5.3.0 |
| 測試 | 67～69 個在真實 Blender 背景模式跑的測試，CI 同時測 5.2.3 與 5.3.0 |

## 怎麼運作
- 入口技能 `blender-core` 依任務分派給其他技能
- 兩種執行方式：
  - **Live**：裝 Blender MCP 伺服器，AI 直接操作你開著的 Blender
  - **Headless**：沒有 MCP 時，AI 在背景啟動 Blender 跑 Python（bpy）腳本
- 每個腳本回傳 JSON 結果，方便 AI 判斷成功與否

## 28 個技能（依流程分組）

| 階段 | 技能 |
|---|---|
| 入口・場景 | core、scene-setup、workflow-recipes（完整範例流程）|
| 建模 | hardsurface-modeling、sculpting、geometry-nodes、retopology-uv |
| 材質・貼圖 | pbr-materials、texturing（磨損、髒污、貼花）、texture-baking（法線、AO、ORM）|
| 角色 | character-rigging（Rigify）、facial-shapekeys（ARKit 52）、animation（mocap 重定向）、clothing、hair-grooming |
| 場景・氛圍 | environment-kits、lighting-lookdev、time-of-day、weather-fx（雨雪、水坑、閃電）、stylized-npr（卡通描邊）|
| 輸出 | game-optimization（LOD）、export-pipelines（Roblox / Unity / Unreal / Godot / web / USD）、rendering、video-editing |
| 其他 | simulation（剛體、布料、流體）、addon-development、pipeline-automation、asset-qa（交付前檢查）|

## 安裝

**Claude Code（plugin）**
```
/plugin marketplace add EL4CTEO/blender-skills
/plugin install blender-agent-skills@blender-agent-skills
```

**其他代理或手動**
```bash
git clone https://github.com/EL4CTEO/blender-skills
./blender-skills/install/install.sh        # macOS / Linux
.\blender-skills\install\install.ps1       # Windows
```
- 預設裝到 `~/.claude/skills` 與 `~/.agents/skills`
- 選項：`--agent`、`--project DIR`、`--skills a,b`、`--uninstall`

## 範例指令
- 「做一個給 Unreal 用的遊戲道具木箱，要烘焙法線和 LOD」
- 「用 Rigify 綁這個角色，加走路動畫匯出到 Unity」
- 「檢查模型有沒有 z-fighting 和浮空零件，再匯出給 Roblox」
- 「把這條街改成下雨夜晚，加水坑和閃電」
- 「幫角色加上襯衫和髮片，再把 Mixamo 跑步動作套上去」

## 在我的環境能不能用
- ⚠️ **伺服器容器不適合**：ARM64、沒有 GUI、沒裝 Blender
- ✅ **家裡 Windows 電腦較適合**：裝 Blender 5.3 + Claude Code，執行 `install.ps1`；可搭配 [Remote Control](https://code.claude.com/docs/en/remote-control) 用手機遙控
- 快速檢查原始碼：沒看到對外下載或可疑的網路請求；用 subprocess 啟動 Blender（正常行為）

## 相關頁面
- [[ai/multi-agent-workflows]]

## 來源
- raw/2026-11-15_blender-skills_github.md
- https://github.com/EL4CTEO/blender-skills
- 對照頁：https://el4cteo.github.io/blender-skills/comparison/

<!-- updated: 2026-11-15 -->
