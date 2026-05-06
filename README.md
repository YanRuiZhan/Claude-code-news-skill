# /news — Claude Code 新闻资讯技能

从 Hacker News、AI Base、The Next Web、HelloGitHub、HubLens 等多个新闻源搜集素材，整理成 10-20 条中文新闻简讯的 Claude Code 技能。

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

技能会自动从多个新闻源并发抓取最新热点，汇总去重后按板块分类输出。

## 推荐配置

- 建议配置 **HubLens MCP**，可优先提供 AI、GitHub 与产品动态聚合信号。
- 建议安装 **Tavily MCP** 作为搜索补充，在 WebSearch 不稳定时可作为备选。

## 新闻源

| 源 | 说明 | 访问方式 |
|---|---|---|
| [AI Base](https://www.aibase.com/zh/daily) | AI 领域每日新闻，中文，墙内可达 | WebFetch 直接抓取 |
| HubLens | AI / GitHub / 产品动态聚合源 | 优先通过已配置的 HubLens MCP 获取 |
| [Hacker News](https://news.ycombinator.com) | 全球技术热点 | WebSearch 搜索 |
| [HelloGitHub](https://hellogithub.com) | 开源项目推荐，中文 | WebFetch 或 WebSearch |
| [The Next Web](https://thenextweb.com/news) | 国际科技新闻 | WebSearch 搜索 |
| WebSearch 补充 | 覆盖其他热点 | 关键词搜索 |

## 抓取策略

考虑到网络环境限制，默认采用以下优先级：

1. 已配置的 **HubLens MCP**
2. 中文站点直抓：**AI Base**、**HelloGitHub**
3. **WebSearch** 搜索 Hacker News、TNW 等国际站点
4. 必要时使用 **Tavily** 作为备选
5. 最后补充中文关键词搜索，如“今日科技热点”“AI 新闻”

## 输出格式

按板块分类输出，每条简讯不超过 2 句话，总量 10-20 条：

```
新闻日期 YYYY-MM-DD

### 一、板块名称

| # | 标题 | 要点 |
|---|------|------|
| 1 | **主标题** | 一句话简述 |
```

常见板块包括：

- AI / 大模型
- 行业事件
- 投融资与市场
- 开源项目
- 开发者趋势

## 示例输出

以下为 2026-05-06 运行 `/news` 的实际输出：

### 一、AI / 大模型

| # | 标题 | 要点 |
|---|------|------|
| 1 | **OpenAI 发布 GPT-5.5 Instant** | OpenAI 将 GPT-5.5 Instant 升级为 ChatGPT 默认模型，并同步提供 API `chat-latest`；重点是更少幻觉、更少冗余追问和更简洁输出。 |
| 2 | **Anthropic 被曝与 Google Cloud 签下 2000 亿美元大单** | 多家媒体称 Anthropic 承诺未来五年向 Google 采购云服务与芯片算力，金额约 2000 亿美元，反映头部模型公司对算力的长期绑定。 |
| 3 | **Anthropic 新一轮融资估值冲向 9000 亿美元** | TechCrunch 和 CNBC 均报道 Anthropic 正筹备新融资，估值或升至 9000 亿美元级别，显示资本市场继续押注头部 AI 平台。 |
| 4 | **腾讯混元推出 5 个开源 3D 模型** | AI Base 今日快讯提到腾讯混元集中发布一批 3D 相关开源模型，继续加码多模态与生成式内容基础设施。 |
| 5 | **Chrome 被曝自动下载约 4GB AI 模型引发隐私争议** | AI Base 汇总称 Google Chrome 为 Gemini Nano 相关能力自动下发大模型文件，引发本地存储占用与用户知情权讨论。 |
| 6 | **苹果被曝将允许 iPhone 选择第三方 AI 模型** | 多家媒体转述，未来 iOS 能力可能允许用户在 Siri 等场景中选择 Google 或 Anthropic 的模型，AI 入口控制权进一步开放。 |

### 二、行业事件

| # | 标题 | 要点 |
|---|------|------|
| 7 | **Wiz 用 AI 逆向发现 GitHub 高危 RCE 漏洞** | CVE-2026-3854 影响 GitHub.com 与 GitHub Enterprise Server，攻击者在具备 push 权限时可借单次 `git push` 触发后端命令执行。 |
| 8 | **GitHub 在数小时内完成修复与缓解** | GitHub 表示在收到报告后 40 分钟内完成复现确认，并在两小时左右向 GitHub.com 部署修复，GitHub Enterprise Server 补丁随后发布。 |
| 9 | **AI 辅助漏洞挖掘正在加速进入实战期** | 从 GitHub 漏洞到 Linux 老漏洞再发现，近期多起案例都显示 AI 已开始显著降低高价值漏洞研究的时间成本。 |

### 三、投融资与市场

| # | 标题 | 要点 |
|---|------|------|
| 10 | **Nscale 宣布在葡萄牙投资 6.95 亿欧元并联手微软** | TNW 报道 AI 基础设施公司 Nscale 加码葡萄牙数据中心与 AI 基础设施建设，说明欧洲本地算力布局仍在升温。 |
| 11 | **YC 最新投资命题更偏向硬科技与重资产 AI** | TNW 指出，Y Combinator 最新论调已从纯软件扩展到机器人、无人机、芯片等更重资本领域，AI 创业逻辑继续外溢到实体世界。 |
| 12 | **Kimi 融资消息持续发酵** | AI Base 将“Kimi 获 20 亿美元新融资”列为今日热点之一，尽管仍需等待更权威披露，但国产大模型头部融资预期明显升温。 |

### 四、开源项目

| # | 项目 | ⭐ | 简介 |
|---|------|----|------|
| 13 | **systeminformer** | — | HelloGitHub 第 121 期收录的 Windows 系统监控工具，适合开发者与运维查看进程、句柄和系统状态。 |
| 14 | **OfficeCLI** | — | 命令行操作 Word / Excel / PPT 的工具，体现办公自动化继续向 CLI 与 Agent 工作流靠拢。 |
| 15 | **abtop** | — | 用于监控 AI 编程助手使用情况的工具，贴近当前开发者对 Agent 成本、上下文和效率的关注。 |
| 16 | **DAC** | — | HN 近期出现的 “dashboard as code” 开源工具，主打给 AI agents 和人类共同使用的可视化工作流。 |
| 17 | **Pu.sh** | — | HN 上的轻量 coding-agent harness 项目，强调用很少的 shell 代码搭建完整代理执行回路。 |

### 五、开发者趋势

- **开发者社区继续围绕 coding agents 展开工具创新**：Hacker News 近期高频出现 agent harness、agent dashboard、Claude Code 插件、知识库构建等项目。
- **“AI + 安全研究”正在成为新基建能力**：AI 不再只用于写代码，也在逆向、模糊测试、漏洞发现与补丁验证中快速落地。
- **中文聚合源与国际源出现明显共振**：一边是 GPT-5.5、Anthropic、Chrome AI 模型等国际话题，另一边是腾讯混元、Kimi 等国产模型动态同步升温。

## 环境要求

- Claude Code（任意版本）
- 网络连接（优先 HubLens，其次中文站直抓，再用 WebSearch / Tavily 补充）
