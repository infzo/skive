---
name: Ontology
source: skillhub.cn
url: https://skillhub.cn/skills/ontology
collected_date: 2026-05-09
usage_count: 21.7万
author: oswalpalash (via ClawHub)
---

# Ontology

类型化知识图谱，用于结构化智能体记忆与可组合技能。支持创建/查询实体及关联。

A typed vocabulary + constraint system for representing knowledge as a verifiable graph.

## Core Concept

Everything is an entity with a type, properties, and relations to other entities.

```
Entity: { id, type, properties, relations, created, updated }
Relation: { from_id, relation_type, to_id, properties }
```

## When to Use

| Trigger | Action |
|---------|--------|
| "Remember that..." | Create/update entity |
| "What do I know about X?" | Query graph |
| "Link X to Y" | Create relation |
| "Show all tasks for project Z" | Graph traversal |
| "What depends on X?" | Dependency query |

## Core Types

### Agents & People
- `Person: { name, email?, phone?, notes? }`
- `Organization: { name, type?, members[] }`

### Work
- `Project: { name, status, goals[], owner? }`
- `Task: { title, status, due?, priority?, assignee?, blockers[] }`

### Time & Place
- `Event: { title, start, end?, location?, attendees[] }`
- `Location: { name, address?, coordinates? }`

### Information
- `Document: { title, path?, url?, summary? }`
- `Note: { content, tags[], refs[] }`

## Storage

Default: `memory/ontology/graph.jsonl`

```jsonl
{"op":"create","entity":{"id":"p_001","type":"Person","properties":{"name":"Alice"}}}
{"op":"relate","from":"proj_001","rel":"has_owner","to":"p_001"}
```

## Workflows

```bash
# Create Entity
python3 scripts/ontology.py create --type Person --props '{"name":"Alice"}'

# Query
python3 scripts/ontology.py query --type Task --where '{"status":"open"}'

# Link Entities
python3 scripts/ontology.py relate --from proj_001 --rel has_task --to task_001
```

---

## 收集说明

- 收集时间：2026-05-09
- 数据来源：skillhub.cn 详情页
- 原作者：oswalpalash (via ClawHub)
