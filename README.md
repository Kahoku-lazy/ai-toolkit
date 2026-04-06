# AI工具包

一个实用的 AI 工具集合项目。

## 项目简介

本项目旨在收集和整理各种实用的 AI 工具和功能。

## 开始使用

```bash
# 克隆项目
git clone https://github.com/Kahoku-lazy/ai-toolkit.git

# 进入目录
cd ai-toolkit
```

## 目录结构

| 目录 | 说明 |
|------|------|
| `Agent/` | 存放子代理设定 |
| `Agent Skills/` | 存放 Skills 技能（按功能分类） |
| `Agent Skills/Anthropics/` | Anthropic 官方 Skills |
| `Agent Skills/文档处理/` | 文档相关 Skills（docx、pptx、pdf 等） |
| `Markdown/` | 存放定向业务、RAG 所需的相关文档 |
| `Notes/` | 存放笔记文件 |

## Agent Skills 功能介绍

本项目集成了 [Anthropics](https://github.com/anthropics) 官方提供的 17 个 Agent Skills，位于 `Agent Skills/Anthropics/skills/` 目录下。

### 📄 文档处理

| Skill | 功能描述 | 使用场景 |
|-------|----------|----------|
| **docx** | 创建、读取、编辑 Word 文档 | 生成报告、备忘录、信函、模板；处理表格目录、页眉页脚；图片插入替换；修订跟踪和批注 |
| **pdf** | PDF 文件的全面操作 | 提取文本/表格、合并拆分、旋转页面、添加水印、创建新 PDF、填写表单、加密解密、OCR 识别 |
| **pptx** | 演示文稿处理 | 创建幻灯片、演讲稿；读取和提取内容；编辑更新现有演示；处理模板、布局、演讲备注 |
| **xlsx** | 电子表格处理 | 创建、读取、编辑 Excel 文件；数据清洗和格式化；图表制作；CSV/TSV 转换 |

### 🎨 设计与视觉

| Skill | 功能描述 | 使用场景 |
|-------|----------|----------|
| **canvas-design** | 创建精美的 PNG/PDF 视觉作品 | 设计海报、艺术品、静态视觉内容；使用内置字体库 |
| **algorithmic-art** | 使用 p5.js 创建算法艺术 | 生成艺术、代码艺术、流场、粒子系统；原创算法艺术创作 |
| **frontend-design** | 创建高质量前端界面 | 构建网页组件、落地页、仪表盘、React 组件；避免通用 AI 审美 |
| **theme-factory** | 为文档和页面应用主题 | 为幻灯片、文档、报告、HTML 页面应用 10 种预设主题或自定义主题 |
| **brand-guidelines** | 应用 Anthropic 品牌规范 | 需要 Anthropic 品牌色彩、字体、视觉风格的文档和作品 |

### 🛠️ 开发与构建

| Skill | 功能描述 | 使用场景 |
|-------|----------|----------|
| **claude-api** | 使用 Claude API 构建应用 | 集成 `anthropic` 或 `@anthropic-ai/sdk`；开发基于 Claude 的应用程序 |
| **mcp-builder** | 创建 MCP (Model Context Protocol) 服务器 | 集成外部 API 或服务；支持 Python (FastMCP) 和 Node/TypeScript (MCP SDK) |
| **web-artifacts-builder** | 创建复杂的多组件 HTML 产物 | 使用 React、Tailwind CSS、shadcn/ui 构建需要状态管理、路由的复杂产物 |
| **webapp-testing** | 测试本地 Web 应用 | 使用 Playwright 验证前端功能、调试 UI、捕获截图、查看浏览器日志 |

### 📝 内容与协作

| Skill | 功能描述 | 使用场景 |
|-------|----------|----------|
| **doc-coauthoring** | 协作文档编写 | 编写技术文档、提案、规范、决策文档；通过迭代完善内容 |
| **internal-comms** | 内部沟通写作 | 撰写状态报告、领导层更新、公司新闻、FAQ、事件报告 |
| **slack-gif-creator** | 创建 Slack 优化 GIF | 为 Slack 制作动画 GIF；提供约束条件和验证工具 |

### 🔧 工具与开发

| Skill | 功能描述 | 使用场景 |
|-------|----------|----------|
| **skill-creator** | 创建和优化 Skill | 从零创建 skill、编辑优化现有 skill、运行评估测试、基准性能分析 |

---

## 本地文档处理 Skills

位于 `Agent Skills/文档处理/` 目录下，用于处理各类文档格式。

| Skill | 功能描述 | 文件类型 | 来源 |
|-------|----------|----------|------|
| **frontend-slides** | 创建动画丰富的 HTML 演示文稿 | HTML/PPT | 社区 |

> 💡 **计划添加**：docx、xlsx、pptx、XMind、pdf 等文档处理技能

## 技能使用说明

### frontend-slides 演示文稿制作

**位置：** `Agent Skills/文档处理/frontend-slides/`

**功能：** 创建零依赖、动画丰富的 HTML 演示文稿，支持 12 种精美预设主题。

**使用方法：**

1. **激活技能** - AI 会自动读取 `Agent Skills/frontend-slides/SKILL.md`
2. **选择模式** - 告诉 AI 你的需求：
   - **新建演示文稿** - 从零创建
   - **转换 PPT** - 将 `.pptx` 文件转换为 HTML
   - **美化现有** - 改进已有的 HTML 演示文稿
3. **提供内容** - 给 AI 你的文本内容、图片或主题
4. **选择样式** - 从 12 种预设主题中选择（或让 AI 推荐）
5. **生成并预览** - AI 生成单文件 HTML，直接在浏览器打开

**12 种预设主题：**

| 主题 | 风格 | 适用场景 |
|------|------|----------|
| **Bold Signal** | 自信大胆，现代高冲击 | 商业提案、产品发布 |
| **Electric Studio** | 简洁专业，高对比 | 技术演讲、数据报告 |
| **Creative Voltage** | 创意活力，复古现代 | 创意展示、设计提案 |
| **Dark Botanical** | 优雅艺术，高端质感 | 艺术展示、高端品牌 |
| **Notebook Tabs** | 编辑组织，优雅触感 | 教程、文档说明 |
| **Pastel Geometry** | 友好现代，平易近人 | 教育、培训材料 |
| **Split Pastel** | 活泼创意，友好 | 创意项目、团队介绍 |
| **Vintage Editorial** | 机智自信，编辑风 | 写作、内容创作 |
| **Neon Cyber** | 未来科技，自信 | 科技产品、开发者内容 |
| **Terminal Green** | 开发者黑客风 | 技术文档、CLI 工具 |
| **Swiss Modern** | 包豪斯精确风 | 设计展示、建筑 |
| **Paper & Ink** | 文学编辑，深思熟虑 | 文学、出版内容 |

**示例命令：**
```bash
# 使用技能创建演示文稿
# 告诉 AI: "使用 frontend-slides 技能，将我的笔记做成 PPT"

# 生成的 HTML 文件可以直接在浏览器打开
start presentation.html
```

**输出特点：**
- 单文件 HTML，无需构建工具
- 响应式设计，适配各种屏幕
- 键盘/触摸/滚轮导航
- 动画效果丰富
- 可部署到 Vercel 或导出为 PDF

## 快速开始

```bash
# 克隆项目
git clone https://github.com/Kahoku-lazy/ai-toolkit.git

# 进入目录
cd ai-toolkit

# Agent Skills 位于
# Agent Skills/Anthropics/skills/<skill-name>/
# Agent Skills/文档处理/<skill-name>/
```

## 贡献

欢迎提交 Issue 和 Pull Request！

## 许可证

MIT License
