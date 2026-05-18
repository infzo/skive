---
name: Gog
source: skillhub.cn
url: https://skillhub.cn/skills/gog
collected_date: 2026-05-09
usage_count: 17.1万
author: steipete (via ClawHub)
---

# Gog

Google Workspace 命令行工具，支持 Gmail、日历、云端硬盘、通讯录、表格和文档。

Use gog for Gmail/Calendar/Drive/Contacts/Sheets/Docs. Requires OAuth setup.

## Setup (once)

```bash
gog auth credentials /path/to/client_secret.json
gog auth add you@gmail.com --services gmail,calendar,drive,contacts,sheets,docs
gog auth list
```

## Common commands

### Gmail
```bash
gog gmail search 'newer_than:7d' --max 10
gog gmail send --to a@b.com --subject "Hi" --body "Hello"
```

### Calendar
```bash
gog calendar events <calendarId> --from <iso> --to <iso>
```

### Drive
```bash
gog drive search "query" --max 10
```

### Contacts
```bash
gog contacts list --max 20
```

### Sheets
```bash
gog sheets get <sheetId> "Tab!A1:D10" --json
gog sheets update <sheetId> "Tab!A1:B2" --values-json '[["A","B"],["1","2"]]'
gog sheets append <sheetId> "Tab!A:C" --values-json '[["x","y","z"]]'
gog sheets clear <sheetId> "Tab!A2:Z"
```

### Docs
```bash
gog docs export <docId> --format txt --out /tmp/doc.txt
gog docs cat <docId>
```

## Notes

- Set `GOG_ACCOUNT=you@gmail.com` to avoid repeating --account
- For scripting, prefer `--json` plus `--no-input`
- Confirm before sending mail or creating events

---

## 收集说明

- 收集时间：2026-05-09
- 数据来源：skillhub.cn 详情页
- 原作者：steipete (via ClawHub)
