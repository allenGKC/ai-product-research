# XCrawl 产品调研报告

> 调研时间：2026-05-08 | 数据来源：XCrawl 自动抓取（6 次搜索 + 4 次抓取）

## 一句话总结

XCrawl 是一个面向 AI 时代的网页数据 API 平台，把任意网站转换成 LLM 友好的结构化数据（Markdown/JSON），主打"不用写爬虫代码，一个 API 搞定"。

## 基本信息

| 项目 | 详情 |
|------|------|
| 官网 | https://xcrawl.com |
| 文档 | https://docs.xcrawl.com |
| GitHub | https://github.com/xcrawl-api |
| 定位 | AI-ready web scraping API，结构化数据提取平台 |
| Trustpilot | 4.6/5（20 条评价） |

## 核心产品线（6 个 API）

| API | 干什么 | 一句话说明 |
|-----|--------|-----------|
| **Scrape API** | 单页抓取 | 输入 URL，输出 Markdown/JSON/截图，支持 JS 渲染 |
| **Search API** | 多引擎搜索 | 搜 Google/Bing/DuckDuckGo，返回结构化 SERP 数据 |
| **SERP API** | 深度 SERP | 富结果、People Also Ask、知识图谱，SEO 专用 |
| **Crawl API** | 批量爬取 | 智能递归爬站，深度最多 3 级，单次最多 100 页 |
| **Map API** | 站点地图 | 扫描域名下所有 URL，最多 10 万个 |
| **ChatGPT API** | ChatGPT 数据 | 从 ChatGPT 交互中提取结构化数据（新功能） |

## 定价策略

| 方案 | 价格 | 说明 |
|------|------|------|
| 免费试用 | 1,000 credits | 注册即送，无需信用卡 |
| 按量付费 | ~$1/1000 页 | 10 个并发任务 |
| Pro 月付 | $99/月 | 更多并发 + 高级功能 |

实际使用中，搜索一次约 2 credits，抓取一页约 1-2 credits。

## 技术亮点

- **LLM 友好输出**：直接返回干净的 Markdown，不用二次清洗
- **防反爬能力**：内置住宅代理轮换 + 浏览器指纹伪装，官方宣称 99%+ 成功率
- **MCP 集成**：支持 Claude Code / Cursor / VS Code 等 AI 工具直接调用
- **无代码集成**：支持 n8n / Zapier / Make 自动化工作流
- **全球代理**：支持按国家/地区选择代理节点

## GitHub / 开源

| 项目 | 说明 |
|------|------|
| xcrawl-skills | 5 个官方 Skill（scrape/search/map/crawl/默认入口），面向多 Agent 运行时 |
| 开发语言 | TypeScript / Node.js |
| 开源协议 | MIT |
| 活跃度 | 仓库较新（2026 年 3 月），社区贡献者活动尚少 |

## 社区评价

**正面反馈（Trustpilot 4.6/5）：**
- "今年用过最好的 web scraping API"
- CLI 工具方便快速测试
- 住宅代理自动轮换 + 指纹伪装效果好
- X 上开发者圈子里口碑不错，"LLM 友好格式"是核心卖点

**负面/中性反馈：**
- 相比 Firecrawl、ScrapingBee 等竞品，知名度还不够高
- GitHub 社区活跃度偏低（5 个仓库，提交数少）
- 定价页面信息不够透明（需注册后查看详细方案）

## 竞品对比

| 维度 | XCrawl | Firecrawl | ScrapingBee | Apify |
|------|--------|-----------|-------------|-------|
| 核心定位 | AI 数据 API | AI 爬虫平台 | 通用爬虫 API | 全功能爬虫平台 |
| LLM 友好格式 | ✅ 原生支持 | ✅ 原生支持 | ❌ 需后处理 | ❌ 需后处理 |
| MCP 集成 | ✅ 官方支持 | ✅ 官方支持 | ❌ | ❌ |
| 免费额度 | 1,000 credits | 500 credits | 1,000 credits | $5 额度 |
| 起步价 | ~$1/1000页 | $16/月 | $49/月 | $49/月 |
| 防反爬 | 住宅代理+指纹 | 住宅代理 | 住宅代理 | 自带代理 |
| 独特卖点 | ChatGPT API、SERP 深度分析 | 开源、Fire Engine | 简单易用 | Actor 生态 |

## 木马人点评

**适合谁：**
- AI Agent 开发者（需要给 Agent 装上网能力）
- 自媒体人（调研竞品、收集素材、SEO 分析）
- 不想写爬虫代码但需要网页数据的人

**值不值得用：**
- 如果你已经在用 Claude Code / OpenClaw，XCrawl 的 MCP 集成是最大加分项
- 免费 1,000 credits 够测试，按量付费比月付方案灵活
- 和 Firecrawl 比，各有千秋；XCrawl 的 SERP API 和 ChatGPT API 是差异化优势

**写作角度：**
- "用 XCrawl 做了一个 AI 产品深扒 Skill"（当前选题）
- "XCrawl vs Firecrawl：AI 爬虫选哪个？"
- "给 Claude Code 装上网能力：XCrawl MCP 实战"
