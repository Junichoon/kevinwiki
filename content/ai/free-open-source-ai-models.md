---
title: "10 個免費開源 AI 模型（Hugging Face 熱門）"
---

# 10 個免費開源 AI 模型（Hugging Face 熱門）

> 全部免費、可離線、一般電腦不需顯示卡（GPT-OSS-20B 需 16GB RAM）。依 Hugging Face 按讚數排名，#1 最高。

## 依用途分類

| 用途 | 排名 | 模型 | 開發者 | 參數量 | 重點 | 限制 |
|---|---|---|---|---|---|---|
| 文字轉語音 | #1 | **Kokoro-82M** | — | 82M | 英文發音接近真人、多音色、可做有聲書；Apache 授權可商用 | 中文音色少、不能複製人聲 |
| 圖像/影片分割 | #2 | **SAM 3**（亦提 SAM 2） | Meta | ~8 億 | 打字描述就能圈出、追蹤物件，去背換背景 | 提示詞只支援英文；需申請下載；無顯卡處理影片慢 |
| 離線聊天 | #3 | **GPT-OSS-20B** | OpenAI | 20B | 離線版 ChatGPT，回答前會推理，可調推理強度；Ollama / LM Studio | **需 16GB RAM**；只能處理文字 |
| 說話者分離 | #4 | **pyannote.audio Community-1** | — | — | 標出錄音中每段是誰說的，搭配 Whisper 做會議記錄 | 需到 Hugging Face 同意條款；需基礎 Python |
| 語音轉文字 | #5 | **Whisper Large V3 Turbo** | OpenAI | — | 轉逐字稿快、準，自動辨識語言或翻成英文 | 中文常輸出簡體 |
| 文件 OCR | #6 | **GLM 文件模型** ⚠️ | 智譜 AI | ~9 億 | 掃描檔轉文字/表格、抽取指定欄位、辨識公式印章、8 種語言；可用 Ollama | 不能聊天 |
| 文字搜圖 | #7 | **CLIP** | OpenAI | ~4 億 | 用一句話從幾千張照片中找圖；Immich 等相簿的底層技術 | 原生只支援英文；需搭配相簿軟體 |
| 多模態助理 | #8 | **Gemma 系列** ⚠️ | Google | — | 聊天、寫作、看圖、聽聲音；Ollama 一行安裝 | 知識量受體積限制 |
| 視覺問答 | #9 | **Moondream 2**（預覽版 3） | — | 2B | 看圖回答、寫描述、框選並計數物件；Apache 2.0 | 中文較弱 |
| 翻譯 | #10 | **HYMT-2 1.8B** | 騰訊混元 | 1.8B | 33 種語言（含繁中）離線互譯，可指定專有名詞與語氣；壓縮版約 440MB 手機可跑 | 需 LM Studio 等工具 |

## ⚠️ 尚未確認的型號
NotebookLM 兩次輸出說法不同，需看影片畫面確認：
- Google 模型：「Gemma 4 14B」vs「Gemma 2 9B/14B」
- 智譜模型：「GLM-OCR / GLM-4V」vs「GLM-Edge-v2」

## 常用搭配工具
- **Ollama**：一行指令下載/執行模型（Gemma、GPT-OSS、GLM）
- **LM Studio**：圖形介面跑模型（HYMT、GPT-OSS）
- 組合技：Whisper（轉文字）+ pyannote（分人）= 分人分段的會議記錄

## 已產出的資料
- NotebookLM「AI研究」筆記本：筆記「免費開源模型」、互動心智圖、文字心智圖
- 🧠 心智圖：[Google 文件](https://docs.google.com/document/d/1NbONtHOEaMj1NIIqObXdt_WAWHq0k-bZq3IG6Lj1tG4/edit)
- 📁 [Drive 資料夾](https://drive.google.com/drive/folders/1wsFivijgU5YJdRKZgdDW5o6wLKo7W-Dg)

## 相關頁面
- [[ai/notebooklm]]

## 來源
- raw/2026-11-15_free-ai-models_notebooklm-note.md
- raw/2026-11-15_free-ai-models_mindmap.txt
- YouTube 辰星說Github《10 個必裝 AI 工具，完全免費！離線版 ChatGPT｜打字找照片｜錄音轉逐字稿｜不用顯卡｜Hugging Face 熱門模型》https://www.youtube.com/watch?v=DECRFD8965Q

<!-- updated: 2026-11-15 -->
