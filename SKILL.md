---
name: commit-daily-summary
description: Use when the user wants a same-day summary of git commits or a commit-based daily report, asks what they did today, or says 总结我今天做了什么, 总结我的提交, 提交总结, 今天提交总结, 日报.
---

# commit-daily-summary

## Overview

Use this skill to turn one day of git commits into a readable work summary. The goal is not to dump commit lines, but to translate them into grouped, human-friendly task statements.

## Core Rules

- Default scope is **today** in the user's local timezone unless the user gives a date.
- Prefer **git evidence** over memory.
- Group commits by **workstream / theme**, not just by repository order.
- Rewrite raw commit messages into concise Chinese action summaries.
- Do not include empty, noise-only, or clearly meaningless commits as standalone achievements.

## Workflow

### Step 1: Determine the date and repo scope

Default assumptions:
- date range: today
- repository scope: current repository unless the user asks for multiple repositories

Clarify only when necessary:
- today vs a specific date
- current repo vs multiple repos
- whether the user wants only task summaries or task summaries + raw commit details

### Step 2: Collect commits

Use direct git commands with explicit repository paths.

Recommended command pattern:

```bash
git -C <repo> log --since="YYYY-MM-DD 00:00" --until="YYYY-MM-DD 23:59:59" --pretty=format:"%h%x09%s"
```

If no commits are found, state that clearly.

### Step 3: Group commits into workstreams

Cluster related commits together, for example:
- 同一功能开发
- 同一缺陷修复
- 同一配置或工具链调整
- 同一文档更新

Do not create one task sentence per commit if several commits are obviously part of the same workstream.

### Step 4: Rewrite into Chinese action summaries

Good summary lines should:
- start with a clear action verb
- describe the actual business or engineering result
- omit noisy implementation trivia unless it matters
- be understandable to someone reading a daily report quickly

Examples:
- 实现了行情页的筛选条件持久化
- 修复了任务轮询在终态下未刷新概览的问题
- 重构了图表数据映射逻辑，降低了重复处理分支
- 补充了设置保存链路的回归测试

### Step 5: Output the daily report

Preferred structure:
- 日期范围
- 今日工作摘要
- 仓库 / workstream 明细
- 如有需要，再附原始 commits

## Recommended Output Shape

```markdown
## 提交总结

- 日期：2026-03-30
- 范围：today / current repo

### 今日工作摘要
- ...
- ...

### 分项明细
#### 仓库 A
- workstream 1: ...
- workstream 2: ...

### 原始提交（可选）
- abc123 feat(...)
```

## When to Use

- 用户说“总结我今天做了什么”
- 用户说“总结我的提交”
- 用户说“提交总结”
- 用户要一份基于 commit 的日报

## When Not to Use

- 用户要的是当前会话收尾，而不是 commit 视角
- 用户要的是跨会话的项目级日报
- 用户没有 git 提交，真正需要的是工作区变更总结

In those cases, prefer session-wrap or project-daily style skills instead.

## Quality Checklist

Before responding, verify:

- [ ] Date scope is explicit
- [ ] Summary is based on actual commits
- [ ] Related commits are grouped into workstreams
- [ ] Chinese task lines are human-readable and action-oriented
- [ ] Empty noise commits are not treated as major work items



