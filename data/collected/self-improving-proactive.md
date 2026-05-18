---
name: Self-Improving + Proactive Agent
source: skillhub.cn
url: https://skillhub.cn/skills/self-improving
collected_date: 2026-05-09
usage_count: 26.5万
author: ivangdavila (via ClawHub)
---

# Self-Improving + Proactive Agent

自我反思+自我批评+自我学习+自组织记忆。智能体评估自身工作、发现错误并持续改进。

## When to Use

- User corrects you or points out mistakes
- You complete significant work and want to evaluate the outcome
- You notice something in your own output that could be better
- Knowledge should compound over time without manual maintenance

## Architecture

Memory lives in `~/self-improving/` with tiered structure:

```
~/self-improving/
├── memory.md          # HOT: ≤100 lines, always loaded
├── index.md           # Topic index with line counts
├── heartbeat-state.md # Heartbeat state
├── projects/          # Per-project learnings
├── domains/           # Domain-specific (code, writing, comms)
├── archive/           # COLD: decayed patterns
└── corrections.md     # Last 50 corrections log
```

## Learning Signals

Log automatically when you notice these patterns:

### Corrections → add to corrections.md
- "No, that's not right..."
- "Actually, it should be..."
- "You're wrong about..."
- "I prefer X, not Y"
- "Remember that I always..."
- "I told you before..."

### Preference signals → add to memory.md if explicit
- "I like when you..."
- "Always do X for me"
- "Never do Y"
- "My style is..."

### Pattern candidates → track, promote after 3x
- Same instruction repeated 3+ times
- Workflow that works well repeatedly
- User praises specific approach

## Self-Reflection

After completing significant work, pause and evaluate:
- Did it meet expectations?
- What could be better?
- Is this a pattern?

Log format:
```
CONTEXT: [type of task]
REFLECTION: [what I noticed]
LESSON: [what to do differently]
```

---

## 收集说明

- 收集时间：2026-05-09
- 数据来源：skillhub.cn 详情页
- 原作者：ivangdavila (via ClawHub)
