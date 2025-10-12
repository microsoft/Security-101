<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:28:11+00:00",
  "source_file": "AGENTS.md",
  "language_code": "tw"
}
-->
# AGENTS.md

## 專案概述

**Security-101** 是由 Microsoft 創建的入門級網路安全課程。此專案是一個基於文件的學習資源，透過結構化模組教授基本的網路安全概念。它不依賴特定廠商，設計為可在短時間內完成的小課程（每次 30-60 分鐘）。

**主要技術：**
- 使用 Markdown 編寫內容
- Docsify 用於靜態網站生成
- GitHub Pages 用於網站託管
- Co-op Translator 提供多語言支持（超過 50 種語言）
- GitHub Actions 用於 CI/CD

**架構：**
- 教育內容分為 8 個主要模組，每個模組包含子課程
- 使用 Docsify 渲染 Markdown 內容的靜態 HTML 網站
- 使用 Azure AI 服務的自動翻譯工作流程
- 核心內容不需要任何建置工具或套件管理器

## 儲存庫結構

```
/
├── README.md                    # Main entry point with curriculum overview
├── index.html                   # Docsify site entry point
├── [1-8].[1-4] *.md            # Curriculum modules and lessons
├── CODE_OF_CONDUCT.md          # Community guidelines
├── SECURITY.md                 # Security policy
├── SUPPORT.md                  # Support information
├── LICENSE                     # MIT License
├── images/                     # Image assets for lessons
├── translated_images/          # Translated image assets
├── translations/               # Translated versions (50+ languages)
└── .github/
    ├── workflows/
    │   ├── co-op-translator.yml    # Automated translation workflow
    │   ├── deploy.yaml             # GitHub Pages deployment
    │   └── jekyll-gh-pages.yml     # Jekyll site generation
    └── ISSUE_TEMPLATE/             # Issue templates
```

## 設置指令

這是一個文件專案，無需安裝任何依賴項。要處理內容：

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## 開發工作流程

### 本地檢視內容

此專案使用 Docsify 進行渲染。要預覽更改：

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### 內容結構

模組按順序編號：
- **模組 1：** 基本安全概念 (1.1-1.7)
- **模組 2：** 身份與存取管理 (2.1-2.4)
- **模組 3：** 網路安全 (3.1-3.4)
- **模組 4：** 安全運營 (4.1-4.4)
- **模組 5：** 應用程式安全 (5.1-5.3)
- **模組 6：** 基礎設施安全 (6.1-6.3)
- **模組 7：** 資料安全 (7.1-7.3)
- **模組 8：** AI 安全 (8.1-8.4)

每個模組結尾都有一個測驗文件（例如 "1.7 End of module quiz.md"）。

### 修改內容

1. 直接編輯根目錄中的 Markdown 文件
2. 遵循現有命名規則：`[module].[lesson] [Title].md`
3. 如果新增或移除模組，更新 README.md 表格
4. 將圖片添加到 `/images/` 目錄
5. 使用相對路徑引用圖片：`![描述](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.tw.png)`

## 翻譯工作流程

**自動翻譯：**
- 翻譯由 Co-op Translator GitHub Action 自動處理
- 當您將更改推送到 `main` 分支時，工作流程會將內容翻譯成超過 50 種語言
- 翻譯文件存儲在 `/translations/[language_code]/`
- 翻譯元數據保存在 YAML 前置資料中

**支持的語言：** 阿拉伯語、孟加拉語、保加利亞語、緬甸語、中文（簡體、繁體）、克羅埃西亞語、捷克語、丹麥語、荷蘭語、愛沙尼亞語、芬蘭語、法語、德語、希臘語、希伯來語、印地語、匈牙利語、印尼語、意大利語、日語、韓語、立陶宛語、馬來語、馬拉地語、尼泊爾語、挪威語、波斯語、波蘭語、葡萄牙語、旁遮普語、羅馬尼亞語、俄語、塞爾維亞語、斯洛伐克語、斯洛文尼亞語、西班牙語、斯瓦希里語、瑞典語、塔加拉語、泰米爾語、泰語、土耳其語、烏克蘭語、烏爾都語、越南語等。

