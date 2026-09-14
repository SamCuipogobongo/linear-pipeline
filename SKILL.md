---
name: linear-pipeline
description: 团队在 Linear 里的工作流 SOP，分 For PM 和 For Executor 两个视角。当任务涉及在 Linear 里建 Issue、规划 Project、处理 Triage、排 Cycle、走评审或发版时使用，确保所有工作按统一的归属、节奏和状态规范执行。Use when working with Linear issues, projects, triage, cycles, milestones, or releases.
---

# Linear Pipeline

## 对象模型（先认清，再决定往哪放）

- **Issue**：个人负责的具体任务，几小时到几天。每张 Issue 必须属于一个 Team；可以不属于任何 Project（进 backlog），但不能没有 Team。Issue 还可以有子 Issue——Project 内部用父 Issue 再做一层轻量分组是正常用法，不用为每个小主题都建 Milestone。
- **Project**：一组 Issue 组成的、有交付期限的成果，可跨 Team。回答「要交付什么」。
- **Initiative**：公司级顶层目标，跨一个到几个季度，罩着多个 Project。回答「为什么做」。
- **Milestone**：Project 内部的阶段切分，通常对应发布节奏，边界是项目。
- **Cycle**：Team 的固定时间盒，装一批预先定好的工作，不绑定发布，边界是团队。
- **Workspace / Team**：全公司共用一个 Workspace，下面切成 Team。Issue、Project、Triage、Cycle、视图全部以 Team 为边界。

## Workspace 地图（按你的团队结构改写）

- **执行团队**：要交付的工作在这里跑 Cycle、走 Triage。可以是一个或多个，按组织架构或协作关系切分。
- **容器区**：放非执行的壳 Project——未成形的想法、workspace 级文档。容器必须是 Project，里面停的是 Document，因为 Document 只能挂在 Project / Initiative 上；未成形的想法不写成 Issue。
- **战略停车场（可选）**：未成形的 initiative 和公司战略，成形后才立项移到执行团队。

## 一件事放哪

- 要交付、需要拆成多张卡的事 → 在执行团队立 Project；够大（跨项目、跨季度）再挂 Initiative。
- 一张卡装得下的散活 → 直接建 Issue，进 Team 的 backlog。
- 还没成形的想法 / 文档 → 不进 backlog，也不写成 Issue；以 Document 形式停在容器区的壳 Project 里，未成形的战略话题放战略停车场。
- 计划外进来的（bug、用户反馈、路线图上没有但必须处理的）→ 一律先进 Triage 等审。
- 计划内的活不过 Triage：直接在 Project 里建 Issue、挂 Milestone、排进 Cycle。

## 硬约束

- Linear 是上下文系统：决策、产品思考和进展沉淀在 Linear，不让别人只能靠私聊才知道你做到哪。项目级结论收进 Project Overview，不散落在 Slack 或本地文档。
- Issue 是承诺不是想法：要写清上下文、要做什么、预期结果、验收标准、依赖；一张卡一个负责人，多人协作用 Sub-issue 和链接表达。
- 产品思考先于执行：用户场景、为什么做、取舍先在产品文档里想清楚，再落成 Project 和 Issue；模糊想法不进 Issue 队列。
- 计划外的工作必须过 Triage，不许直接进团队工作流。
- 状态靠真实事件流转（PR 合并、部署完成），不靠人手动改；被阻塞时在卡里写清卡在哪、影响什么、需要谁。
- 交付要留可读结果：代码、设计、测试结果、文档链接到 Issue 上；自动 Done 只是交付事件，不等于验收通过。
- Agent 可以起草和执行，人负责校验：spec、验收标准、对外发布等关键内容经人核对后才进执行。

## For PM

