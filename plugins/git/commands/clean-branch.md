---
description: 清理所有远程已删除但本地仍存在的分支
---

## 你的任务

你需要执行以下 bash 命令来清理从远程仓库中删除但仍在本地存在的分支。

## 要执行的命令

1. **首先，列出分支以识别任何带有 [gone] 状态的分支**
   执行此命令：

   ```bash
   git branch -v
   ```

   注意：带有 '+' 前缀的分支有相关的暂存目录，在删除前必须先移除暂存目录。

2. **接下来，识别需要移除的 [gone] 分支的暂存目录**
   执行此命令：

   ```bash
   git worktree list
   ```

3. **最后，移除暂存目录并删除 [gone] 分支（处理常规和暂存分支）**
   执行此命令：
   ```bash
   # 处理所有 [gone] 分支，移除 '+' 前缀
   git branch -v | grep '\[gone\]' | sed 's/^[+* ]//' | awk '{print $1}' | while read branch; do
     echo "处理分支: $branch"
     # 查找并移除存在的暂存目录
     worktree=$(git worktree list | grep "\\[$branch\\]" | awk '{print $1}')
     if [ ! -z "$worktree" ] && [ "$worktree" != "$(git rev-parse --show-toplevel)" ]; then
       echo "  移除暂存目录: $worktree"
       git worktree remove --force "$worktree"
     fi
     # 删除分支
     echo "  删除分支: $branch"
     git branch -D "$branch"
   done
   ```

## 预期行为

执行这些命令后，您将：

- 查看所有本地分支及其状态的列表
- 识别并移除与 [gone] 分支相关的暂存目录
- 删除所有标记为 [gone] 的分支
- 提供已移除的暂存目录和分支的反馈信息

如果没有任何分支被标记为 [gone]，则报告无需进行清理。
