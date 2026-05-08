# AI Product Research

一键深扒任意 AI 产品。输入产品名，自动抓取官网功能、GitHub 数据、社区评价、竞品对比，输出结构化调研报告。

## 安装

**最简单：把链接丢给你的 AI Agent**

在 Claude Code、Codex、OpenClaw 或其他 AI Agent 中，直接说：

```
帮我安装这个 skill：https://github.com/allenGKC/ai-product-research
```

Agent 会自动完成安装。

**手动安装**

```bash
# Claude Code
git clone https://github.com/allenGKC/ai-product-research.git ~/.claude/skills/ai-product-research

# OpenClaw
git clone https://github.com/allenGKC/ai-product-research.git ~/skills/ai-product-research

# Codex
git clone https://github.com/allenGKC/ai-product-research.git ~/.codex/skills/ai-product-research
```

## 前置条件

需要 XCrawl API key（注册即送 1,000 免费 credits）：

### 第一步：注册 XCrawl

通过以下链接注册：

👉 https://xcrawl.com/?keyword=henitdw4

注册流程：
1. 打开链接，点击 **Start Free Trial**
2. 用邮箱注册（无需信用卡）
3. 注册完成后自动获得 1,000 免费 credits

### 第二步：获取 API key

1. 登录后进入 https://dash.xcrawl.com/api-key
2. 复制你的 API key

### 第三步：配置到本地

创建配置文件 `~/.xcrawl/config.json`：

```json
{"apiKey": "xc-你的key"}
```

搞定，可以直接用了。每次搜索约 2 credits，抓取一页约 1-2 credits，1,000 credits 能用很久。

## 使用

在你的 AI Agent 中说：

```
深扒一下 Cursor
```

或者：

```
帮我调研一下 v0 这个产品
```

Skill 会自动：
1. 搜索产品官网，抓取功能和定价
2. 搜索 GitHub 仓库，提取技术指标
3. 搜索社区评价（Trustpilot、Reddit、X 等）
4. 搜索竞品对比
5. 输出结构化调研报告

## 示例输出

见 [example-output-xcrawl.md](example-output-xcrawl.md) — 用 XCrawl 深扒 XCrawl 自己的完整报告。

## 报告包含

- 一句话总结
- 核心功能列表
- 定价策略
- GitHub / 技术指标
- 社区评价（正面 + 负面）
- 竞品对比表
- 木马人点评（适合谁、值不值得用、写作角度）

## License

MIT
