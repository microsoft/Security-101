<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:26:48+00:00",
  "source_file": "AGENTS.md",
  "language_code": "zh"
}
-->
# AGENTS.md

## 项目概述

**Security-101** 是由微软创建的一个面向初学者的网络安全课程。该项目是一个基于文档的学习资源，通过结构化模块教授网络安全的基本概念。它与供应商无关，设计为可以在短时间内完成的小课程（每节课30-60分钟）。

**关键技术：**
- 使用 Markdown 编写内容
- 使用 Docsify 生成静态网站
- 使用 GitHub Pages 托管
- 使用 Co-op Translator 提供多语言支持（50+种语言）
- 使用 GitHub Actions 实现持续集成/持续交付（CI/CD）

**架构：**
- 教育内容分为8个主要模块，每个模块包含子课程
- 使用 Docsify 渲染 Markdown 内容的静态 HTML 网站
- 使用 Azure AI 服务实现自动化翻译工作流
- 核心内容无需构建工具或包管理器

## 仓库结构

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

## 设置命令

这是一个文档项目，无需安装任何依赖项。要处理内容：

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## 开发工作流

### 本地查看内容

该项目使用 Docsify 进行渲染。要预览更改：

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### 内容结构

模块按顺序编号：
- **模块1：** 基本安全概念（1.1-1.7）
- **模块2：** 身份与访问管理（2.1-2.4）
- **模块3：** 网络安全（3.1-3.4）
- **模块4：** 安全运营（4.1-4.4）
- **模块5：** 应用安全（5.1-5.3）
- **模块6：** 基础设施安全（6.1-6.3）
- **模块7：** 数据安全（7.1-7.3）
- **模块8：** AI安全（8.1-8.4）

每个模块以一个测验文件结束（例如，“1.7 模块结束测验.md”）。

### 修改内容

1. 直接编辑根目录中的 Markdown 文件
2. 遵循现有命名约定：`[module].[lesson] [Title].md`
3. 如果添加或删除模块，请更新 README.md 表格
4. 将图片添加到 `/images/` 目录
5. 使用相对路径引用图片：`![描述](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.zh.png)`

## 翻译工作流

**自动翻译：**
- 翻译由 Co-op Translator GitHub Action 自动处理
- 当您将更改推送到 `main` 分支时，工作流会将内容翻译成50多种语言
- 翻译后的文件存储在 `/translations/[language_code]/` 中
- 翻译元数据保存在 YAML 前置数据中

**支持的语言：** 阿拉伯语、孟加拉语、保加利亚语、缅甸语、中文（简体、繁体）、克罗地亚语、捷克语、丹麦语、荷兰语、爱沙尼亚语、芬兰语、法语、德语、希腊语、希伯来语、印地语、匈牙利语、印尼语、意大利语、日语、韩语、立陶宛语、马来语、马拉地语、尼泊尔语、挪威语、波斯语、波兰语、葡萄牙语、旁遮普语、罗马尼亚语、俄语、塞尔维亚语、斯洛伐克语、斯洛文尼亚语、西班牙语、斯瓦希里语、瑞典语、塔加洛语、泰米尔语、泰语、土耳其语、乌克兰语、乌尔都语、越南语等。

**请勿手动编辑翻译文件** - 它们会被自动工作流覆盖。

## 代码风格指南

### Markdown 约定

- 使用标准 Markdown 语法
- 标题：使用 `#` 表示主标题，`##` 表示章节标题，`###` 表示子章节标题
- 列表：使用 `-` 或 `*` 表示无序列表，使用 `1.` 表示有序列表
- 链接：使用描述性文本和完整的 GitHub URL 进行交叉引用
- 图片：存储在 `/images/` 目录中，使用描述性替代文本
- 代码块：使用三引号并添加语言标识符（如果适用）

### 内容指南

- 保持课程内容简洁（30-60分钟阅读时间）
- 使用清晰、适合初学者的语言
- 避免供应商特定工具的说明（课程与供应商无关）
- 在每个模块开始时包含学习目标
- 在适当的地方链接到 Microsoft Learn 的外部资源
- 确保内容具有教育性，而非宣传性

### 文件命名

- 使用格式：`[Module].[Lesson] [Title].md`
- 示例：`1.1 CIA三元组及其他关键概念.md`
- 测验文件：`[Module].[Last] 模块结束测验.md`
- 文件名中使用空格（遵循现有约定）

## GitHub 工作流

### Co-op Translator (co-op-translator.yml)

**触发条件：** 推送到 `main` 分支  
**目的：** 自动翻译新增或修改的 Markdown 文件为50多种语言

**所需环境变量：**
- Azure AI 服务凭据（AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT）
- Azure OpenAI 凭据（可选替代）
- OpenAI 凭据（可选替代）

### 部署 (deploy.yaml)

**触发条件：** 推送到 `main` 分支且 README.md 发生更改  
**目的：** 将静态网站部署到 GitHub Pages  
**输出：** 更新 GitHub Pages 网站

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**触发条件：** 推送到配置的分支  
**目的：** 使用 Jekyll 构建并部署网站

## 拉取请求指南

### 提交前

