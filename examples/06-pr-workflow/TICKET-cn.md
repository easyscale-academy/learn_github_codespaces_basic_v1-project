---
description: "完成一次从新建分支到修改, 提交, push, 再到 Pull Request (PR) 合并的完整流程, 并能提交一个已经成功合并的 PR 链接."
---

# 创建分支并完成一次 Pull Request 合并

## 1. 目标

在你自己的一个 GitHub repository 里, 从零走一遍 create branch, edit, commit, push, 到 Pull Request (PR) merge 的完整流程. 这是任何真实项目日常协作都会用到的最基本工作流, 完成这个练习之后, 你就具备了独立提交改动并让改动进入主分支的能力.

---

## 2. 要做的事情

1. 打开一个你自己拥有的 repository, 启动 Codespace, 确认左下角状态栏显示的是 `main`.
2. 点击状态栏的分支名, 选择 Create new branch from..., 基础分支选 `main`, 新分支命名为 `practice-branch-你的名字` (例如 `practice-branch-john`).
3. 确认底部状态栏显示的分支名称已经切换成新分支.
4. 对 `README.md` 或其他任意文件做一个小修改, 比如加一行文字, 然后保存.
5. 依次完成 stage 和 commit, 写一条清楚的 commit 消息.
6. 点击 Sync Changes 把分支推送到 GitHub, 如果提示需要发布分支就点击确认.
7. 打开 GitHub 网站, 为这个分支创建一个 Pull Request, 目标合并到 `main`.
8. 检查 PR 里的改动无误后, 点击 Merge pull request 完成合并.
9. 合并后点击 Delete branch 删掉这个分支, 再回到 Codespace 切换到 `main` 并同步一次.
10. 把合并后的 Pull Request 链接发给导师确认.

开始之前请确保工作区是干净的, 也就是没有改了还没提交的文件, 这样切换分支不会被打断; 切换分支时遇到未提交改动该怎么办, 下一个 mini task 会专门讲. 如果 GitHub 上没有自动弹出创建 PR 的提示, 手动进入 Pull requests 标签页, 点击 New pull request 并选择你的分支即可.

**预计用时:** 15 到 30 分钟

---

## 3. 检查清单

- [ ] **创建分支时指定了基础分支**: 用 Create new branch from... 明确基于 `main` 创建, 而不是随手用了默认选项.
- [ ] **推送新分支**: 知道新分支需要 push 才会出现在 GitHub 上, 并完成了一次成功推送.
- [ ] **完成完整闭环**: 独立走完 create branch, edit, commit, push, PR merge 的完整流程, 中间没有卡住.
- [ ] **合并后做了收尾**: 删掉了用完的分支, 并把本地的 `main` 同步到了合并之后的最新状态.
- [ ] **准备好可验收的链接**: 手上有一个已经显示为已合并状态的 PR 链接, 可以直接打开验证.
