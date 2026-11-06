# AGENTS.md — AI 實戰學習筆記庫 (AI Study Notes Hub) 專案開發規範

> **給 AI 助教 / 開發代理 (Coding Agent) 的核心指令**：
> 在修改本專案或新增任何學習筆記頁面之前，請務必完整閱讀本規範。所有新增與修改都必須 100% 遵守本文件的目錄結構、命名規則、視覺設計與 HTML 模板規範，以確保整個網站的一致性與可維護性。

---

## 1. 專案目的 (Project Purpose)
本專案為「**AI 實戰學習筆記庫 (AI Study Notes Hub)**」，旨在建立一個結構化、模組化且易於擴充的個人知識庫網站。
- **核心目標**：紀錄課堂所學之 AI 工具應用、Vibe Coding 實作心得、Prompt Engineering 技巧與 Agentic AI 開發規範。
- **設計理念**：擺脫「每次重做一個網頁」的方式，透過本 `AGENTS.md` 定義標準化規範，讓 AI 未來只需接收「筆記主題與重點」，即可在數秒內自動產出格式統一的新頁面並更新首頁索引。

---

## 2. 檔案命名與目錄結構 (Directory Structure & Naming Conventions)

```text
ai-study-notes/
├── AGENTS.md                         # AI 開發與擴充規範文件（本檔案）
├── README.md                         # GitHub 專案說明文件
├── index.html                        # 網站首頁（包含專案簡介、統計數據與筆記卡片總覽）
├── style.css                         # 全站共用樣式表（嚴禁在 HTML 內寫大量行內樣式）
└── notes/                            # 存放所有獨立筆記頁面的資料夾
    ├── note-01-vibe-coding.html      # 第 01 篇筆記：Vibe Coding 概念與實戰
    ├── note-02-agents-md.html        # 第 02 篇筆記：AGENTS.md 規則設計與專案管理
    └── note-03-prompt-engineering.html # 第 03 篇筆記：結構化 Prompt 設計技巧
```

### 命名規則：
1. **筆記檔案存放位置**：所有獨立文章頁面必須放在 `notes/` 資料夾下。
2. **筆記檔案命名格式**：一律採用小寫英文與連字號（kebab-case），格式為 `note-XX-topic-slug.html`，其中 `XX` 為兩位數流水號（如 `01`, `02`, `03`, `04`）。
3. **跨頁相對路徑注意**：
   - 在 `index.html` 引用樣式為 `href="style.css"`，連往筆記為 `href="notes/note-XX-xxx.html"`。
   - 在 `notes/*.html` 引用樣式為 `href="../style.css"`，返回首頁為 `href="../index.html"`。

---

## 3. 網頁整體視覺風格 (Visual Style & Design System)
全站採用「**現代深色科技感結合清晰閱讀體驗 (Modern Tech Knowledge Base)**」風格，所有顏色與排版皆定義於 `style.css` 的 CSS 變數中：

- **色彩規範 (Color Palette)**：
  - 背景主色 (`--bg-main`)：`#f8fafc`（淺灰白，確保長文閱讀舒適）
  - 頂部導覽與橫幅深色 (`--bg-dark`)：`#0f172a`（深海藍黑，展現資工科技感）
  - 卡片背景 (`--bg-card`)：`#ffffff`
  - 主強調色 (`--primary`)：`#2563eb`（皇家科技藍）
  - 次強調色 (`--accent`)：`#0ea5e9`（亮青藍）
  - 標籤與重點提示色 (`--badge-bg` / `--badge-text`)：`#dbeafe` / `#1e40af`
- **字體規範**：優先使用 `'Noto Sans TC', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`，程式碼區塊使用 `'JetBrains Mono', Consolas, monospace`。
- **響應式設計 (RWD)**：首頁卡片採用 CSS Grid (`repeat(auto-fill, minmax(300px, 1fr))`)，支援桌面與手機瀏覽。

---

## 4. 頁面結構規範 (Page Structure)

### A. 首頁 (`index.html`) 結構：
1. **頂部導覽列 (`.navbar`)**：顯示網站標題「AI 實戰學習筆記庫」與作者資訊、GitHub 連結。
2. **英雄橫幅區 (`.hero`)**：介紹知識庫目的、目前收錄筆記數量與核心特色。
3. **規則說明橫幅 (`.rule-banner`)**：簡述本站如何透過 `AGENTS.md` 驅動擴充。
4. **筆記卡片列表區 (`.notes-grid`)**：每一篇筆記對應一張 `.note-card`，包含：
   - 編號與分類標籤 (`.note-tag`)
   - 筆記標題 (`<h3>`)
   - 簡短摘要 (`<p>`)
   - 關鍵字標籤群 (`.keywords`)
   - 底部閱讀連結與建立日期 (`.card-footer`)
5. **頁尾 (`.footer`)**：版權宣告與作者資訊（雲科大資工碩一 黃永升）。