1. **内容审查：** 确保网络安全概念的准确性和清晰性
2. **格式检查：** 验证 Markdown 格式是否正确渲染
3. **链接测试：** 测试所有内部和外部链接
4. **图片检查：** 确保所有图片加载正常并具有描述性替代文本
5. **一致性：** 遵循现有内容结构和风格

### PR 标题格式

使用描述性标题：
- `新增：[新内容描述]`
- `更新：[模块/课程] - [简要描述]`
- `修复：[问题描述]`
- `文档：[文档更改]`

### 必需检查

- 内容准确性（人工审查）
- Markdown 格式验证
- 链接验证
- 翻译工作流完成（针对 `main` 分支合并）

### 审查流程

1. 至少需要一位维护者审查
2. 重点关注安全概念的技术准确性
3. 验证可访问性和适合初学者
4. 确保保持供应商中立性

## 常见任务

### 添加新课程

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

### 更新现有内容

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### 添加图片

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.zh.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## 测试与验证

### 内容验证

由于这是一个文档项目，测试重点包括：

1. **Markdown 渲染：** 使用 Docsify 本地查看更改
2. **链接验证：** 手动点击所有链接
3. **图片加载：** 验证所有图片是否正确显示
4. **翻译：** 检查文件是否被翻译工作流拾取（自动化）
5. **可访问性：** 确保标题层次结构和替代文本正确

### 本地预览

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### 提交前检查清单

- [ ] Markdown 文件使用正确语法
- [ ] 所有链接有效并尽可能使用 HTTPS
- [ ] 图片具有描述性替代文本
- [ ] 内容适合初学者且准确
- [ ] 保持供应商中立语言
- [ ] 如果添加或删除模块，更新 README.md
- [ ] 文件命名遵循约定

## 安全注意事项

- **内容中不得包含敏感信息：** 切勿提交 API 密钥、密码或敏感数据
- **链接验证：** 确保所有外部链接指向可信来源
- **图片内容：** 验证图片不包含敏感信息
- **翻译工作流：** 使用 Azure AI 服务并正确认证
- **SECURITY.md：** 遵循 SECURITY.md 中的漏洞报告流程

## 其他资源

### 相关微软课程

此课程是微软教育资源集合的一部分：
- 初学者生成式 AI
- 初学者 AI
- 初学者数据科学
- 初学者机器学习
- 初学者 Web 开发
- 初学者物联网

### 外部学习路径

完成 Security-101 后：
- [Microsoft 安全、合规性和身份基础知识](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [考试 SC-900：Microsoft 安全、合规性和身份基础知识](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## 贡献指南

1. **在 GitHub 上 Fork 仓库**
2. **创建一个特性分支** 用于您的更改
3. **进行更改** 遵循上述指南
4. **本地测试** 确保所有内容正确渲染
5. **提交拉取请求** 并清晰描述更改内容
6. **响应维护者反馈**

## 常见问题与故障排除

### 翻译未生效

- 确保更改已推送到 `main` 分支
- 检查 GitHub Actions 标签页中的工作流状态
- 验证翻译工作流的密钥配置
- 翻译是自动完成的，请勿手动编辑翻译文件

### 图片未加载

- 验证图片路径使用正斜杠：`images/filename.png`
- 检查图片文件是否已提交到仓库
- 确保图片文件名完全匹配（区分大小写）
- 使用相对路径，而非绝对 URL

### Docsify 未渲染

- 检查根目录中是否存在 `index.html`
- 验证 Docsify CDN 链接是否可访问
- 确保 Markdown 文件使用标准语法
- 检查浏览器控制台中的 JavaScript 错误

### 链接无效

- 使用完整的 GitHub URL 进行课程间交叉引用
- 格式：`https://github.com/microsoft/Security-101/blob/main/[file].md`
- 在渲染视图中测试链接，而非仅在原始 Markdown 中

## 项目维护

### 定期任务

- 审查并合并社区贡献
- 随着安全领域的发展更新内容以确保准确性
- 监控翻译工作流是否有错误
- 响应问题和讨论
- 保持外部链接的最新状态

### 版本控制

- `main` 分支受保护，需要通过 PR 审查
- 所有更改都需通过拉取请求流程
- 翻译文件是自动生成的，请勿手动编辑
- 使用有意义的提交信息

## AI 编码代理注意事项

- **这是一个文档项目** - 重点关注内容质量，而非代码
- **请勿修改翻译文件** - 它们是自动生成的
- **保持文件命名约定** - 文件名中使用空格，遵循现有模式
- **更新 README.md** 时添加或删除模块以保持表格同步
- **在提交 PR 前进行本地测试** 确保 Markdown 正确渲染
- **遵循现有内容风格** - 保持适合初学者、供应商中立的语气
- **无需构建过程** - 简单的 HTTP 服务器即可满足本地开发需求
- **尊重模块结构** - 每个模块都有一致的编号和组织方式

---

**免责声明**：  
本文档使用AI翻译服务 [Co-op Translator](https://github.com/Azure/co-op-translator) 进行翻译。尽管我们努力确保翻译的准确性，但请注意，自动翻译可能包含错误或不准确之处。原始语言的文档应被视为权威来源。对于关键信息，建议使用专业人工翻译。我们不对因使用此翻译而产生的任何误解或误读承担责任。