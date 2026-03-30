# commit-summary

A skill for turning one day of git commits into a concise, human-readable daily work summary.

## What this skill does

`commit-summary` converts raw git commit history into grouped task summaries that are easier to read in standups, daily reports, or work logs.

Instead of repeating raw commit lines, it:
- collects commits within a date range,
- groups related commits by workstream,
- rewrites them into short action-oriented summaries,
- optionally includes raw commit details as an appendix.

## When to use

Use this skill when the user says things like:
- “summarize my commits”
- “what did I do today?”
- “daily commit summary”
- “总结我今天做了什么”
- “总结我的提交”
- “提交总结”
- “今天提交总结”
- “日报”

## When not to use

This skill is **not** the best fit when the user wants:
- a current-session wrap-up,
- a project-wide daily summary that combines sessions and unstaged changes,
- a research note or analysis memo,
- a summary of uncommitted work only.

## Trigger phrases

English:
- summarize my commits
- what did I do today
- daily commit summary

Chinese:
- 总结我今天做了什么
- 总结我的提交
- 提交总结
- 今天提交总结
- 日报

## Workflow

1. **Determine scope**
   - Default to today in the user's local timezone.
   - Decide whether the summary covers one repo or multiple repos.

2. **Collect commits**
   - Use git history as the primary evidence source.
   - Be explicit about the time window.

3. **Group by workstream**
   - Merge related commits into broader themes.
   - Avoid one-line-per-commit summaries when commits clearly belong together.

4. **Rewrite as Chinese action summaries**
   - Use short action verbs.
   - Emphasize outcomes rather than raw implementation noise.

5. **Produce the report**
   - Include date scope, summary bullets, grouped details, and raw commits only if helpful.

## Installation

Copy the folder into your local skills directory.

Common locations:

- Codex: `~/.codex/skills/commit-summary`
- Agents-style setups: `~/.agents/skills/commit-summary`

## Repository structure

```text
commit-summary/
  SKILL.md
  README.md
  LICENSE
  .gitignore
```

## Usage example

### Example prompt

```text
总结我的提交
```

### Expected behavior

The agent should:
- determine the date range,
- read commit history,
- group related work,
- rewrite it into readable Chinese task statements,
- avoid dumping raw commits without interpretation.

## Output example

```markdown
## 提交总结

- 日期：2026-03-30
- 范围：today / current repo

### 今日工作摘要
- 修复了任务页的终态刷新问题
- 补充了设置保存链路的回归测试
- 整理了图表配置与调试日志输出

### 分项明细
#### trading-system
- 图表链路：修复终态刷新与状态展示
- 测试保护：新增 focused 回归用例
```

## Customization

You can adapt this skill for:
- multi-repository daily summaries,
- organization-specific daily report formats,
- timezone-aware work windows,
- append-only commit detail sections.

## Limitations

- It depends on commit history being available.
- It is not a replacement for a session summary when work is still uncommitted.
- It should not invent work beyond what commit evidence supports.

## License

MIT
