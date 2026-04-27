---
name: news
description: 用户输入 /news 时触发。从 Hacker News、AI Base、The Next Web、HelloGitHub 等新闻源搜集素材，整理成10-20条中文新闻简讯。也适用于用户说"看看今天有什么新闻"、"帮我整理最新资讯"等类似请求。
---

# /news — 获取最新新闻资讯

## 执行流程

1. **并发抓取** — 同时从多个新闻源搜索最新热点
2. **汇总去重** — 合并相似话题，筛选出最重要的 10-20 条
3. **分类输出** — 按类别组织，每条简讯不超过 2 句话

## 新闻源（按优先级）

| 源 | 说明 | 建议工具 |
|---|---|---|
| AI Base (aibase.com/zh/daily) | AI 领域每日新闻，中文，墙内可达 | WebFetch 直接抓取 |
| Hacker News (news.ycombinator.com) | 全球技术热点 | WebSearch 搜索最新 |
| HelloGitHub (hellogithub.com) | 开源项目推荐，中文 | WebFetch 或 WebSearch |
| The Next Web (thenextweb.com/news) | 国际科技新闻 | WebSearch 搜索最新 |
| WebSearch 补充搜索 | 覆盖其他热点 | WebSearch 关键词搜索 |

## 抓取策略

考虑到网络环境限制：

- **AI Base** 和 **HelloGitHub** 是中文站，优先用 WebFetch 直接抓取页面内容
- **Hacker News** 和 **TNW** 优先使用 WebSearch 搜索关键词如 "Hacker News top stories today"、"latest tech news" 获取
- 必要时使用 tavily_search / tavily_extract 作为备选
- 最后用 WebSearch 搜索 "今日科技热点"、"AI 新闻" 等中文关键词作为补充

## 输出格式

用以下排版结构输出，板块之间不用分割线，表格已足够区分：

```
新闻日期  YYYY-MM-DD

### 一、板块名称

| # | 标题 | 要点 |
|---|------|------|
| 1 | **主标题** | 一句话简述 |

### 二、板块名称

...
```

### 分类建议

根据当日素材灵活分类，常用分类及对应的格式：

- **分类一：AI / 大模型** — 大模型发布、AI 产品更新、技术突破 → 用表格（标题 + 要点）
- **分类二：行业事件** — 融资收购、安全事件、大公司动态 → 用表格
- **分类三：投融资与市场** — 金额、估值、交易结构 → 用表格
- **分类四：开源项目** — 热门新项目 → 用表格（增加 ⭐ 列展示热度）
- **分类五：开发者趋势** — 框架更新、统计数据 → 可用精简列表

### 格式要求

- 每条简讯严格控制在 2 句话以内
- 保持客观事实陈述，不添加评论
- 总量控制在 10-20 条
- 如果某类信息过少，可合并分类
- 日期标注为抓取当日日期
- 板块间无需 `---` 分割线，标题 + 表格已是足够的视觉分隔
