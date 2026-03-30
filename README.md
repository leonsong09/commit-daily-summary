# commit-daily-summary

<p align="center">
    <a href="https://linux.do" alt="LINUX DO"><img src="https://shorturl.at/ggSqS" /></a>
</p>

[![License](https://img.shields.io/github/license/leonsong09/commit-daily-summary)](https://github.com/leonsong09/commit-daily-summary/blob/main/LICENSE)
[![Last Commit](https://img.shields.io/github/last-commit/leonsong09/commit-daily-summary)](https://github.com/leonsong09/commit-daily-summary/commits/main)
[![Repo Size](https://img.shields.io/github/repo-size/leonsong09/commit-daily-summary)](https://github.com/leonsong09/commit-daily-summary)

> 基于 git 提交生成中文日报，把原始 commit 压缩成按主题聚合、动作导向的可读总结。

## 适用场景

当用户想要：
- 总结我今天做了什么
- 总结我的提交
- 提交总结
- 今天提交总结
- 日报

## 不适用场景

以下情况更适合其他 skill：
- 当前会话收尾：`session-wrap`
- 同日项目级工作汇总：`project-daily-summary`
- 调研/分析结论整理：`research-note-wrap`
- 只看未提交工作区改动而不是提交记录

## 触发词

中文：
- 总结我今天做了什么
- 总结我的提交
- 提交总结
- 今天提交总结
- 日报

English:
- summarize my commits
- what did I do today
- daily commit summary

## 工作流

1. 先确定日期范围与仓库范围，默认是**今天 / 当前仓库**。
2. 用 git log 收集提交作为第一证据源。
3. 把相关 commits 聚合为 workstream，而不是一条 commit 对一条摘要。
4. 改写成中文动作化总结句。
5. 输出日报；必要时再附原始 commits。

## 安装

将整个目录复制到本地技能目录，例如：

```text
~/.codex/skills/commit-daily-summary
```

或：

```text
~/.agents/skills/commit-daily-summary
```

## 仓库结构

```text
commit-daily-summary/
  SKILL.md
  README.md
  LICENSE
  .gitignore
```

## 配置

该 skill 默认不写死日报输出路径；若项目要求落盘，可在项目 `AGENTS.md` 中补充保存目录和文件名规范。

## 用法示例

### 示例输入

```text
总结我的提交
```

### 预期行为

- 明确时间范围
- 读取 git 提交
- 聚合同主题 commits
- 输出中文动作化总结
- 避免单纯罗列原始 commit 标题

## 输出示例

```markdown
## 提交总结

- 日期：2026-03-30
- 范围：today / current repo

### 今日工作摘要
- 修复了任务页终态刷新问题
- 补充了设置保存链路的回归测试
- 整理了图表配置与调试日志输出
```

## 限制

- 它以 git 提交为核心证据；如果没有 commit，需要明确说明。
- 它不适合替代当前会话总结或项目级全局日报。
- 若提交粒度很差，摘要质量也会受影响。

## License

MIT