**請勿手動編輯翻譯文件** - 它們將被自動工作流程覆蓋。

## 程式碼風格指南

### Markdown 規範

- 使用標準 Markdown 語法
- 標題：使用 `#` 作為主標題，`##` 作為章節，`###` 作為子章節
- 列表：使用 `-` 或 `*` 作為無序列表，使用 `1.` 作為有序列表
- 連結：使用描述性文字和完整的 GitHub URL 進行交叉引用
- 圖片：存儲在 `/images/` 目錄，使用描述性替代文字
- 程式碼區塊：使用三個反引號並加上語言標識（如果適用）

### 內容指南

- 保持課程集中且簡潔（30-60 分鐘閱讀時間）
- 使用清晰、適合初學者的語言
- 避免廠商特定工具的指導（課程是廠商中立的）
- 在每個模組開始時包含學習目標
- 適當時鏈接到 Microsoft Learn 的外部資源
- 確保內容具有教育性，而非推廣性

### 文件命名

- 使用格式：`[Module].[Lesson] [Title].md`
- 範例：`1.1 The CIA triad and other key concepts.md`
- 測驗文件：`[Module].[Last] End of module quiz.md`
- 文件名中使用空格（遵循現有規範）

## GitHub 工作流程

### Co-op Translator (co-op-translator.yml)

**觸發條件：** 推送到 `main` 分支  
**目的：** 自動翻譯新增/修改的 Markdown 文件至超過 50 種語言

**所需環境變數：**
- Azure AI 服務憑證（AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT）
- Azure OpenAI 憑證（可選替代方案）
- OpenAI 憑證（可選替代方案）

### 部署 (deploy.yaml)

**觸發條件：** 當 README.md 更改時推送到 `main` 分支  
**目的：** 部署靜態網站到 GitHub Pages  
**輸出：** 更新 GitHub Pages 網站

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**觸發條件：** 推送到配置的分支  
**目的：** 使用 Jekyll 建置並部署網站

## 拉取請求指南

### 提交前

1. **內容審查：** 確保網路安全概念的準確性和清晰性
2. **格式化：** 驗證 Markdown 格式是否正確渲染
3. **連結：** 測試所有內部和外部連結
4. **圖片：** 確保所有圖片加載正常並具有描述性替代文字
5. **一致性：** 遵循現有內容結構和風格

### PR 標題格式

使用描述性標題：
- `新增： [新內容描述]`
- `更新： [模組/課程] - [簡要描述]`
- `修正： [問題描述]`
- `文件： [文件更改]`

### 必要檢查

- 內容準確性（手動審查）
- Markdown 格式驗證
- 連結驗證
- 翻譯工作流程完成（針對 `main` 分支合併）

### 審查流程

1. 至少需要一位維護者審查
2. 重點關注安全概念的技術準確性
3. 驗證可訪問性和適合初學者
4. 確保保持廠商中立性

## 常見任務

### 新增課程

```bash
# 1. Create new Markdown file with proper naming
touch "[Module].[Lesson] [Title].md"

# 2. Add content following template structure
# 3. Update README.md module table with new entry
# 4. Add entry to module overview table
# 5. Ensure quiz file numbering is correct

# 6. Commit changes
git add "[Module].[Lesson] [Title].md" README.md
git commit -m "Add: [Module].[Lesson] - [Title]"
git push
```

### 更新現有內容

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### 添加圖片

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.tw.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## 測試與驗證

### 內容驗證

由於這是一個文件專案，測試重點包括：

1. **Markdown 渲染：** 使用 Docsify 本地檢視更改
2. **連結驗證：** 手動點擊所有連結
3. **圖片加載：** 驗證所有圖片顯示正常
4. **翻譯：** 檢查文件是否被翻譯工作流程拾取（自動化）
5. **可訪問性：** 確保正確的標題層次結構和替代文字

### 本地預覽

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### 提交前檢查清單