1. 立 Initiative：在 Workspace → Initiatives 手动建（公司级目标数量少，部分工具链不支持 initiatives），让后面的 Project 都能挂到它下面。
2. 切 Team（按组织架构或经常协作的一群人）；每个 Team 配好自己的任务列表、Project、设置和常用 Issue 模板（如 bug 报告模板）。
3. 立 Project 并养 Project Overview。立项有门槛：问题、目标用户、价值、证据、成功标准先写进产品文档，模糊想法不许直接拆给执行者。Overview 是项目唯一的上下文存放地（Linear 里文档只能建在 Project 和 Initiative 里），按阶段写：
   - 头脑风暴：写目标、数据、可行路径，不用写得太完美；可让 Agent 先分析 backlog 和历史 customer requests 起草初稿，再拉同事进评论和话题评审，边谈边锁定结论。
   - 评审通过后：把定好的列表项直接转成 Issue，加 Milestone 排时间线，按每个人的职能派活；也可让 Agent 从目标日期倒推时间线、按发布阶段建 Milestone。
   - 项目变复杂：某些段落转成独立 Document、外链 Figma 等文件，Overview 保持总入口。
   - 持续更新：新决定和新信息都更新进去，不能过时。验收标准：不了解项目的人只看 Overview 和外链就能完整了解进度，不用查 Issue、不用找人。
4. 审 Triage：先过一遍 Triage Intelligence 的自动建议（它会推荐 team、project、assignee 和相关卡），再对每张卡做四个动作之一——接受（1）、标重复（2）、拒绝（3）、推迟（H）；拿不准的建议悬停看理由再定。接受的卡必须归属明确、信息齐全、可验收，做不到的退回补上下文或推迟。确认要做的把优先级、标签、指派人一次设完，也可以直接把卡派给 coding agent 实现。做完的标志：队列清空，不留暂存垃圾。
5. 在 Cycles 视图排 Cycle，先看 cycle graph（灰线总量、蓝线完成），按团队实际产能排；本周期范围定死后，中途加活要能说出理由，周期结束看灰线涨幅复盘中途塞了多少。
6. 每天先清 inbox；评审去 Reviews tab（guided review 先看核心改动，意见留行内评论）。派给 agent 的活建「assignee 是任意 agent」的视图按状态盯；按 agent 或 team 分组、开 Insights 还能量化产出。
7. 汇报：Project 页发 project update（可设每周提醒、同步 Slack）；数字用 Insights 面板（选指标、切片、分组），攒成 dashboard；项目健康看 progress graph 上灰线和完成线的缺口。
8. 发布：改动进 Release 走 Pipeline（scheduled 计划发版 / continuous 持续部署 / production 面向客户），release notes 可让 Agent 生成；部署完 Issue 自动 Done，最初那条 Slack 话题自动收到更新。

## For Executor

1. 动手前先打开所属 Project 的 Overview 和侧栏 Milestones，确认这张 Issue 属于哪个阶段、对应哪个目标。
2. 建卡分两种情况：计划内的活在 Project 里直接建 Issue（快捷键 C）、挂 Milestone、设负责人和 estimate、排进 Cycle；计划外的从 Slack / Intercom 消息直接建 Issue（bug 建议用 bug 报告模板；还没有的话先让 PM 在 Team 设置里建一个），或落成 customer request 挂到已有 Issue / Project 上，默认进 Triage 等审。
3. 每天先清 inbox（今天到期的、新指派的、评论和 @、项目更新提醒），再看 My Issues，视图只留当前 Cycle 的卡；不急着做的丢 backlog 是正常操作。
4. 上下文都在卡上（附件、关联的 PR、同步的 Slack 话题、评论）。状态不用手动改：起 PR 自动 In Progress，合并自动 Merged，部署自动 Done。不想自己做的，整张卡可以派给 coding agent 实现，你只审它开的 PR；用顺手的 Agent 流程存成自己的 personal skill（存 skill 不限角色）。
5. PR 开好把卡挪到评审状态（建议在 In Progress 和 Done 之间加一个自定义状态，如 Need Review，让「等人看」和「已交付」区分开），在 Reviews tab 等审；收到评论可以直接让 coding agent 改，diff 自动更新，改完确认后合并。
6. 收尾不是点 Done：验收标准逐条满足、产出（代码、PR、测试结果、文档）链接到 Issue、必要 review 完成后再关闭；自动 Done 只是部署事件，不代表验收通过。

## 验收

随便挑一张卡，应该能说出它属于哪个 Project、哪个 Milestone、为什么排进这个 Cycle、现在到哪一步。说不清哪一个，回对应步骤检查。
