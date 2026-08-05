---
description: "完成一次从新建分支到修改, 提交, push, 再到 Pull Request (PR) 合并的完整流程, 并能提交一个已经成功合并的 PR 链接."
---

# 创建分支并完成一次 Pull Request 合并

## 1. 目标

在你自己的一个 GitHub repository 里, 从零走一遍 create branch, edit, commit, push, 到 Pull Request (PR) merge 的完整流程. 这是任何真实项目日常协作都会用到的最基本工作流, 完成这个练习之后, 你就具备了独立提交改动并让改动进入主分支的能力.

---

## 2. 要做的事情

1. 打开一个你自己拥有的 repository, 启动 Codespace
2. 用 **Create new branch from...** 基于 `main` 创建一个新分支, 命名为 `practice-branch-你的名字` (例如 `practice-branch-john`)
3. 确认底部状态栏显示的分支名称已经切换成新分支
4. 对 `README.md` (或其他任意文件) 做一个小修改, 比如加一行文字
5. 依次完成 stage, commit (写一条清楚的 commit 消息), 再 push 到 GitHub, 如果提示需要发布分支就点击确认
6. 打开 GitHub 网站, 为这个分支创建一个 Pull Request, 目标合并到 `main`
7. 检查 PR 里的改动无误后, 点击 **Merge pull request** 完成合并
8. 把合并后的 Pull Request 链接发给导师确认

如果切换分支时提示有未提交的改动, 先完成 commit, 或者在源代码管理面板里右键选择 **Discard Changes** 丢弃改动, 再重新创建分支; 如果 GitHub 上没有自动弹出创建 PR 的提示, 手动进入 **Pull requests** 标签页, 点击 **New pull request** 并选择你的分支即可.

**预计用时:** 15 到 20 分钟

---

## 3. 检查清单

- [ ] **切换和创建分支**: 能在底部状态栏用 **Create new branch from...** 创建并切换到新分支
- [ ] **处理未提交的改动**: 理解并能在切换分支前正确处理未提交的改动 (commit, stash 或丢弃)
- [ ] **推送新分支**: 知道新分支需要 push 才会出现在 GitHub 上, 并完成了一次成功推送
- [ ] **完成完整闭环**: 独立走完 create branch, edit, commit, push, PR merge 的完整流程, 并能提交一个已合并的 PR 链接
