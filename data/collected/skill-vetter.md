---
name: Skill Vetter
source: skillhub.cn
url: https://skillhub.cn/skills/skill-vetter
collected_date: 2026-05-09
usage_count: 23.5万
author: spclaudehome (via ClawHub)
---

# Skill Vetter 🔒

AI智能体技能安全预审工具。安装ClawdHub、GitHub等来源技能前，检查风险信号、权限范围及可疑模式。

Security-first vetting protocol for AI agent skills. Never install a skill without vetting it first.

## When to Use

- Before installing any skill from ClawdHub
- Before running skills from GitHub repos
- When evaluating skills shared by other agents
- Anytime you're asked to install unknown code

## Vetting Protocol

### Step 1: Source Check
- Where did this skill come from?
- Is the author known/reputable?
- How many downloads/stars does it have?
- When was it last updated?

### Step 2: Code Review (MANDATORY)

🚨 REJECT IMMEDIATELY IF YOU SEE:
- curl/wget to unknown URLs
- Sends data to external servers
- Requests credentials/tokens/API keys
- Reads ~/.ssh, ~/.aws, ~/.config without clear reason
- Accesses MEMORY.md, USER.md, SOUL.md, IDENTITY.md
- Uses base64 decode on anything
- Uses eval() or exec() with external input
- Modifies system files outside workspace
- Network calls to IPs instead of domains

### Step 3: Permission Scope
- What files does it need to read/write?
- What commands does it run?
- Does it need network access? To where?

### Step 4: Risk Classification

| Risk Level | Examples | Action |
|------------|----------|--------|
| 🟢 LOW | Notes, weather, formatting | Basic review, install OK |
| 🟡 MEDIUM | File ops, browser, APIs | Full code review required |
| 🔴 HIGH | Credentials, trading, system | Human approval required |
| ⛔ EXTREME | Security configs, root access | Do NOT install |

## Output Format

```
SKILL VETTING REPORT
═══════════════════════════════════════
Skill: [name]
Source: [ClawdHub / GitHub / other]
Author: [username]
RISK LEVEL: [🟢 LOW / 🟡 MEDIUM / 🔴 HIGH / ⛔ EXTREME]
VERDICT: [✅ SAFE / ⚠️ CAUTION / ❌ DO NOT INSTALL]
═══════════════════════════════════════
```

---

## 收集说明

- 收集时间：2026-05-09
- 数据来源：skillhub.cn 详情页
- 原作者：spclaudehome (via ClawHub)
