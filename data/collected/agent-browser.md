---
name: Agent Browser
source: skillhub.cn
url: https://skillhub.cn/skills/agent-browser
collected_date: 2026-05-09
usage_count: 25.5万
author: thesethrose (via ClawHub)
---

# Agent Browser

基于Rust的快速无头浏览器自动化CLI，支持Node.js回退，允许AI代理通过结构化命令执行页面导航、点击、输入和快照操作。

## Installation

```bash
npm install -g agent-browser
agent-browser install
```

## Quick start

```bash
agent-browser open <url>        # Navigate to page
agent-browser snapshot -i       # Get interactive elements with refs
agent-browser click @e1         # Click element by ref
agent-browser fill @e2 "text"   # Fill input by ref
agent-browser close             # Close browser
```

## Core workflow

1. Navigate: `agent-browser open <url>`
2. Snapshot: `agent-browser snapshot -i` (returns elements with refs like @e1, @e2)
3. Interact using refs from the snapshot
4. Re-snapshot after navigation or significant DOM changes

## Commands

### Navigation
- `agent-browser open <url>` - Navigate to URL
- `agent-browser back` - Go back
- `agent-browser forward` - Go forward
- `agent-browser reload` - Reload page
- `agent-browser close` - Close browser

### Snapshot (page analysis)
- `agent-browser snapshot` - Full accessibility tree
- `agent-browser snapshot -i` - Interactive elements only (recommended)
- `agent-browser snapshot -c` - Compact output
- `agent-browser snapshot -d 3` - Limit depth to 3
- `agent-browser snapshot -s "#main"` - Scope to CSS selector

### Interactions (use @refs from snapshot)
- `agent-browser click @e1` - Click
- `agent-browser fill @e2 "text"` - Clear and type
- `agent-browser type @e2 "text"` - Type without clearing
- `agent-browser press Enter` - Press key
- `agent-browser hover @e1` - Hover
- `agent-browser check @e1` - Check checkbox
- `agent-browser select @e1 "value"` - Select dropdown

### Get information
- `agent-browser get text @e1` - Get element text
- `agent-browser get url` - Get current URL
- `agent-browser get title` - Get page title

---

## 收集说明

- 收集时间：2026-05-09
- 数据来源：skillhub.cn 详情页
- 原作者：thesethrose (via ClawHub)
