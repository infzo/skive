---
name: Summarize
source: skillhub.cn
url: https://skillhub.cn/skills/summarize
collected_date: 2026-05-09
usage_count: 43.3万
author: steipete (via ClawHub)
---

# Summarize

使用summarize CLI总结URL或文件（支持网页、PDF、图片、音频、YouTube）。

Fast CLI to summarize URLs, local files, and YouTube links.

## Quick start

```
summarize "https://example.com" --model google/gemini-3-flash-preview
summarize "/path/to/file.pdf" --model google/gemini-3-flash-preview
summarize "https://youtu.be/dQw4w9WgXcQ" --youtube auto
```

## Model + keys

Set the API key for your chosen provider:
- OPENAI_API_KEY
- ANTHROPIC_API_KEY
- XAI_API_KEY
- GEMINI_API_KEY / GOOGLE_GENERATIVE_AI_API_KEY / GOOGLE_API_KEY

Default model is `google/gemini-3-flash-preview` if none is set.

## Useful flags

- `--length short|medium|long|xl|xxl|<chars>`
- `--max-output-tokens <count>`
- `--extract-only`
- `--json`
- `--firecrawl auto|off|always`
- `--youtube auto`

## Config

Optional config file: ~/.summarize/config.json

```json
{ "model": "openai/gpt-5.2" }
```

Optional services:
- FIRECRAWL_API_KEY
- APIFY_API_TOKEN

---

## 收集说明

- 收集时间：2026-05-09
- 数据来源：skillhub.cn 详情页
- 原作者：steipete (via ClawHub)
