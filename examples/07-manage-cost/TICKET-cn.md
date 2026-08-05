---
description: "巡查一遍自己名下真实的 Codespaces, 能准确说出免费额度是否够用, compute 与 storage 分别怎么计费, Stop 与 Delete 该怎么选, 才算这个 mini task 完成."
---

# GitHub Codespaces 费用, 管理与最佳实践

## 1. 目标

Codespaces 是按需计费的云资源, 不搞清楚计费规则, 很容易要么因为担心花钱而不敢放手用, 要么因为用错方式白白浪费免费额度. 这个 mini task 要求你在读完对应的 README 之后, 回到自己真实的 GitHub 账户, 亲手巡查一遍手上的 Codespaces, 练习 Stop 与 Delete 的取舍, 并用最省钱的机器配置创建一个新的 Codespace, 把学到的计费心智模型落到实际操作上.

---

## 2. 要做的事情

1. 完整读一遍对应的 README, 搞清楚免费额度, compute 与 storage 两种账单, Stop 与 Delete 的区别, 以及 30 天自动删除规则.
2. 打开自己的 Codespaces 管理面板, 数一数目前有多少个 Codespaces, 分别记录哪些在运行, 哪些已停止.
3. 点开至少一个 Codespace 的机器配置, 确认它用的是不是最低的 2-core 配置.
4. 如果手上有正在运行的 Codespace, 用状态栏菜单或管理面板把它 Stop 一次.
5. 确认某个 Codespace 的代码已经全部 push 到 GitHub 之后, 把它 Delete 掉, 完成一次清理.
6. 在任意 repo 里用 New with options 创建一个新的 Codespace, 手动选择 2-core 机器和离自己近的 region.
7. 用自己的话把下面四个问题的答案写下来, 准备好讲给导师或同学听: 清理前后 Codespaces 数量各是多少; 之前的 Codespaces 用的是什么机器配置, 有没有比 2-core 更大的; Stop 和 Delete 的区别用自己的话怎么说; 为什么删除前必须先 push.

**预计用时:** 15 到 20 分钟

---

## 3. 检查清单

- [ ] **读完教程**: 完整读完对应的 README, 理解免费额度, compute 与 storage 两种账单, Stop 与 Delete 的区别, 以及自动删除规则.
- [ ] **算清免费额度**: 能说出 Free 账户每月是 120 个 compute 额度加 15GB storage, 且知道额度按机器核数扣, 用 2-core 折合下来只有大约 60 小时.
- [ ] **分清两种账单**: 能解释清楚 compute 只在运行时计费, storage 只要 Codespace 存在就一直计费.
- [ ] **巡查过自己的 Codespaces**: 打开管理面板, 数清楚自己名下 Codespaces 的数量与状态, 并检查过至少一个的机器配置.
- [ ] **练过 Stop**: 用状态栏菜单或管理面板成功 Stop 过一个 Codespace.
- [ ] **练过 Delete**: 在确认代码已 push 之后, 成功 Delete 过一个不再需要的 Codespace.
- [ ] **会用最小机器创建**: 用 New with options 手动创建过一个 2-core 机器的 Codespace.
- [ ] **理解 Stop 与 Delete 的区别**: 能用自己的话讲清楚 Stop 是暂停但仍占存储, Delete 是彻底清空且删除前必须先 push.
- [ ] **理解自动删除规则**: 知道 Codespace 连续 30 天无操作会被自动删除, 且明白这对未推送代码的风险.
- [ ] **养成省钱习惯**: 能说出至少三条最佳实践, 比如用完就 Stop, 用最小机器, 早 push 常 push, 定期清理.
