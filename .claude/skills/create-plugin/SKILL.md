---
name: create-plugin
description: 创建符合 claude-plugins 仓库规范的 Claude Code 插件
allowed-tools: Read, Write, Edit, Bash, Grep, Glob
---

# 创建 Claude Code 插件指南

claude-plugins 仓库是一个集合了多种开发者插件的 claude code plugin marketplace。本指南将引导你如何创建一个符合仓库规范的 Claude Code 插件。

## 插件类型介绍

插件可以有多种形式，每种形式适用于不同的使用场景：

### 1. Commands（命令）

- **用途**：定义可执行的命令，通常用于执行特定的任务或操作
- **特点**：可以指定 allowed-tools 来限制命令可以使用的工具
- **示例**：`git commit`、`git clean-branch`、`code-review`
- **文件格式**：`命令名.md`，包含 YAML frontmatter

### 2. Agents（代理）

- **用途**：定义自主工作的 AI 代理，可以执行复杂的多步骤任务
- **特点**：可以指定 model 来选择使用的 AI 模型（如 opus、sonnet）
- **示例**：`code-simplifier`
- **文件格式**：`代理名.md`，包含 YAML frontmatter

### 3. Skills（技能）

- **用途**：定义复杂的工作流程和指南，通常包含详细的步骤说明
- **特点**：可以包含多个子步骤、示例和最佳实践
- **示例**：`ui-ux`
- **文件格式**：`技能名/SKILL.md`，包含 YAML frontmatter

### 4. Hooks（钩子）

- **用途**：在特定事件发生时自动执行的脚本
- **特点**：可以在工具调用前后执行自定义逻辑
- **状态**：当前仓库暂未使用

### 5. MCP（Model Context Protocol）

- **用途**：扩展 Claude 的能力，连接外部服务和数据源
- **特点**：可以访问外部 API、数据库等
- **状态**：当前仓库暂未使用

### 6. LSP（Language Server Protocol）

- **用途**：提供语言特定的智能提示和分析
- **特点**：可以提供代码补全、诊断等功能
- **状态**：当前仓库暂未使用

## 仓库目录结构

```
claude-plugins/
├── .claude-plugin/
│   └── marketplace.json          # 插件市场元数据（所有插件的注册信息）
├── plugins/
│   ├── code/                     # 代码插件
│   │   ├── .claude-plugin/
│   │   │   └── plugin.json       # 插件元数据
│   │   ├── agents/
│   │   │   └── code-simplifier.md
│   │   ├── commands/
│   │   │   └── code-review.md
│   │   └── README.md
│   ├── git/                      # Git 插件
│   │   ├── .claude-plugin/
│   │   │   └── plugin.json
│   │   ├── commands/
│   │   │   ├── commit.md
│   │   │   └── clean-branch.md
│   │   └── README.md
│   └── design/                   # 设计插件
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── skills/
│       │   └── ui-ux/
│       │       └── SKILL.md
│       └── README.md
└── schema/
    ├── marketplace.schema.json   # marketplace.json 的 JSON Schema
    └── plugin.schema.json        # plugin.json 的 JSON Schema
```

## 创建步骤

当用户需要创建新的 Claude Code 插件时，按以下步骤操作：

### 步骤 1：确定插件类别和类型

1. **询问插件类别**：确定插件属于哪个类别（如 code、git、design 等）
   - 如果是已知类别（code、git、design），则在该类别下创建
   - 如果是新类别，则创建新的类别目录（**目录名称只能是一个单词**）

2. **询问插件类型**：确定要创建的插件类型
   - Commands：执行特定任务的命令
   - Agents：自主工作的 AI 代理
   - Skills：复杂的工作流程和指南
   - 可以同时创建多种类型

3. **收集插件信息**：
   - 插件名称（name）
   - 插件描述（description）
   - 作者信息（author）
   - 版本号（version，默认 1.0.0）
   - 关键词（keywords）
   - 主页链接（homepage）

### 步骤 2：创建插件目录结构

根据插件类型创建相应的目录结构：

```bash
# 创建插件根目录
mkdir -p plugins/<类别名>/.claude-plugin

# 根据类型创建子目录
mkdir -p plugins/<类别名>/commands    # 如果包含 commands
mkdir -p plugins/<类别名>/agents      # 如果包含 agents
mkdir -p plugins/<类别名>/skills      # 如果包含 skills
```

### 步骤 3：创建 plugin.json

在 `plugins/<类别名>/.claude-plugin/plugin.json` 创建插件元数据文件：

```json
{
  "name": "插件名称",
  "description": "插件描述",
  "version": "1.0.0",
  "author": {
    "name": "作者名称",
    "email": "作者邮箱（可选）"
  },
  "homepage": "主页链接",
  "keywords": ["关键词1", "关键词2"],
  "commands": "./commands/", // 如果有 commands
  "agents": "./agents/", // 如果有 agents
  "skills": "./skills/" // 如果有 skills
}
```

