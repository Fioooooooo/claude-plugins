---
allowed-tools: Bash(git add:*), Bash(git status:*), Bash(git commit:*)
description: 基于当前的更改，创建一个 git 提交
---

## Context

- 当前 git 状态: !`git status`
- 当前 git 差异（已暂存和未暂存的更改): !`git diff HEAD`
- 当前分支: !`git branch --show-current`
- 最近的提交: !`git log --oneline -10`

## 你的任务

根据上述更改，创建一个单独的 git 提交。

你可以在一个响应中调用多个工具。使用单条消息进行暂存和创建提交。不要使用其他工具或执行其他操作。除了这些工具调用外，不要发送任何其他文本或消息。