- [ ] Markdown 文件使用正確語法
- [ ] 所有連結有效並盡可能使用 HTTPS
- [ ] 圖片具有描述性替代文字
- [ ] 內容適合初學者且準確
- [ ] 保持廠商中立語言
- [ ] 如果新增或移除模組，更新 README.md
- [ ] 文件命名遵循規範

## 安全考量

- **內容中無機密信息：** 切勿提交 API 金鑰、密碼或敏感數據
- **連結驗證：** 確保所有外部連結指向可信來源
- **圖片內容：** 驗證圖片不包含敏感信息
- **翻譯工作流程：** 使用 Azure AI 服務並正確進行身份驗證
- **SECURITY.md：** 遵循 SECURITY.md 中的漏洞報告流程

## 其他資源

### 相關 Microsoft 課程

此課程是 Microsoft 教育資源的一部分：
- 初學者生成式 AI
- 初學者 AI
- 初學者資料科學
- 初學者機器學習
- 初學者網頁開發
- 初學者物聯網

### 外部學習路徑

完成 Security-101 後：
- [Microsoft 安全性、合規性與身份基礎知識](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [考試 SC-900：Microsoft 安全性、合規性與身份基礎知識](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## 貢獻指南

1. **在 GitHub 上 Fork 儲存庫**
2. **為您的更改創建功能分支**
3. **按照上述指南進行更改**
4. **在本地測試**以確保所有內容正確渲染
5. **提交拉取請求**並清楚描述更改
6. **回應維護者的反饋**

## 常見問題與故障排除

### 翻譯無法運作

- 確保更改已推送到 `main` 分支
- 檢查 GitHub Actions 標籤中的工作流程狀態
- 驗證翻譯工作流程的憑證是否已配置
- 翻譯是自動進行的；請勿手動編輯翻譯文件

### 圖片無法加載

- 確認圖片路徑使用正斜線：`images/filename.png`
- 檢查圖片文件是否已提交到儲存庫
- 確保圖片文件名完全匹配（區分大小寫）
- 使用相對路徑，而非絕對 URL

### Docsify 無法渲染

- 確認根目錄中存在 `index.html`
- 驗證 Docsify CDN 連結是否可訪問
- 確保 Markdown 文件使用標準語法
- 檢查瀏覽器控制台中的 JavaScript 錯誤

### 連結無法運作

- 使用完整的 GitHub URL 進行課程間的交叉引用
- 格式：`https://github.com/microsoft/Security-101/blob/main/[file].md`
- 在渲染視圖中測試連結，而非僅在原始 Markdown 中

## 專案維護

### 定期任務

- 審查並合併社群貢獻
- 隨著安全領域的發展更新內容以保持準確性
- 監控翻譯工作流程是否有錯誤
- 回應問題和討論
- 保持外部連結的最新狀態

### 版本控制

- `main` 分支受到保護，需要 PR 審查
- 所有更改都需通過拉取請求流程
- 翻譯文件是自動生成的，請勿手動編輯
- 使用有意義的提交訊息

## 給 AI 編碼代理的注意事項

- **這是一個文件專案** - 重點在於內容品質，而非程式碼
- **請勿修改翻譯文件** - 它們是自動生成的
- **保留文件命名規範** - 文件名中使用空格，遵循現有模式
- **新增或移除模組時更新 README.md** 以保持表格同步
- **在提交 PR 前進行本地測試**以確保 Markdown 正確渲染
- **遵循現有內容風格** - 保持適合初學者且廠商中立的語氣
- **不需要建置流程** - 簡單的 HTTP 伺服器即可滿足本地開發需求
- **尊重模組結構** - 每個模組都有一致的編號和組織方式

---

**免責聲明**：  
本文件已使用 AI 翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 進行翻譯。雖然我們致力於提供準確的翻譯，但請注意，自動翻譯可能包含錯誤或不準確之處。原始文件的母語版本應被視為權威來源。對於關鍵資訊，建議使用專業人工翻譯。我們對因使用此翻譯而產生的任何誤解或錯誤解釋不承擔責任。