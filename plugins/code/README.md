# Code 插件

综合代码辅助工具集，帮助你提升代码质量和开发效率。

## 功能特性

### 🔍 代码审查 (Code Review)

> 来源: https://claudecodecommands.directory/commands/code-review

对代码变更进行全面深入的审查，包括：

- 代码质量分析
- 潜在问题和 bug 检测
- 性能优化建议
- 安全漏洞识别
- 最佳实践建议

**使用方式：**

```bash
/code-review
```

### ✨ 代码简化 (Code Simplifier)

> 来源: https://github.com/anthropics/claude-plugins-official/tree/main/plugins/code-simplifier

在不改变功能的前提下，优化并简化代码以提高清晰度、一致性和可维护性。

**核心原则：**

- 保持功能性：绝不改变代码的作用，只改变实现方式
- 遵循项目标准：严格遵守项目现有的编码规范和最佳实践
- 提升清晰度：减少复杂性，提高可读性
- 保持平衡：避免过度简化导致代码难以理解

**使用方式：**

代码简化器会自动分析最近修改的代码并应用优化，无需手动调用。

## 安装

将此插件添加到你的 Claude Code 配置中：

```bash
claude-code plugin install https://github.com/Fioooooooo/claude-plugins
```

## 未来规划

- 代码格式化
- 代码重构建议
- 依赖分析
- 测试覆盖率分析
- 更多代码质量工具集成

## 作者

**Fio**

## 许可证

MIT
