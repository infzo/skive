---
name: Github
source: skillhub.cn
url: https://skillhub.cn/skills/github
collected_date: 2026-05-09
usage_count: 27.6万
author: steipete (via ClawHub)
---

# Github

使用 `gh` CLI 与 GitHub 交互，通过 `gh issue`、`gh pr`、`gh run` 和 `gh api` 管理议题、PR、CI 运行及高级查询。

Use the gh CLI to interact with GitHub. Always specify --repo owner/repo when not in a git directory, or use URLs directly.

## Pull Requests

Check CI status on a PR:
```
gh pr checks 55 --repo owner/repo
```

List recent workflow runs:
```
gh run list --repo owner/repo --limit 10
```

View a run and see which steps failed:
```
gh run view <run-id> --repo owner/repo
```

View logs for failed steps only:
```
gh run view <run-id> --repo owner/repo --log-failed
```

## API for Advanced Queries

The `gh api` command is useful for accessing data not available through other subcommands.

Get PR with specific fields:
```
gh api repos/owner/repo/pulls/55 --jq '.title, .state, .user.login'
```

## JSON Output

Most commands support `--json` for structured output. You can use `--jq` to filter:
```
gh issue list --repo owner/repo --json number,title --jq '.[] | "\(.number): \(.title)"'
```

---

## 收集说明

- 收集时间：2026-05-09
- 数据来源：skillhub.cn 详情页
- 原作者：steipete (via ClawHub)
