# linear-pipeline

一个给 AI Agent 用的 Linear 工作流 SOP skill。

A [skill](https://agentskills.io) (`SKILL.md`) that encodes a team's Linear operating procedure — object model, placement rules, hard constraints, and role-based workflows — so agents can execute the process instead of every teammate learning the whole Linear Method by hand.

## 它解决什么问题

教每个同事学会 Linear Method 的成本很高。与其教，不如把团队的 SOP 写成一个 skill，让每个人的 Agent 按同一套规范执行：什么东西放哪、Issue 怎么才算合格、计划外的活怎么走 Triage、Cycle 怎么排、怎么验收。

## 结构

`SKILL.md` 分七层：

1. **触发条件**（frontmatter `description`）：涉及 Issue / Project / Triage / Cycle / Milestone / Release 时加载
2. **对象模型**：Issue / Project / Initiative / Milestone / Cycle / Team 的定义与边界
3. **Workspace 地图**：把「你的 workspace 长什么样」写进 skill（示例结构，按团队实际改写）
4. **一件事放哪**：放置决策表——要交付的立 Project、散活进 backlog、未成形的想法进 Document 容器、计划外走 Triage
5. **硬约束**：不可违反的原则——Issue 是承诺不是想法、产品思考先于执行、状态事件驱动、交付留可读结果、Agent 起草人校验
6. **For PM / For Executor**：双角色操作流程，每步带质量门槛或完成标志
7. **验收**：一句话自检——随便挑一张卡，能说出它属于哪个 Project、哪个 Milestone、为什么在这个 Cycle

## 核心设计取舍

- **Issue 是承诺，不是想法**。没成形的想法不进 Issue 队列，以 Document 形式停在壳 Project 里（Linear 里 Document 只能挂在 Project / Initiative 上）。
- **计划内 vs 计划外分流**。计划外的活一律先进 Triage 等审，不许直接进团队工作流。
- **状态由事件驱动**。PR 合并、部署完成驱动状态流转，不靠人手动改。
- **Agent 起草，人校验**。spec、验收标准、对外发布内容必须经人核对。

## 使用方法

把 `SKILL.md` 放进 Agent 的 skill 目录（如 `~/.config/devin/skills/linear-pipeline/`、`.claude/skills/` 或 Linear 的 team-level skill），按你的团队结构改写「Workspace 地图」一节。

## License

MIT
