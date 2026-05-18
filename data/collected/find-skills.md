---
name: Find Skills
source: skillhub.cn
url: https://skillhub.cn/skills/find-skills
collected_date: 2026-05-09
usage_count: 41.4万
author: jimliuxinghai (via ClawHub)
---

# Find Skills

当用户询问"如何做某事"、"寻找某技能"或希望扩展功能时，帮助发现并安装智能体技能。

This skill helps you discover and install skills from the open agent skills ecosystem.

## When to Use This Skill

Use this skill when the user:
- Asks "how do I do X" where X might be a common task with an existing skill
- Says "find a skill for X" or "is there a skill for X"
- Asks "can you do X" where X is a specialized capability
- Expresses interest in extending agent capabilities
- Wants to search for tools, templates, or workflows
- Mentions they wish they had help with a specific domain

## What is the Skills CLI?

The Skills CLI (`npx skills`) is the package manager for the open agent skills ecosystem.

Key commands:
- `npx skills find [query]` - Search for skills interactively or by keyword
- `npx skills add <package>` - Install a skill from GitHub or other sources
- `npx skills check` - Check for skill updates
- `npx skills update` - Update all installed skills

Browse skills at: https://skills.sh/

## How to Help Users Find Skills

### Step 1: Understand What They Need
- The domain (e.g., React, testing, design, deployment)
- The specific task (e.g., writing tests, creating animations, reviewing PRs)

### Step 2: Search for Skills
```
npx skills find [query]
```

Examples:
- User asks "how do I make my React app faster?" → `npx skills find react performance`
- User asks "can you help me with PR reviews?" → `npx skills find pr review`

### Step 3: Present Options to the User
Show the skill name, install command, and link to learn more.

### Step 4: Offer to Install
```
npx skills add <owner/repo@skill> -g -y
```

## Common Skill Categories

| Category | Example Queries |
|----------|-----------------|
| Web Development | react, nextjs, typescript, css, tailwind |
| Testing | testing, jest, playwright, e2e |
| DevOps | deploy, docker, kubernetes, ci-cd |
| Documentation | docs, readme, changelog, api-docs |
| Code Quality | review, lint, refactor, best-practices |
| Design | ui, ux, design-system, accessibility |
| Productivity | workflow, automation, git |

---

## 收集说明

- 收集时间：2026-05-09
- 数据来源：skillhub.cn 详情页
- 原作者：jimliuxinghai (via ClawHub)
