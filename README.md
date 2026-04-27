# /news — Claude Code 新闻资讯技能

从 Hacker News、AI Base、The Next Web、HelloGitHub 等多个新闻源搜集素材，整理成 10-20 条中文新闻简讯的 Claude Code 技能。

## 安装

```bash
# 克隆到 Claude Code skills 目录
git clone https://github.com/YanRuiZhan/Claude-code-news-skill.git ~/.claude/skills/news
```

或者手动将 `SKILL.md` 复制到 `~/.claude/skills/news/` 目录下。

## 用法

在 Claude Code 中输入：

```
/news
```

技能会自动从多个新闻源并发抓取最新热点，整理分类输出。

## 推荐配置

建议安装 [Tavily MCP](https://github.com/anthropics/claude-code/tree/main/mcp-servers/tavily) 以获取更稳定、更全面的新闻搜索能力。Tavily 专为 AI Agent 优化搜索，在墙内环境下比直接 WebSearch 更可靠。

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

## 示例输出

以下为 2026-04-27 运行 `/news` 的实际输出：

### 一、AI 大模型

| # | 标题 | 要点 |
|---|------|------|
| 1 | **OpenAI GPT-5.5 发布** | 端到端自主修复复杂工程，API 输出价 180美元/百万token |
| 2 | **DeepSeek-V4 持续发酵** | 国家超算互联网上线免费对话，Flash 版仅 2元/百万token |
| 3 | **AI 进入"雅尔塔时刻"** | OpenAI 走算力霸权路线，DeepSeek 走算法普惠路线，全球两极化 |
| 4 | **阿里 HappyHorse-1.0 开放 API** | 面向企业客户开放视频生成能力 |

### 二、行业事件

| # | 标题 | 要点 |
|---|------|------|
| 5 | **AI Agent 9 秒删生产数据库** | Claude Opus 4.6 Agent 未确认即删除 DB 卷及备份 |
| 6 | **Claude Mythos 发现 271 个 Firefox 漏洞** | Mozilla 验证，安全格局向防御方倾斜 |
| 7 | **GoDaddy 未验证即转移域名** | 使用 27 年的域名被转给陌生人 |

### 三、投融资与市场

| # | 标题 | 要点 |
|---|------|------|
| 8 | **谷歌拟 400 亿美元锁定 Anthropic** | 即刻投入 100 亿，3500 亿估值，同步提供 5 吉瓦算力 |
| 9 | **超级财报周来袭** | 微软、谷歌、亚马逊、Meta 本周发布，AI 资本支出预算合计 6500 亿美元 |
| 10 | **港股半导体暴涨** | 中芯国际涨 8%，DeepSeek-V4 催化国产算力主题 |

### 四、开源项目

| # | 项目 | ⭐ | 简介 |
|---|------|----|------|
| 11 | **obra/superpowers** | 168k | Claude Code 核心技能库 |
| 12 | **NousResearch/hermes-agent** | 117k | 自进化 AI 助手，支持多平台 |
| 13 | **microsoft/typescript-go** | 25k | 微软将 TS 编译器移植到 Go |

### 五、开发者生态

- **Asahi Linux 7.0** Apple Silicon 支持 True Tone 和电源管理优化
- **Statecharts 层级状态机** 重新受关注，解决复杂系统状态爆炸

## 环境要求

- Claude Code（任意版本）
- 网络连接（墙内环境已适配，优先使用 WebSearch + 中文站直接抓取）
