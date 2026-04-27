# /news — Claude Code 新闻资讯技能

从 Hacker News、AI Base、The Next Web、HelloGitHub 等多个新闻源搜集素材，整理成 10-20 条中文新闻简讯的 Claude Code 技能。

## 安装

```bash
# 克隆到 Claude Code skills 目录
git clone https://github.com/YanRuiZhan/news-skill.git ~/.claude/skills/news
```

或者手动将 `SKILL.md` 复制到 `~/.claude/skills/news/` 目录下。

## 用法

在 Claude Code 中输入：

```
/news
```

技能会自动从多个新闻源并发抓取最新热点，整理分类输出。

## 新闻源

| 源 | 说明 | 访问方式 |
|---|---|---|
| [AI Base](https://www.aibase.com/zh/daily) | AI 领域每日新闻，中文 | WebFetch 直接抓取 |
| [Hacker News](https://news.ycombinator.com) | 全球技术热点 | WebSearch 搜索 |
| [HelloGitHub](https://hellogithub.com) | 开源项目推荐，中文 | WebFetch 或 WebSearch |
| [The Next Web](https://thenextweb.com/news) | 国际科技新闻 | WebSearch 搜索 |
| WebSearch 补充 | 覆盖其他热点 | 关键词搜索 |

## 输出格式

按板块分类输出，每条简讯不超过 2 句话，总量 10-20 条：

```
新闻日期 YYYY-MM-DD

### 一、板块名称

| # | 标题 | 要点 |
|---|------|------|
| 1 | 主标题 | 一句话简述 |
```

## 环境要求

- Claude Code（任意版本）
- 网络连接（墙内环境已适配，优先使用 WebSearch + 中文站直接抓取）
