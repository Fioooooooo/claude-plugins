---
allowed-tools: Bash(git diff:*), Bash(git log:*)
description: 对代码变更进行全面审查
---

## Context

- 当前 git 状态: !`git status`
- 最近的更改: !`git diff HEAD~1`
- 最近的提交: !`git log --oneline -5`
- 当前分支: !`git branch --show-current`

## 你的任务

进行全面代码审查，重点关注：

1. **代码质量**：检查可读性、可维护性和遵循的最佳实践
2. **安全性**：查找潜在的漏洞或安全问题
3. **性能**：识别潜在的性能瓶颈
4. **测试**：评估测试覆盖率和质量
5. **文档**：检查代码是否已适当文档化

提供具体且可操作的反馈，必要时逐行注释。
