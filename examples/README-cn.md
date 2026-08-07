# GitHub Codespaces 入门: 系列索引

这门课教你用 GitHub Codespaces 在浏览器里干活: 不用在自己电脑上装任何东西, 打开网页就有一个配置好的开发环境, 并且在里面完成一个开发者每天都在做的那套动作, 改代码, 提交, 推送, 开分支, 合并.

下面 8 篇 mini task 是按顺序设计的, 分成三块. 第一块解决 "有没有地方干活", 第二块解决 "干完的活怎么留下来", 这是整门课的重头, 第三块解决 "这东西花多少钱, 以及学完往哪走". 建议从 01 顺着读到 08, 每篇先读 README, 再照着 TICKET 自查.

## 1. 有地方干活: 从为什么到怎么用

这一组回答两个问题: 我为什么需要云端开发环境, 以及它长什么样, 怎么开怎么关.

- [01-why-cloud-dev](01-why-cloud-dev/README-cn.md): 讲清这门课的出发点, 为什么科技行业的生态长在 Unix 那一侧, 没有 Mac 的人会在哪里被反复消耗, 以及为什么已经有 Mac 的人同样要学.
- [02-launch-your-first-codespaces](02-launch-your-first-codespaces/README-cn.md): 亲手启动, 使用, 停止, 重启并删除你的第一个 Codespace, 顺便搞懂 stop 和 delete 的区别.
- [03-codespaces-ui](03-codespaces-ui/README-cn.md): 把界面上的 7 个区域一一认全, Activity Bar, Side Bar, Editor, Terminal 各是干什么的, 不再对着一堆按钮发懵.

---

## 2. 让工作留得下来: Git 主线

这一组是整门课的核心. 在 Codespaces 里改了东西不等于保存下来了, 这三篇教你怎么让它真正变成项目历史的一部分, 并且不影响别人.

- [04-commit-and-push](04-commit-and-push/README-cn.md): 走一次完整的 Edit, Stage, Commit, Push 循环, 并搞懂 Git 为什么把 Stage 和 Commit 设计成两步.
- [05-pr-workflow](05-pr-workflow/README-cn.md): 从 `main` 拉一个分支, 改完推上去, 开一个 Pull Request 并把它合并回去, 这是专业团队每天在走的流程.
- [06-branch-basics](06-branch-basics/README-cn.md): 收拾日常用分支时最容易卡住的六个地方, 我在哪个分支, 怎么切, 新分支基于谁, 没提交的改动怎么办, 本地怎么合并, push 和 pull 到底在同步什么.

---

## 3. 用得省, 也知道往哪走

这一组处理两件收尾的事: 别让账单失控, 以及学完之后该在哪干活.

- [07-manage-cost](07-manage-cost/README-cn.md): 看懂 compute 和 storage 两笔账单, 算清免费额度到底是多少小时, 并给自己设一道月度预算上限.
- [08-wrap-up](08-wrap-up/README-cn.md): 把前面七篇串成一条完整的日常循环, 并给出一个判断: 下一个任务该用本地环境还是 Codespaces.

---

## 4. 小结

顺着这三块读下来, 你会得到一个能独立开展工作的最小配置: 有一个随时可用, 搞坏了也不心疼的开发环境; 有一套让工作安全留存并且能和别人协作的流程; 还有对成本的基本掌控, 知道钱花在哪, 以及怎么不花冤枉钱.

这门课全程不需要敲 Git 命令, 但你走的正是真实项目里那套工作流. 概念一旦建立起来, 将来换任何工具, 换到命令行, 都能很快上手.
