---
description: "学完这个 mini task, 你能看懂 GitHub Codespaces 的 compute 与 storage 两种账单, 会在额度不够时升级或按量付费并给自己设好月度预算上限, 分清 Stop 与 Delete 的适用场景, 并把免费额度和自动删除规则用成几条省钱习惯, 顺带建立起对云服务按需计费模型的通用直觉."
---

# GitHub Codespaces: 费用, 管理与最佳实践

## 1. 概览

前面几个 mini task 你已经学会了创建 Codespace, 修改代码, 提交推送, 创建分支, 用 PR 合并改动. 这些是操作层面的技能. 这篇要补上另一半, 也是很多初学者会忽略的一半: 这东西到底怎么计费, 我该怎么管理它才不会既浪费额度, 又不小心丢代码.

---

## 2. 学习目标

Codespaces 是一种典型的云服务, 它不是你买断的电脑, 而是按需租用的计算资源. 不理解计费逻辑, 你要么会因为不敢用而错过它的方便, 要么会因为用错方式白白浪费免费额度, 甚至在超出额度后收到意外账单. 更重要的是, 这套计费逻辑不是 Codespaces 独有的, 你以后接触 AWS, Azure, Google Cloud 等任何云平台, 都会用到同一套思维方式.

学完这个 mini task, 你将能够:

1. 判断 GitHub 免费账户的 compute 和 storage 额度, 对自己的学习和个人项目来说是否够用
2. 区分 compute 和 storage 两种独立账单, 分别在什么时候触发计费
3. 在额度不够用时选择升级 Pro 或按量付费, 并知道必须先设好月度预算上限才不会收到意外账单
4. 根据场景选择 Stop 还是 Delete, 并养成删除前先确认代码已经 push 的习惯
5. 理解 Codespaces 30 天无操作自动删除的默认行为, 以及它对未推送代码的风险
6. 掌握几条可以立刻落地的省钱习惯, 并把这套思维方式迁移到其他云服务

---

## 3. 前置知识

- 完成过前面的 mini task, 会创建, 修改, 提交并推送 Codespace 里的代码
- 有一个 GitHub 账户, 且至少用过一次 Codespaces

---

## 4. 你将构建或学到什么

这是一篇纯阅读型的 mini task, 你不会在这里写代码或搭建项目, 而是建立一套完整的 Codespaces 计费心智模型: 免费额度有多少, compute 和 storage 分别怎么算钱, Stop 和 Delete 该怎么选, 以及一套能立刻用起来的省钱习惯清单. 读完之后, 你面对自己的 Codespaces 列表, 应该能一眼判断哪些该留, 哪些该关, 哪些该删.

---

## 5. 免费额度: 够用吗

