---
type: skill
title: GitHub CLI (gh) 命令行使用与 push 实践
domain: development
created: 2026-08-28
last_updated: 2026-08-28
tags: [GitHub, gh, CLI, git-push]
related_pages: ["07_Skills/Git/01.20260522.Git_Commands.md"]
---

# GitHub CLI (gh) 命令行使用与 push 实践

> 来源：`gh --help`、`gh auth status`、`gh repo view` 实测（本机 gh v2.98.0，仓库 yaoyansum/obsidian_cc），GitHub Docs https://cli.github.com/manual/

## 1. 是什么

`gh` 是 GitHub 官方命令行工具，把网页上能做的事搬到终端：

```text
git = 本地版本控制（commit / branch / merge）
gh  = 远程 GitHub 操作（repo / issue / PR / workflow / release / api）
```

两者配合：`git` 管本地，`gh` 管 GitHub。`gh` 并不会替代 `git push`，而是在此之上提供 `gh repo create / gh pr create / gh browse` 等快捷能力。

安装后执行 `gh auth login` 一次认证，后续 `git push` 会自动走 `gh` 存的 token，无需再输密码。

---

## 2. 安装与认证

### 2.1 安装

```bash
# Windows (winget)
winget install --id GitHub.cli

# macOS
brew install gh

# 验证
gh --version   # gh version 2.98.0 (2026-08-20)
```

### 2.2 登录

```bash
gh auth login
# 交互式选择：GitHub.com → HTTPS → Yes → Paste token / Browser 登录

gh auth status          # 查看当前账号与权限
gh auth refresh -s repo,workflow,delete_repo  # 追加 scope
```

本 vault 实测：

```text
✓ Logged in to github.com account yaoyansum (keyring)
  Token scopes: 'delete_repo', 'gist', 'read:org', 'repo', 'workflow'
  Git operations protocol: https
```

### 2.3 常用配置

```bash
gh config set editor "code --wait"
gh config set prompt enabled
gh alias set co "pr checkout"   # 自定义别名
gh alias list
```

---

## 3. 核心命令速查

```bash
gh --help
gh <command> --help     # 查看子命令帮助，例如 gh pr --help
gh help <command>
```

| 分组 | 命令 | 作用 |
|------|------|------|
| 仓库 | `gh repo create/list/view/clone/fork` | 创建/查看/克隆/复刻仓库 |
| Issue/PR | `gh issue/pr create/list/view/close/merge` | 全流程管理 |
| 代码 | `gh browse`, `gh search repos/code/issues` | 浏览器打开、搜索 |
| 发布 | `gh release create/list/view` | 发版 |
| 工作流 | `gh workflow/run/cache` | Actions |
| 通用 | `gh api`, `gh gist`, `gh alias` | 调 API、代码片段 |

---

## 4. 最常用：与 push 相关的完整工作流

### 4.1 Obsidian vault 日常三步走（本仓库已配置 origin）

```bash
# 1. 查看状态
git status
gh repo view --json name,owner --jq "{name:.name, owner:.owner.login}"
# → {"name":"obsidian_cc","owner":"yaoyansum"}

# 2. 暂存 + 提交
git add .                                   # 或 git add 07_Skills/Git/20260828_GitHub_CLI_Gh_Usage.md
git commit -m "skill | 新增 gh CLI 使用笔记"

# 3. 推送（git 负责传输，gh 负责认证）
git push
# 等价于 git push origin main（当前分支 main 已跟踪 origin/main）
```

> 本次操作即执行：
> `git add 07_Skills/Git/20260828_GitHub_CLI_Gh_Usage.md 00_Index/Index.md 01_Log/Log.md && git commit -m "..." && git push`

### 4.2 从零新建仓库并推送（`gh` 一键建仓）

传统方式需先去网页建空仓库，再 `git remote add`。用 `gh` 一条命令完成：

```bash
mkdir my-notes && cd my-notes
git init
git add . && git commit -m "Initial commit"
gh repo create my-notes --public --source=. --remote=origin --push
# --public/--private  可见性
# --source=.          把当前目录作为源码
# --remote=origin     自动 git remote add
# --push              自动 git push
```

等价手动：

```bash
gh repo create my-notes --public
git branch -M main
git remote add origin https://github.com/yaoyansum/my-notes.git
git push -u origin main
```

### 4.3 克隆与 Fork