### B. 單篇筆記頁 (`notes/note-XX-*.html`) 固定結構：
每一篇筆記頁面**必須**包含以下 5 個標準區塊（不得刪減）：
1. **頂部導覽列 (`.navbar`)**：包含「← 返回筆記總覽 (`../index.html`)」按鈕。
2. **文章標頭區 (`.article-header`)**：顯示筆記編號、分類標籤、主標題 `<h1>`、發布日期與閱讀時間。
3. **本篇核心摘要框 (`.summary-box`)**：用 3 點條列（Bullet points）總結這篇筆記最重要的收穫。
4. **正文內容區 (`.article-content`)**：
   - 必須包含明確的 `<h2>` 小節標題。
   - 必須包含至少一個「實務範例或指令區塊 (`<pre><code>`)」或「重點比較表格 (`<table class="styled-table">`)」。
   - 必須包含一個「AI 實戰小撇步 (`.tip-box`)」區塊。
5. **底部導覽區 (`.article-nav`)**：提供返回首頁以及上一篇/下一篇筆記的快速連結。

---

## 5. AI 新增內容時的標準作業流程 (SOP for Adding New Content)

當使用者對 AI 下達指令（例如：「*請依照 AGENTS.md 幫我新增第 04 篇關於 RAG 檢索增強生成的筆記*」）時，AI 必須嚴格執行以下 3 個步驟：

### 步驟 1：建立新筆記 HTML 檔案
- 在 `notes/` 目錄下建立 `note-XX-topic.html`（編號接續目前最大編號 +1）。
- 套用下方第 6 節的「單篇筆記標準 HTML 模板」，填入完整且具教學價值的內容（不可只填空白佔位符）。

### 步驟 2：同步更新首頁 (`index.html`)
- 在 `index.html` 的 `.notes-grid` 區塊內，**新增一張對應的 `.note-card` 卡片**。
- 更新首頁統計區塊中的「已收錄筆記篇數」數字。

### 步驟 3：更新相鄰筆記的底部導覽（選用但推薦）
- 將前一篇筆記底部的「下一篇」連結指向新建立的 `note-XX-topic.html`。

---

## 6. 標準程式碼模板 (Templates for AI)

### 6.1 首頁新增卡片模板 (`index.html` 內 `.notes-grid` 使用)
```html
<!-- 新增筆記卡片模板 -->
<article class="note-card">
  <div class="card-top">
    <span class="note-number">NOTE #XX</span>
    <span class="note-category">分類名稱</span>
  </div>
  <h3><a href="notes/note-XX-slug.html">筆記主標題</a></h3>
  <p class="card-desc">這裡填寫 40~60 字的筆記核心摘要，說明這篇筆記解決什麼問題或介紹什麼觀念。</p>
  <div class="keywords">
    <span>#關鍵字1</span>
    <span>#關鍵字2</span>
    <span>#關鍵字3</span>
  </div>
  <div class="card-footer">
    <span class="date">📅 YYYY-MM-DD</span>
    <a href="notes/note-XX-slug.html" class="read-more">閱讀筆記 →</a>
  </div>
</article>
```

### 6.2 單篇筆記頁面標準模板 (`notes/note-XX-slug.html` 使用)
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>NOTE #XX：筆記標題 | AI 實戰學習筆記庫</title>
  <link rel="stylesheet" href="../style.css">
</head>
<body>
  <header class="navbar">
    <div class="container nav-container">
      <a href="../index.html" class="brand">🤖 AI 實戰學習筆記庫</a>
      <nav>
        <a href="../index.html" class="nav-link">← 返回筆記總覽</a>
      </nav>
    </div>
  </header>

  <main class="container article-container">
    <div class="article-header">
      <div class="article-meta">
        <span class="note-number">NOTE #XX</span>
        <span class="note-category">分類名稱</span>
        <span class="date">📅 YYYY-MM-DD</span>
      </div>
      <h1>筆記主標題</h1>
      <p class="subtitle">一句話副標題說明本篇核心價值</p>
    </div>

    <section class="summary-box">
      <h2>🎯 本篇核心重點 (Key Takeaways)</h2>
      <ul>
        <li><strong>重點一</strong>：說明文字...</li>
        <li><strong>重點二</strong>：說明文字...</li>
        <li><strong>重點三</strong>：說明文字...</li>
      </ul>
    </section>

    <article class="article-content">
      <h2>1. 核心概念說明</h2>
      <p>段落內容...</p>

      <h2>2. 結構比較或實務範例</h2>
      <pre><code>// 範例 Prompt 或程式碼區塊</code></pre>

      <div class="tip-box">
        <strong>💡 AI 實戰小撇步：</strong>
        <p>提供具體可操作的建議...</p>
      </div>
    </article>

    <div class="article-nav">
      <a href="../index.html" class="btn-secondary">← 回到首頁總覽</a>
    </div>
  </main>

  <footer class="footer">
    <div class="container">
      <p>© 2026 AI 實戰學習筆記庫 | 雲科大資工碩一 黃永升 (M11517041) | 依循 AGENTS.md 規範建置</p>
    </div>
  </footer>
</body>
</html>
```

---

## 7. AI 修改與維護禁止事項 (Constraints & Guardrails)
1. **禁止破壞既有結構**：新增筆記時，不得刪除首頁既有的筆記卡片或修改 `style.css` 的核心變數名稱。
2. **禁止使用外部複雜框架**：專案保持純靜態 HTML5 + CSS3，不引入需編譯的打包工具，確保 GitHub Pages 可直接部署瀏覽。
3. **語言與語氣規範**：全站內容使用繁體中文（台灣習慣用語），專有名詞可保留英文（如 Prompt、Agent、LLM、Repository），語氣應清晰、具條理且適合學習者閱讀。
