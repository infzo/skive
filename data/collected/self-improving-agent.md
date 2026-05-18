---
name: Self-Improving Agent
source: skillhub.cn
url: https://skillhub.cn/skills/self-improving-agent
collected_date: 2026-05-09
usage_count: 60.2万
author: pskoett (via ClawHub)
---

# Self-Improving Agent

捕获经验教训、错误和纠正，以实现持续改进。使用时机：（1）命令或操作意外失败；（2）用户纠正……

Log learnings and errors to markdown files for continuous improvement. Coding agents can later process these into fixes, and important learnings get promoted to project memory.

## First-Use Initialisation

Before logging anything, ensure the .learnings/ directory and files exist in the project or workspace root. If any are missing, create them:

```
mkdir -p .learnings
[ -f .learnings/LEARNINGS.md ] || printf "# Learnings\n\nCorrections, insights, and knowledge gaps captured during development.\n\n**Categories**: correction | insight | knowledge_gap | best_practice\n\n---\n" > .learnings/LEARNINGS.md
[ -f .learnings/ERRORS.md ] || printf "# Errors\n\nCommand failures and integration errors.\n\n---\n" > .learnings/ERRORS.md
[ -f .learnings/FEATURE_REQUESTS.md ] || printf "# Feature Requests\n\nCapabilities requested by the user.\n\n---\n" > .learnings/FEATURE_REQUESTS.md
```

Never overwrite existing files. This is a no-op if .learnings/ is already initialised.

## Quick Reference

- Log errors → `.learnings/ERRORS.md`
- Log learnings (correction) → `.learnings/LEARNINGS.md`
- Log learnings (knowledge_gap) → `.learnings/LEARNINGS.md`
- Log learnings (best_practice) → `.learnings/LEARNINGS.md`
- Log feature requests → `.learnings/FEATURE_REQUESTS.md`

## OpenClaw Setup (Recommended)

OpenClaw is the primary platform for this skill. It uses workspace-based prompt injection with automatic skill loading.

### Installation

Via ClawdHub (recommended):
```
clawdhub install self-improving-agent
```

Manual:
```
git clone https://github.com/peterskoett/self-improving-agent.git ~/.openclaw/skills/self-improving-agent
```

### Workspace Structure

```
~/.openclaw/workspace/
├── AGENTS.md          # Multi-agent workflows, delegation patterns
├── SOUL.md            # Behavioral guidelines, personality, principles
├── TOOLS.md           # Tool capabilities, integration gotchas
├── MEMORY.md          # Long-term memory (main session only)
├── memory/            # Daily memory files
│   └── YYYY-MM-DD.md
└── .learnings/        # This skill's log files
    ├── LEARNINGS.md
    ├── ERRORS.md
    └── FEATURE_REQUESTS.md
```

---

## 收集说明

- 收集时间：2026-05-09
- 数据来源：skillhub.cn 详情页
- 原作者：pskoett (via ClawHub)