```bash
gh repo clone yaoyansum/obsidian_cc              # 等价 git clone https://...
gh repo clone yaoyansum/obsidian_cc -- --depth 1 # 浅克隆透传给 git
gh repo fork cli/cli --clone --remote             # fork 并克隆到本地
gh browse                                         # 浏览器打开当前仓库
gh browse --branch main -- commits                # 打开指定分支/页面
```

### 4.4 分支 + PR 工作流（推荐）

```bash
git switch -c feature/gh-notes
# ... 修改文件 ...
git add . && git commit -m "docs: gh notes"
git push -u origin feature/gh-notes

gh pr create --title "新增 gh CLI 笔记" --body "补充 gh auth/repo/pr 全流程" --fill
gh pr view --web        # 浏览器看 PR
gh pr checks            # 看 CI 是否通过
gh pr merge --squash --delete-branch  # 合并后删分支
```

查看/检出他人 PR：

```bash
gh pr list --limit 10
gh pr view 123 --comments
gh pr checkout 123      # 本地检出 PR 分支
gh pr diff 123
```

---

## 5. 其他高频命令

### 5.1 Issue

```bash
gh issue create --title "Bug: GEE 导出失败" --body "复现步骤..." --label bug
gh issue list --search "label:bug state:open" --limit 10
gh issue view 42 --comments
gh issue close 42 --reason completed
```

### 5.2 Release

```bash
gh release create v0.2.0 --title "v0.2.0" --notes "新增 gh 笔记" --generate-notes
gh release list --limit 5
gh release view v0.2.0
```

### 5.3 Search 与 API

```bash
gh search repos "lake carbon remote sensing" --limit 5
gh search issues --repo yaoyansum/obsidian_cc "gh"
gh api repos/yaoyansum/obsidian_cc --jq .stargazers_count
gh api repos/yaoyansum/obsidian_cc/issues --paginate --jq ".[].title"
```

### 5.4 Gist / Workflow

```bash
gh gist create README.md --public --desc "gh cheatsheet"
gh workflow list
gh workflow run "CI" --ref main -f input1=value
gh run list --limit 5
gh run view <run-id> --log
```

---

## 6. `gh` 与 `git push` 的关系辨析

| 操作 | 用谁 | 说明 |
|------|------|------|
| `git add/commit/push/pull/fetch` | `git` | 本地版本控制与传输 |
| `gh repo create/clone/fork` | `gh` | 远程仓库生命周期 |
| `gh pr create/merge` | `gh` | 必须通过 GitHub API 完成，git 做不到 |
| `gh auth login` | `gh` | 写入 keyring 的 token 会被 `git push` 自动使用 |

所以日常在 `obsidian_cc` 中：

```bash
# 只改本地文件 → 仍用 git 三件套
git add . && git commit -m "update" && git push

# 需要建仓/开 PR/发版/查 Actions → 用 gh
gh pr create --fill
gh release create v1.0 --generate-notes
```

---

## 7. 排错

```bash
gh auth status --show-token   # 检查 token 是否过期（慎在共享机使用）
gh auth login --with-token < token.txt  # 非交互登录（CI）
git remote -v                 # 检查 origin 是否为 https://github.com/...
# 若 push 报 403，先刷新 scope
gh auth refresh -h github.com -s repo,workflow

# gh 代理/网络问题
gh config set git_protocol https
env | grep -i proxy
```

---

## 8. 一页 Cheatsheet（可直接背）

```bash
# 认证
gh auth login && gh auth status

# 日常推送
git status && git add . && git commit -m "msg" && git push

# 新仓库
gh repo create <name> --public --source=. --remote=origin --push

# PR
git switch -c feat/x && git push -u origin feat/x
gh pr create --fill && gh pr view --web && gh pr merge --squash --delete-branch

# 查看
gh repo view --web
gh issue list --limit 10
gh pr list --limit 10
gh run list --limit 5
```

---

## 相关页面

- [[01.20260522.Git_Commands|Git 常用命令与技巧]] — 本篇的 `git` 前置基础
- [[01.20260525.OpenCode_Skills|OpenCode 可用技能索引]]
- 官方手册：https://cli.github.com/manual/  和 https://docs.github.com/en/github-cli

## 操作记录

- 2026-08-28 创建本页，覆盖 `gh auth/repo/clone/fork/pr/issue/release/search/api` 全流程，已在 `yaoyansum/obsidian_cc` 实测 `gh version` 与 `gh auth status`。
