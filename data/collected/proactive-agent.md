---
name: Proactive Agent
source: skillhub.cn
url: https://skillhub.cn/skills/proactive-agent
collected_date: 2026-05-09
usage_count: 18.6万
author: halthelobster (via ClawHub)
---

# Proactive Agent 🦞

将AI智能体从任务执行者升级为主动预判需求、持续优化的智能伙伴。

By Hal Labs — Part of the Hal Stack. A proactive, self-improving architecture for your AI agent.

## The Three Pillars

### Proactive — creates value without being asked
- Anticipates your needs — Asks "what would help my human?"
- Reverse prompting — Surfaces ideas you didn't know to ask for
- Proactive check-ins — Monitors what matters

### Persistent — survives context loss
- WAL Protocol — Writes critical details BEFORE responding
- Working Buffer — Captures every exchange in the danger zone
- Compaction Recovery — Knows exactly how to recover after context loss

### Self-improving — gets better at serving you
- Self-healing — Fixes its own issues
- Relentless resourcefulness — Tries 10 approaches before giving up
- Safe evolution — Guardrails prevent drift

## Architecture Overview

```
workspace/
├── ONBOARDING.md      # First-run setup
├── AGENTS.md          # Operating rules, learned lessons
├── SOUL.md            # Identity, principles, boundaries
├── USER.md            # Human's context, goals, preferences
├── MEMORY.md          # Curated long-term memory
├── SESSION-STATE.md   # Active working memory (WAL target)
├── HEARTBEAT.md       # Periodic self-improvement checklist
├── TOOLS.md           # Tool configurations
└── memory/
    ├── YYYY-MM-DD.md  # Daily raw capture
    └── working-buffer.md  # Danger zone log
```

## Quick Start

1. Copy assets to workspace: `cp assets/*.md ./`
2. Agent detects ONBOARDING.md and offers setup
3. Answer questions (all at once, or drip over time)
4. Agent auto-populates USER.md and SOUL.md
5. Run security audit: `./scripts/security-audit.sh`

## Core Philosophy

The mindset shift: Don't ask "what should I do?" Ask "what would genuinely delight my human that they haven't thought to ask for?"

---

## 收集说明

- 收集时间：2026-05-09
- 数据来源：skillhub.cn 详情页
- 原作者：halthelobster (via ClawHub)
