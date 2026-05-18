---
name: collect-skills
description: 从 ClawHub API 收集热门 Skill 定义，支持并行收集和增量更新
trigger: /collect-skills
---

## 目标

从 ClawHub（skillhub.cn 的数据源）通过 API 收集当前热门、使用量高的 Skill，存储到项目中供后续分析和学习。

## 输入

- 无特定前置条件
- 可选：用户指定收集数量（默认 10 个）
- 可选：用户指定排序方式（默认 downloads）

## API 端点

Base URL: `https://clawhub.ai`

| 端点 | 方法 | 说明 |
|------|------|------|
| `/api/v1/skills` | GET | 列出 skills，支持排序和分页 |
| `/api/v1/skills/{slug}` | GET | 获取单个 skill 详情 |
| `/api/v1/skills/{slug}/file` | GET | 获取 skill 文件内容 |

### 请求参数

**GET /api/v1/skills**
- `limit`: 数量限制（1-200）
- `sort`: 排序方式 - `downloads`（下载量）、`trending`（7天趋势）、`stars`（收藏）、`createdAt`（最新）
- `cursor`: 分页游标

**GET /api/v1/skills/{slug}/file**
- `path`: 文件路径（如 `SKILL.md`）
- `version`: 版本号（可选，默认最新）

### 速率限制

- 匿名读取：600次/分钟/IP
- 响应头包含 `Retry-After`，超限时需等待

## 执行步骤

### 1. 检查已有收集（增量）

```
读取 data/collected/index.md
解析已收集的 skill slug 列表
存储到变量 existing_slugs
```

### 2. 获取热门 Skill 列表

```bash
curl -s "https://clawhub.ai/api/v1/skills?sort=downloads&limit=15" | \
  jq '.items[] | {slug, displayName, summary, stats}'
```

解析响应，提取前 N 个 Skill（排除已存在的）：
```
skill_list = 从响应中提取
skill_list = skill_list[0:N]  # 取前 N 个
skill_list = [s for s in skill_list if s.slug not in existing_slugs]  # 增量过滤
```

### 3. 并行收集 Skill 详情

将 Skill 列表分成 3-4 组，并行启动 Agent 收集：

```
组1: skill_list[0:3]
组2: skill_list[3:6]
组3: skill_list[6:9]
...
```

**每个 Agent 执行以下步骤：**

#### 3.1 获取 Skill 元数据

```bash
curl -s "https://clawhub.ai/api/v1/skills/{slug}" | jq .
```

提取字段：
- `slug`: 唯一标识
- `displayName`: 显示名称
- `summary`: 简介
- `owner.handle`: 作者
- `stats`: 统计数据
- `latestVersion.version`: 版本号

#### 3.2 获取 Skill 定义文件

```bash
curl -s "https://clawhub.ai/api/v1/skills/{slug}/file?path=SKILL.md"
```

如果 SKILL.md 不存在，尝试其他常见文件：
- `skill.md`
- `README.md`
- `{skill-name}.md`

#### 3.3 存储 Skill 文件

文件路径：`data/collected/{sanitized_slug}.md`

文件格式：
```markdown
---
name: {displayName}
source: clawhub.ai
url: https://clawhub.ai/{slug}
collected_date: {YYYY-MM-DD}
usage_count: {stats.downloads}
author: {owner.handle}
version: {latestVersion.version}
---

{Skill 定义内容}
```

### 4. 等待所有 Agent 完成

```
收集所有 Agent 的结果
汇总成功/失败列表
```

### 5. 自动生成索引

扫描 `data/collected/` 目录，自动生成 `index.md`：

```bash
ls data/collected/*.md | grep -v index.md | while read f; do
  name=$(basename "$f" .md)
  # 提取 frontmatter 信息
done
```

索引格式：
```markdown
---
title: 已收集 Skills 索引
updated: {YYYY-MM-DD}
---

| 名称 | 来源 | 使用量 | 收集日期 | 文件 |
|------|------|--------|----------|------|
| {displayName} | clawhub.ai | {count} | {date} | [{name}.md]({name}.md) |
...

## 统计
- 总数: X 个 Skill
- 最新收集: {date}
```

## 输出

- `data/collected/*.md`：收集的 Skill 文件
- `data/collected/index.md`：自动生成的索引

## 错误处理

### API 限流 (429)

```bash
# 检查响应头
curl -I "https://clawhub.ai/api/v1/skills"
# 等待 Retry-After 秒数后重试
sleep $retry_after
```

### Skill 文件不存在

1. 尝试备用文件名
2. 如果都失败，记录为 "内容获取失败"
3. 继续处理下一个

### 网络错误

1. 单个请求重试最多 3 次
2. 每次间隔 2 秒
3. 如果仍失败，跳过当前 Skill

## 优化特性

### 并行收集

使用 Agent 工具并行处理多个 Skill，预计节省 50-60% 时间：

| Skill 数量 | 串行耗时 | 并行耗时 |
|------------|----------|----------|
| 10 | ~25s | ~10s |
| 20 | ~50s | ~20s |

### 增量更新

每次收集前检查 index.md，跳过已存在的 Skill，避免重复工作。

### API 优先

使用 REST API 替代浏览器自动化：
- 更快：单次请求 < 500ms
- 更稳定：无页面渲染依赖
- 更易解析：JSON 响应直接处理

## 限制条件

- **数量限制**：默认最多收集 10 个热门 Skill
- **速率限制**：遵守 ClawHub API 限流规则
- **存储限制**：跳过已收集的 Skill（通过 slug 比对）

## 注意事项

- 遵守 ClawHub 的使用条款和速率限制
- 请求时设置合理的 User-Agent
- 保留原始内容的完整性
- 标注来源 URL，便于后续追溯
- 收集后人工复核，确认内容准确性
