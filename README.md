# 🤖 AI 實戰學習筆記庫 (AI Study Notes Hub)

> **雲科大 資工碩一 黃永升 (M11517041)** — AI 課程作業專案：建立自己的 `AGENTS.md` 規則驅動網站

## 📌 專案簡介
本專案是一個專門用來記錄與整理 AI 課程學習心得的「**AI 實戰學習筆記庫**」。
不同於單次性的 Vibe Coding（只求把單一網頁做出來），本專案的核心在於建立了詳盡的 [`AGENTS.md`](./AGENTS.md) 開發規範文件，明確定義了：
1. **專案目錄與檔案命名規則**（所有筆記統一為 `notes/note-XX-slug.html`）
2. **全站統一的視覺設計系統**（共用 `style.css` 深色科技感搭配高可讀性排版）
3. **單篇筆記頁面的 5 大必備結構與標準 HTML 模板**
4. **AI 新增內容時的標準作業流程（SOP）**（建立新筆記頁 + 同步更新首頁卡片與統計數據）

透過這套規則，未來每當有新的課程主題或學習筆記，只需對 AI 下達一句簡短指令，AI 就能依照 [`AGENTS.md`](./AGENTS.md) 自動產出風格與結構 100% 一致的新頁面！

## 📂 專案結構
```text
ai-study-notes/
├── AGENTS.md                           # 核心！給 AI 閱讀的專案開發與擴充規範
├── README.md                           # 專案說明文件
├── index.html                          # 網站首頁（筆記總覽與 AGENTS.md 機制說明）
├── style.css                           # 全站共用樣式表
└── notes/                              # 獨立學習筆記頁面資料夾
    ├── note-01-vibe-coding.html        # NOTE #01：從 Vibe Coding 到規格驅動開發
    ├── note-02-agents-md.html          # NOTE #02：AGENTS.md 與 CLAUDE.md 實戰指南
    └── note-03-prompt-engineering.html # NOTE #03：結構化 Prompt 設計技巧
```
