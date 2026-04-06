# Agent Skills Specification 笔记

> 来源：https://agentskills.io/specification  
> 整理日期：2026年4月6日

---

## 概述

Agent Skills 是一种用于定义 AI 代理技能的规范格式，通过结构化的目录和 `SKILL.md` 文件来描述技能的功能和使用方式。

---

## 目录结构

一个 skill 是一个目录，**必须**包含 `SKILL.md` 文件：

```
skill-name/
├── SKILL.md          # 必需：元数据 + 使用说明
├── scripts/          # 可选：可执行代码
├── references/       # 可选：文档资料
├── assets/           # 可选：模板、资源文件
└── ...               # 其他文件或目录
```

---

## SKILL.md 格式

必须包含 **YAML frontmatter**，后跟 Markdown 内容。

### Frontmatter 字段

| 字段 | 必需 | 说明 | 约束 |
|------|------|------|------|
| `name` | ✅ | 技能名称 | 最多64字符，仅小写字母、数字、连字符 |
| `description` | ✅ | 技能描述 | 最多1024字符，描述功能和使用场景 |
| `license` | ❌ | 许可证 | 许可证名称或文件名 |
| `compatibility` | ❌ | 兼容性 | 最多500字符，环境要求说明 |
| `metadata` | ❌ | 元数据 | 键值映射，用于附加信息 |
| `allowed-tools` | ❌ | 允许的工具 | 空格分隔的工具列表（实验性功能） |

### 最小示例

```yaml
---
name: skill-name
description: A description of what this skill does and when to use it.
---
```

### 完整示例

```yaml
---
name: pdf-processing
description: Extract PDF text, fill forms, merge files. Use when handling PDFs.
license: Apache-2.0
metadata:
  author: example-org
  version: "1.0"
---
```

---

## 字段详细说明

### name 字段规范

- 1-64 个字符
- 仅允许：`a-z`、数字、连字符 `-`
- ❌ 不能以连字符开头或结尾
- ❌ 不能包含连续连字符 `--`
- **必须与父目录名称匹配**

**有效**：`pdf-processing`、`data-analysis`、`code-review`  
**无效**：`PDF-Processing`（大写）、`-pdf`（开头连字符）、`pdf--processing`（连续连字符）

### description 字段规范

- 1-1024 个字符
- 应同时描述：**功能** + **使用时机**
- 包含具体关键词，帮助智能体识别任务

**良好示例**：
```yaml
description: Extracts text and tables from PDF files, fills PDF forms, and merges multiple PDFs. Use when working with PDF documents or when the user mentions PDFs, forms, or document extraction.
```

**不佳示例**：
```yaml
description: Helps with PDFs.
```

### compatibility 字段示例

```yaml
compatibility: Designed for Claude Code (or similar products)
```
```yaml
compatibility: Requires git, docker, jq, and access to the internet
```
```yaml
compatibility: Requires Python 3.14+ and uv
```

---

## 正文内容 (Body Content)

Frontmatter 之后的 Markdown 内容，**无格式限制**。建议包含：

- 分步说明
- 输入和输出示例
- 常见边界情况

💡 **提示**：智能体激活 skill 后会加载整个文件，较长内容可拆分到引用文件中。

---

## 可选目录详解

### `scripts/` - 可执行代码

- 智能体可以运行的脚本
- 应自包含或清楚记录依赖项
- 包含有用的错误消息
- 优雅处理边界情况
- 支持语言：Python、Bash、JavaScript 等（取决于代理实现）

### `references/` - 参考文档

智能体按需阅读的附加文档：

| 文件名 | 用途 |
|--------|------|
| `REFERENCE.md` | 详细技术参考 |
| `FORMS.md` | 表单模板或结构化数据格式 |
| `finance.md` / `legal.md` 等 | 特定领域文件 |

💡 **建议**：保持文件专注，较小的文件意味着更少的上下文使用。

### `assets/` - 静态资源

- **模板**：文档模板、配置模板
- **图片**：图表、示例
- **数据文件**：查找表、模式

---

## 渐进式披露 (Progressive Disclosure)

为了高效利用上下文，按以下层级组织：

| 层级 | 内容 | 触发时机 | 建议大小 |
|------|------|----------|----------|
| 1 | 元数据 (`name`, `description`) | 启动时加载所有 skill | ~100 tokens |
| 2 | 说明 (完整 `SKILL.md`) | 激活 skill 时加载 | < 5000 tokens |
| 3 | 资源 (`scripts/`, `references/`, `assets/`) | 按需加载 | 按需 |

📌 **建议**：主 `SKILL.md` 保持在 500 行以内，详细资料移到单独文件。

---

## 文件引用

引用 skill 内其他文件时，使用**相对于 skill 根目录**的路径：

```markdown
See [the reference guide](references/REFERENCE.md) for details.

Run the extraction script:
scripts/extract.py
```

⚠️ **注意**：保持文件引用相对于 `SKILL.md` 只有一级深度，避免深度嵌套。

---

## 验证工具

使用 `skills-ref` 参考库验证 skill：

```bash
skills-ref validate ./my-skill
```

功能：
- 检查 `SKILL.md` frontmatter 是否有效
- 验证命名约定

---

## 快速参考清单

- [ ] 目录名与 `name` 字段匹配
- [ ] `name` 全小写，使用连字符分隔
- [ ] `description` 描述功能和使用场景
- [ ] `SKILL.md` 控制在 500 行以内
- [ ] 详细内容拆分到 `references/` 或 `scripts/`
- [ ] 文件引用使用相对路径
- [ ] 使用 `skills-ref validate` 验证

---

## 相关链接

- 官方规范：https://agentskills.io/specification