**注意**：只包含实际使用的类型字段（commands、agents、skills）。

### 步骤 4：注册到 marketplace.json

在 `.claude-plugin/marketplace.json` 的 `plugins` 数组中添加新插件：

```json
{
  "name": "插件名称",
  "description": "插件描述",
  "version": "1.0.0",
  "author": {
    "name": "作者名称"
  },
  "source": "./plugins/<类别名>",
  "homepage": "主页链接",
  "keywords": ["关键词1", "关键词2"]
}
```

### 步骤 5：创建插件内容文件

根据插件类型创建相应的内容文件：

#### Commands 格式

文件路径：`plugins/<类别名>/commands/<命令名>.md`

```markdown
---
allowed-tools: Bash(git add:*), Bash(git status:*)
description: 命令描述
---

## 你的任务

详细描述命令要执行的任务。
```

#### Agents 格式

文件路径：`plugins/<类别名>/agents/<代理名>.md`

```markdown
---
name: 代理名称
description: 代理描述
model: opus # 可选：opus、sonnet、haiku
---

你是一位专注于...的专家。

你的任务是...

你的工作流程：

1. 步骤1
2. 步骤2
```

#### Skills 格式

文件路径：`plugins/<类别名>/skills/<技能名>/SKILL.md`

```markdown
---
name: 技能名称
description: 技能描述
---

# 技能标题

技能的详细说明和使用指南。

## 使用步骤

1. 步骤1
2. 步骤2

## 示例

提供具体的使用示例。
```

### 步骤 6：创建 README.md

在 `plugins/<类别名>/README.md` 创建插件说明文档：

```markdown
# 插件名称

插件的详细描述。

## 功能

- 功能1
- 功能2

## 使用方法

### Commands

- `/命令名` - 命令描述

### Agents

- `代理名` - 代理描述

### Skills

- `/技能名` - 技能描述

## 示例

提供使用示例。
```

### 步骤 7：验证和测试

1. **验证 JSON 格式**：确保 `plugin.json` 和 `marketplace.json` 格式正确
2. **检查文件路径**：确保所有路径引用正确
3. **测试插件功能**：在 Claude Code 中测试插件是否正常工作

## 最佳实践

### 命名规范

- **类别名**：单个单词，小写，使用连字符分隔（如 `code`、`git`、`design`）
- **命令名**：小写，使用连字符分隔（如 `commit`、`clean-branch`）
- **代理名**：小写，使用连字符分隔（如 `code-simplifier`）
- **技能名**：小写，使用连字符分隔（如 `ui-ux`）

### 描述规范

- **简洁明了**：描述应该简洁但完整地说明插件的功能
- **使用中文**：本仓库使用中文描述
- **突出特点**：强调插件的独特功能和优势

### 版本管理

- **语义化版本**：使用 `major.minor.patch` 格式（如 `1.0.0`）
- **初始版本**：新插件从 `1.0.0` 开始
- **更新规则**：
  - 重大变更：增加 major 版本
  - 新增功能：增加 minor 版本
  - 修复问题：增加 patch 版本

### 文档规范

- **完整的 README**：每个插件都应该有详细的 README.md
- **清晰的示例**：提供实际的使用示例
- **frontmatter 完整**：确保所有必要的元数据都已填写

## 常见问题

### Q: 如何决定创建 command、agent 还是 skill？

- **Command**：适合简单、明确的任务，如执行 git 命令
- **Agent**：适合需要自主决策的复杂任务，如代码优化
- **Skill**：适合需要详细指导的工作流程，如 UI/UX 设计

### Q: 可以在一个插件中混合使用多种类型吗？

可以。例如 `code` 插件同时包含 commands 和 agents。

### Q: 如何更新现有插件？

1. 修改插件内容文件
2. 更新 `plugin.json` 中的版本号
3. 更新 `marketplace.json` 中的版本号
4. 更新 README.md 说明变更内容

### Q: allowed-tools 如何使用？

`allowed-tools` 用于限制命令可以使用的工具。格式：

- `Bash(git add:*)` - 允许执行 `git add` 相关命令
- `Read, Write, Edit` - 允许使用文件操作工具

## 执行流程

当用户请求创建插件时：

1. **收集信息**：通过对话收集所有必要的插件信息
2. **确认类型**：明确插件类型和类别
3. **创建结构**：创建完整的目录结构
4. **生成文件**：创建所有必要的配置和内容文件
5. **注册插件**：更新 marketplace.json
6. **创建文档**：生成 README.md
7. **验证完整性**：检查所有文件是否正确创建
8. **提供指导**：告知用户如何测试和使用新插件