根据 [GitHub 官方计费文档](https://docs.github.com/en/billing/concepts/product-billing/github-codespaces), 个人账户每月赠送的额度如下:

| 账户类型 | compute 额度 (每月) | storage (每月) |
| :--- | :--- | :--- |
| GitHub Free | 120 | 15 GB-month |
| GitHub Pro | 180 | 20 GB-month |

这两个数字在 GitHub 自己的界面上也能查到. 打开 Settings, 进入 Billing and licensing 下面的 Licensing 页面, 就能看到当前账户的套餐和它包含的东西:

![在 Licensing 页面查看当前套餐包含的额度](./img/08-manage-cost-2.png)

注意图里那一行的原文是 120 core-hours, 也就是 120 个核心小时. 这个词很关键, 因为它揭示了一个几乎所有人第一次都会算错的地方: 上面那个 120 不是你能用 120 小时的意思.

每种机器配置都有一个倍率, 倍率等于它的核数. 你实际消耗的额度, 是运行小时数乘以这个倍率. 换句话说, 哪怕是最小的 2-core 机器, 跑一小时也要扣 2 个额度, 而不是 1 个:

| 机器配置 | 倍率 | Free 账户每月实际可用时长 |
| :--- | :--- | :--- |
| 2-core | × 2 | 60 小时 |
| 4-core | × 4 | 30 小时 |
| 8-core | × 8 | 15 小时 |
| 16-core | × 16 | 7.5 小时 |

所以对 Free 账户来说, 真实的答案是: 用最小的 2-core 机器, 每月大约 60 小时; 一旦换成 4-core, 立刻掉到 30 小时.

60 小时对学习和个人项目来说通常是够的: 平均每天用 2 小时, 刚好能撑满一整个月; 或者每周集中用 15 小时, 能撑 4 周. 但如果你随手选了更大的机器, 这份额度会消耗得快得多, 这也是下面那条省钱习惯的由来.

创建 Codespace 时, 默认会直接给你一个标准配置的环境, 但你可以主动选择更低的配置来省额度. 在任意 repository 页面点击绿色的 Code 按钮, 切换到 Codespaces 标签页, 直接点 Create codespace on main 会使用默认配置, 点旁边的 `...` 选择 New with options... 则可以自己挑.

![create-codespace-with-configuration](./img/08-manage-cost-1.png)

New with options... 里有三个值得设置的地方: Branch 决定从哪个分支创建, Region 是服务器区域, 选离自己近的延迟更低, Machine type 是机器配置, 没有特殊需求就选 2-core / 8GB RAM. 对学习和日常开发来说 2-core 完全够用, 只有跑大型构建或机器学习负载时才需要更高配置.

---

## 6. compute 与 storage: 两笔独立的账单

这是很多刚接触云服务的人容易搞混的地方: Codespaces 的费用其实是两件完全独立的事情.

compute 按运行时间收费. Codespace 处于运行状态时才计费, 一旦 Stop 就不再产生 compute 费用. 价格从 2-core 机器每小时 $0.18 起, 和额度倍率一样按核数成倍增加:

| 机器配置 | 每小时价格 |
| :--- | :--- |
| 2-core | $0.18 |
| 4-core | $0.36 |
| 8-core | $0.72 |
| 16-core | $1.44 |
| 32-core | $2.88 |

一句话总结: 开机就计费, 关机就停止计费.

storage 按占用空间收费. 只要 Codespace 还存在, 不管是运行中还是已停止, 都会占用 storage 额度, 只有 Delete 之后才不再计费. 单位是 GB-month, 价格是每 GB 每月 $0.07. 一句话总结: 只要没删, 就一直占着存储额度.

把两者放在一起看会更清楚:

| 状态 | compute 计费 | storage 计费 |
| :--- | :--- | :--- |
| 运行中 | 计费 | 计费 |
| 已 Stop | 不计费 | 计费 |
| 已 Delete | 不计费 | 不计费 |

---

## 7. 额度不够用怎么办: 升级与预算上限

如果你用得比较多, 60 小时可能撑不到月底. 这时候有两条路, 而且它们可以叠加.

一条是升级到 GitHub Pro, 每月 4 美元, 额度从 120 涨到 180 core-hours, 折合 2-core 机器就是从 60 小时涨到 90 小时. 升级入口就在刚才那个 Licensing 页面, 右上角有一个 Upgrade to GitHub Pro 按钮.

另一条是超出免费额度之后按量付费, 也就是前面那张价目表, 2-core 每小时 $0.18. 这条路很方便, 但它藏着这一篇里最需要警惕的一个默认行为.

打开 Settings, 进入 Billing and licensing 下面的 Budgets and alerts 页面, 你会看到 GitHub 把这件事写得很直白:

![Budgets and alerts 页面, 注意说明文字里的 unlimited](./img/08-manage-cost-3.png)

图里那句说明的原文是: 如果没有为某个产品设置 budget, 这个产品的用量就是 unlimited. 换句话说, 默认状态下你是没有刹车的. 一个忘了关的 Codespace 会一直计费, 一个月跑出几十美元并不难, 而你可能要等到账单来了才发现.

这个页面按产品分行, Codespaces, Actions, Packages 各占一条, 互不影响, 所以你要盯的是 Codespaces 那一行. 每行右边会显示这个月已经花了多少, 预算是多少, 以及 Stop usage 这一列是不是 Yes.

要新建一条预算, 点右上角的 New budget; 如果 Codespaces 已经有一条, 从它右侧的 `...` 菜单进去编辑就行. 两条路径打开的是同一个表单:

![设置 Codespaces 的月度预算上限](./img/08-manage-cost-4.png)

表单上有几个地方需要留意:

Product 选 Codespaces, Budget scope 保持 Account, 这样你名下所有仓库的 Codespaces 花费都算在这一条预算里. Budget amount 填一个你能接受的数字, 比如 30. 下面那个 Stop usage when budget limit is reached 一定要勾上, 它才是真正的刹车, 意思是花到这个数就停止提供服务; 不勾的话预算就只是一个观察指标, 拦不住任何东西. 最下面的 Alerts 保持开启, GitHub 会在用量达到 75%, 90% 和 100% 时给你发邮件.

还有一点: 如果页面顶部提示 Payment method is missing, 说明你还没绑定支付方式, 得先添加一张能付美元的信用卡才能保存预算. 这一步看起来有点反直觉, 明明是为了少花钱却要先绑卡, 但逻辑是通的: GitHub 需要先知道往哪收费, 才谈得上给这笔收费设上限.

设完之后你可以在 Billing and licensing 下面的 Usage 页面随时查看本月已经消耗了多少, 离预算还有多远. 建议每周看一眼, 养成习惯之后基本不会再有意外.

---

## 8. Stop 与 Delete: 怎么选

这是管理 Codespaces 最核心的判断.

Stop 相当于把笔记本合上休眠: 硬盘上的所有东西原样保留, 明天打开还能接着做, 不产生 compute 费用, 但 storage 仍在计费. 适合今天的工作告一段落, 但短期内还会回到同一份代码上继续做的情况.

Delete 相当于把这台机器直接扔掉: 里面的一切都不复存在, 下次要重新创建一个全新的 Codespace, compute 和 storage 都不再计费. 适合这个任务已经彻底做完, 短期内不会再用到这个环境的情况.

在点 Delete 之前, 有一件事必须先确认: 代码已经 push 到 GitHub. 记住这个心智模型: push 过的代码活在 GitHub 服务器上, 不管 Codespace 发生什么都安全; 没 push 的代码只存在于这个 Codespace 内部, 一删就没了. 养成这个顺序: 做完工作, commit, push, 再决定是 Stop 还是 Delete.

也不用把 Codespace 当成需要小心翼翼保护的基础设施. 它本质上是可以随时丢弃重建的临时工作区, 只要代码已经 push, 删除旧的, 从同一个 repo 重新创建一个, 它会自动拉取最新代码, 几分钟内就能重新开工.

---

## 9. 自动删除: GitHub 帮你清理

GitHub 会自动删除长期闲置的 Codespace, 不需要你手动操心. 根据 [官方文档](https://docs.github.com/en/codespaces/setting-your-user-preferences/configuring-automatic-deletion-of-your-codespaces), 默认规则是: 一个 Codespace 连续 30 天无操作会被自动删除, 删除前 24 小时会发邮件提醒, 只要重新打开过一次, 计时器就会重置, 保留期限也可以在设置里调整, 范围是 0 到 30 天.

也就是说, 一个 Codespace 放着一个月不管, GitHub 会替你把它清掉, 这其实是件好事, 能自动帮你控制 storage 占用. 唯一的风险在于, 如果里面还留着没有 push 的代码, 这些代码也会一起消失, 这再次说明了 push 习惯的重要性.

---

## 10. 最佳实践: 省钱省心的习惯

把前面几节的知识落成几条日常习惯, 长期坚持下来能省下不少额度:

1. 用完就 Stop: 不用的 Codespace 不要一直挂着运行. 可以在 Codespace 界面左下角点击 Codespaces: xxx, 选择 Stop Current Codespace; 也可以直接关掉浏览器标签页, Codespaces 会在 30 分钟无操作后自动 Stop.
2. 用够用的最小机器: 除非确实需要跑 CPU 密集型任务, 否则一律选 2-core. 前面算过, 换成 4-core 会让可用时长直接减半, 这项习惯长期下来能让免费额度撑得久很多.
3. 早 push, 常 push: 每完成一个阶段的工作就 commit 加 push, 哪怕是实验性的代码, 也先推到一个分支上. 一个可行的工作流是: 新建一个分支 (比如 experiment-xxx), 在这个分支上随意折腾, 每隔一段时间 commit 加 push, 实验成功就开 PR 合并到 main, 失败就直接删掉这个分支.
4. 定期清理不用的 Codespaces: 打开 [github.com/codespaces](https://github.com/codespaces), 看看自己名下都有哪些正在运行或已停止的 Codespaces, 把不再需要的删掉, 不要让闲置环境一直占着 storage 额度.
5. 就算是自己单干, 也用分支加 PR: 独自开发时很容易图省事直接在 main 上改. 更好的习惯是所有改动都在分支上进行, 通过 PR 合并回 main, 让 main 始终保持干净可用的状态. 这样即使某次实验搞砸了, main 依然稳定, 随时可以回退.

---

## 11. 练习

目标: 对着自己真实的 Codespaces 账户做一次巡查和清理, 把上面几节的知识落到自己的账户上.

怎么做:

1. 打开 [github.com/codespaces](https://github.com/codespaces), 浏览完整列表, 记下哪些处于 Running 状态, 哪些是 Stopped.
2. 点开任意一个的 `...` 菜单查看它的 machine type, 看看自己之前用的到底是不是 2-core.
3. 如果有正在运行的 Codespace, 用左下角状态栏菜单或这个管理面板把它 Stop 一次.
4. 找一个确认不再需要的 Codespace, 删除之前先检查一遍 git 状态或 GitHub 上的代码, 确认没有遗漏的改动, 然后把它 Delete 掉.
5. 最后在任意 repo 里用 New with options... 创建一个新的 Codespace, 手动把 Machine type 选成 2-core / 8GB RAM, Region 选离自己近的.

你会观察到: 列表里大概率躺着一些早就用不上却还留着的 Codespaces, 悄悄占用着 storage 额度, 也可能有几个一直停留在创建时的默认机器配置. Stop 之后的 Codespace 仍然出现在列表里, 而 Delete 之后会彻底消失, 这个差别正好对应两种不同的计费状态.

关键洞见: 光是定期看一眼自己有什么, 就足以发现浪费. Stop 和 Delete 不是同一个动作的两种叫法, 选错了要么多花钱, 要么丢代码; 而免费额度是按核数换算的, 用更大的机器本质上就是在成倍地烧这份额度.

---

## 12. 回顾: 我们学到了什么

- 免费额度: Free 账户每月 120 个 compute 额度加 15GB storage, 额度按核数扣, 用 2-core 机器折合大约 60 小时.
- 两种账单: compute 只在运行时计费, storage 只要 Codespace 存在就一直计费.
- 额度不够用: 可以升级 Pro (每月 4 美元, 2-core 折合 90 小时), 也可以按量付费; 但按量付费之前必须先设月度预算上限, 因为不设就是 unlimited, 等于没有刹车.
- Stop 与 Delete: Stop 是暂停, 还占 storage; Delete 是彻底清空, 什么都不再计费; 删除前一定要先 push.
- 自动清理: GitHub 会在 30 天无操作后自动删除 Codespace, 只要代码已经 push 就不必担心.
- 省钱习惯: 用完就 Stop, 用够用的最小机器, 频繁 push, 定期清理, 始终用分支加 PR.

---

## 13. 导师寄语

搞懂 Codespaces 的计费方式, 你其实是在学一件更通用的事情: 按需计费的云服务定价模型是怎么运作的. 老式的模式是买一台电脑, 一次性付钱, 不管用不用都是你的; 按需计费的模式是你租用计算资源, 用多少付多少, 不用就不花钱. 这个转变听起来简单, 但它是理解几乎所有现代云平台账单的起点.

几乎所有云服务都围绕三个维度收费: compute 是 CPU 和内存的使用, 在 Codespaces 里体现为按核数计算的运行时长; storage 是磁盘空间的占用, 体现为 GB-month; network 是数据传输量, Codespaces 目前免费包含. 不同产品可能只对其中一两项收费, 但这个框架在整个行业里是通用的.

所以真正值得带走的不是那几个具体数字, 而是三个问题: 这个服务的计费单位是什么? 什么操作会触发扣费? 哪里是省钱的容易入手点? 把它们当成一份随身携带的检查清单, 以后每接触一个新的云服务就过一遍, 你会发现看懂任何一份陌生的账单都会快很多.

顺便说一句, 这一篇里的具体价格和额度都可能被 GitHub 调整, 偶尔回 [官方计费页面](https://docs.github.com/en/billing/concepts/product-billing/github-codespaces) 确认一次是个好习惯. 而上面那三个问题不会过期.

---

## 14. 速查

**账单速查:** compute 按运行小时数乘以机器核数扣额度 (2-core 起价 $0.18/ 小时), storage 按 GB-month 计费 ($0.07/GB/ 月), Stop 只省 compute, Delete 才两者都省.

**设预算上限:** Settings → Billing and licensing → Budgets and alerts → New budget, Product 选 Codespaces, 填 Budget amount, 务必勾上 Stop usage when budget limit is reached. 不设预算等于不限额.

**关键链接:**

- [GitHub Codespaces 计费说明](https://docs.github.com/en/billing/concepts/product-billing/github-codespaces)
- [配置 Codespaces 自动删除](https://docs.github.com/en/codespaces/setting-your-user-preferences/configuring-automatic-deletion-of-your-codespaces)
- [GitHub 定价页面](https://github.com/pricing)
- [Codespaces 管理面板](https://github.com/codespaces)
