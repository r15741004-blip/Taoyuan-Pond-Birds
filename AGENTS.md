# AGENTS.md - 桃園埤塘野鳥生態圖鑑與調查資料庫 (Taoyuan Pond Birds Wiki)

## 1. 專案目標與定位 (Project Purpose)
- **專案名稱**：桃園埤塘野鳥生態圖鑑與調查資料庫
- **核心目標**：將桃園台地（千塘鄉）之歷史發展、蘆竹鄉 2-18 號埤塘與沙崙村埤塘等真實野鳥調查數據結構化，建立一個兼具生態保育推廣與知識庫功能之靜態 Wiki 網站。
- **整體風格**：自然生態風（翡翠綠 `emerald-600` 主色 / 深石灰 `slate-900` 背景）、現代簡潔、響應式設計 (Responsive Web Design, RWD)。

## 2. 專案目錄結構規範 (Directory Standard)
所有新增與修改的檔案必須嚴格遵守以下目錄結構：

```text
Taoyuan-Pond-Birds/
├── AGENTS.md                 # AI 協作指南與開發規範檔
├── index.html                # 網站首頁（埤塘背景與調查專題目錄）
├── pages/                    # 所有專題與鳥類介紹頁面均放置於此
│   ├── migratory-birds.html  # 冬候鳥調查專題頁面 (收錄鳳頭潛鴨與抽水現象)
│   └── resident-birds.html   # 留鳥與棲地變遷專題頁面 (收錄鷺科與微棲地分析)
└── assets/                   # 靜態圖片、圖示與媒體資源
```

## 3. 技術棧與外部依賴 (Tech Stack & Dependencies)
- **UI 框架**：Tailwind CSS (透過 CDN 引入: `https://cdn.tailwindcss.com`)
- **圖示庫**：Lucide Icons (`https://unpkg.com/lucide@latest`)
- **開發限制**：
  - 僅使用原生 HTML5 + Tailwind CSS + Vanilla JS。
  - 嚴禁引入 npm 套件、Build Tools (如 Vite、Webpack) 或前端框架 (如 React、Vue)，確保程式碼免編譯即可直接於瀏覽器運行並託管於 GitHub Pages。

## 4. UI/UX 視覺與設計系統 (Design System)
- **色調規範 (Color Palette)**：
  - **品牌主色**：翡翠綠 `emerald-600` (`#059669`) / 點綴亮綠 `emerald-400`
  - **背景色**：深色模式 `slate-900` (`#0f172a`)
  - **卡片背景**：`bg-slate-800/50` 搭配 `backdrop-blur-md` 與 `border border-slate-700`
  - **文字顏色**：主標題 `text-white` / 次要標題 `text-emerald-400` / 內文 `text-slate-300` / 數據註解 `text-slate-400`
- **卡片樣式 (Card Component Standard)**：
  - 外框：`border border-slate-700` 搭配圓角 `rounded-xl`
  - 懸浮效果 (Hover)：`hover:border-emerald-500 hover:bg-slate-800 transition duration-300`
- **導覽列規範 (Navigation)**：
  - 全局標題與頁尾需保持一致風格。
  - 所有子頁面 (`pages/*.html`) 頂部必須包含返回首頁按鈕，連結統一寫為 `../index.html`。

## 5. AI 新增與擴充頁面之 SOP 流程 (Content Generation SOP)
當使用者要求 AI **「新增一個鳥類介紹或調查專題頁面」** 時，AI **必須嚴格執行**以下步驟：

### 步驟 A：建立子頁面 (`pages/`)
1. 檔名採用英文小寫與橫線命名 (kebab-case)，如 `pages/black-faced-spoonbill.html`。
2. `<title>` 標籤格式統一為：`[主題名稱] | 桃園埤塘野鳥生態網`。
3. 頁面必須包含四個核心區塊：
   - 頂部導覽列（含返回首頁按鈕 `../index.html`）
   - Hero 主題標題與簡介區
   - 生態特徵與棲地描述卡片
   - 觀測數據/調查統計表格或數據卡片
4. 所有圖示必須正確調用 Lucide Icons 並在頁尾執行 `lucide.createIcons();`。

### 步驟 B：自動更新首頁目錄 (`index.html`)
1. 在 `index.html` 的 `#catalog-grid` 容器內，新增對應新頁面的導向卡片。
2. 卡片需包含圖示、主題名稱、簡短描述，並正確連結至 `./pages/[檔名].html`。

## 6. AI 協作約束條件 (Constraints)
- **禁止破壞全站一致性**：不得隨意更改核心配色方案或替換 CSS 框架。
- **路徑準確性**：首頁資源連結使用 `./`，子頁面資源與返回連結使用 `../`。
- **資料真實性**：新增鳥類調查數據時，應優先採用真實野外實察數據（如蘆竹 2-18 號埤塘之 29 科 67 種紀錄）。