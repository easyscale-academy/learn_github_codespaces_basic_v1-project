---
description: "通过亲手启动, 操作, 停止, 重启并删除一个 GitHub Codespace, 证明你已经理解云端开发环境的价值, 并掌握 stop 与 delete 的区别."
---

# 启动你的第一个 GitHub Codespace

## 1. 目标

本任务要求你在浏览器里亲手走完一次完整的 codespace 生命周期: 启动, 在终端执行命令验证环境, 停止, 重启确认数据保留, 最后删除. 目的是让你真正体会到云端开发环境如何让你绕开本地配置环境的麻烦, 并建立起对 stop (停止) 和 delete (删除) 两种操作差异的直觉, 而不是只停留在概念层面.

---

## 2. 要做的事情

1. 通读教程正文, 理解什么是云端开发环境, GitHub Codespaces 的基本概念, 每月免费额度规则, 以及 stop 和 delete 的区别
2. 打开任意一个 GitHub 仓库页面, 通过 **Code** 按钮的 **Codespaces** 标签创建一个新的 codespace, 等待它启动完成
3. 在终端里依次执行 `echo "Hello World"`, 确认输出正确
4. 创建一个 `message.txt` 文件, 写入一行文字, 内容为 `This is a message`
5. 用 `cat` 命令验证 `message.txt` 的内容和你写入的一致
6. 停止这个 codespace (通过左下角状态菜单, 或访问 github.com/codespaces), 确认它进入 Stopped 状态
7. 重新打开这个 codespace, 用 `cat ~/message.txt` 验证文件内容依然保留
8. 彻底删除这个 codespace, 确认它从列表中消失
9. 用自己的话说清楚 stop 和 delete 分别对数据和额度有什么影响, 各自适用什么场景

**预计用时:** 15 到 20 分钟

---

## 3. 检查清单

- [ ] **理解云端开发环境**: 能说清云端开发环境和本地开发环境的区别, 以及它为什么能帮初学者绕开配置环境的坑
- [ ] **了解 codespaces 基础和免费额度**: 说清 GitHub Codespaces 的基本概念, 每月 60 小时免费额度和 30 分钟自动停止规则
- [ ] **完成启动到删除的完整流程**: 亲手启动, 在终端里执行命令验证环境, 停止, 重启, 最后删除一个 codespace
- [ ] **区分 stop 和 delete**: 能准确说明停止和删除 codespace 分别对数据和额度有什么影响, 以及各自适合什么场景
