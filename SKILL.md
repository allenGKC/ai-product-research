---
name: ai-product-research
description: >
  AI 产品一键深扒。当用户说"深扒XX"、"调研XX"、"分析XX产品"、"产品调研"、
  "帮我看看XX"、"XX怎么样"时触发。输入一个产品名，自动用 XCrawl 抓取
  官网功能、GitHub 数据、社区评价、竞品对比，输出结构化调研报告。
---

# AI 产品一键深扒

输入一个 AI 产品名称，自动完成全维度调研，输出结构化报告。

## 前置条件

需要 XCrawl API key，存放在 `~/.xcrawl/config.json`：

```json
{"apiKey": "xc-xxxxxxxx"}
```

如果文件不存在，提示用户去 https://dash.xcrawl.com/api-key 获取。

## 执行流程

读取 API key：

```bash
cat ~/.xcrawl/config.json | python3 -c "import sys,json; print(json.load(sys.stdin)['apiKey'])"
```

然后按顺序执行以下步骤。每步用 `xcrawl_search` 或 `xcrawl_scrape`，通过 curl 调用 REST API。

### Step 1：搜索产品官网

```bash
curl -s -X POST https://run.xcrawl.com/v1/search \
  -H "Authorization: Bearer $XCRAWL_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"query": "[产品名] official site", "limit": 5}'
```

从结果中找到官网 URL。

### Step 2：抓取官网首页

```bash
curl -s -X POST https://run.xcrawl.com/v1/scrape \
  -H "Authorization: Bearer $XCRAWL_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"url": "[官网URL]", "output": {"formats": ["markdown"]}}'
```

提取：产品定位、核心功能列表、定价信息。

### Step 3：搜索 GitHub 仓库

```bash
curl -s -X POST https://run.xcrawl.com/v1/search \
  -H "Authorization: Bearer $XCRAWL_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"query": "[产品名] github", "limit": 5}'
```

找到 GitHub 仓库后，抓取 README 提取 star 数、最近更新、技术栈。

### Step 4：搜索社区评价

```bash
curl -s -X POST https://run.xcrawl.com/v1/search \
  -H "Authorization: Bearer $XCRAWL_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"query": "[产品名] review OR review OR 评测 OR 体验", "limit": 10}'
```

汇总正面和负面评价。

### Step 5：搜索竞品对比

```bash
curl -s -X POST https://run.xcrawl.com/v1/search \
  -H "Authorization: Bearer $XCRAWL_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"query": "[产品名] vs alternative OR 竞品 OR 对比", "limit": 5}'
```

### Step 6：生成报告

汇总所有信息，按下方模板输出。

## 输出模板

```markdown
# [产品名] 产品调研报告

> 调研时间：YYYY-MM-DD | 数据来源：XCrawl 自动抓取

## 一句话总结
[用一句话概括这个产品是什么、解决什么问题]

## 基本信息
| 项目 | 详情 |
|------|------|
| 官网 | [URL] |
| 定位 | [一句话描述] |
| 创始/团队 | [如有] |
| 上线时间 | [如有] |

## 核心功能
1. **[功能名]**：[一句话说明]
2. **[功能名]**：[一句话说明]
3. ...

## 定价策略
| 版本 | 价格 | 包含内容 |
|------|------|---------|
| 免费版 | ... | ... |
| 付费版 | ... | ... |

## GitHub / 技术指标
| 指标 | 数据 |
|------|------|
| Star 数 | ... |
| 最近更新 | ... |
| 技术栈 | ... |
| 开源协议 | ... |

## 社区评价

**正面反馈：**
- ...

**负面反馈：**
- ...

## 竞品对比
| 维度 | [产品名] | 竞品A | 竞品B |
|------|---------|-------|-------|
| 价格 | ... | ... | ... |
| 功能 | ... | ... | ... |
| 易用性 | ... | ... | ... |

## 木马人点评
- **适合谁**：[目标用户画像]
- **值不值得用**：[个人判断]
- **写作角度**：[如果要写文章，建议的切入角度]

## 结论与推荐

基于以上调研数据，给出明确结论。不要模棱两可，要像朋友推荐一样直接。

格式：
- **结论**：[一句话判断，如"值得试试"、"现阶段不推荐"、"适合特定人群"]
- **核心理由**（2-3 条）：[用调研数据支撑，不要空说]
- **主要顾虑**（1-2 条）：[客观指出风险或不足]
- **行动建议**：[具体该做什么，如"先注册试用免费额度"、"等它出 v2 再看"]
```

## 注意事项

- 如果某步搜索结果不理想，换个关键词重试一次
- GitHub 数据如果搜不到，可以跳过，不要卡住
- 抓取失败的步骤标注"未获取到数据"，继续下一步
- 社区评价要客观呈现正反两面
- 木马人点评保持朋友聊天式语气，不端架子
