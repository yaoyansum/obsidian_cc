---
type: skill
title: Git 常用命令与技巧
domain: development
created: 2026-05-22
last_updated: 2026-05-22
---

# Git 常用命令与技巧

## 基础工作流

```bash
# 查看状态
git status

# 暂存文件
git add <file>          # 单个文件
git add .               # 所有变更
git add -p              # 交互式分段暂存

# 提交
git commit -m "message"
git commit -am "mesg"   # add + commit（仅跟踪过的文件）

# 推送
git push                # 推送到默认远程
git push origin <branch>

# 拉取
git pull                # fetch + merge
git pull --rebase       # fetch + rebase

# 查看历史
git log --oneline --graph -10
git log --oneline --all --graph
git log --author="name" --since="2026-01-01"
```

---

## 分支管理

```bash
# 查看分支
git branch              # 本地
git branch -a           # 全部（含远程）
git branch -vv          # 显示跟踪关系

# 创建与切换
git branch <name>       # 创建
git switch <name>       # 切换（新版）
git checkout -b <name>  # 创建并切换

# 合并
git switch main
git merge <branch>

# 变基
git switch <feature>
git rebase main         # feature 变基到 main

# 删除
git branch -d <name>    # 已合并则删除
git branch -D <name>    # 强制删除
git push origin --delete <name>  # 删除远程

# 重命名
git branch -m <old> <new>
```

---

## 撤销与修改

```bash
# 工作区撤销
git restore <file>              # 丢弃未暂存修改
git checkout -- <file>          # 旧写法

# 暂存区撤销
git restore --staged <file>     # 取消暂存
git reset HEAD <file>           # 旧写法

# 提交修复
git commit --amend              # 修改最近提交信息或内容

# 回退
git reset --soft HEAD~1         # 撤销提交，保留内容
git reset --mixed HEAD~1        # 撤销提交 + 取消暂存
git reset --hard HEAD~1         # 彻底丢弃（慎用）

# 回滚（安全）
git revert HEAD                 # 生成反向提交
git revert <commit_hash>

# 暂存当前工作
git stash                       # 保存现场
git stash list                  # 查看暂存列表
git stash pop                   # 恢复并删除
git stash apply stash@{0}       # 恢复不删除
git stash drop stash@{0}        # 删除指定
```

---

## 团队协作

```bash
# 远程仓库
git remote -v
git remote add origin <url>
git remote set-url origin <url>

# 获取远程分支
git fetch
git fetch origin <branch>
git fetch --prune               # 清理已删除远程分支

# 本地跟踪远程分支
git switch -c <local> origin/<remote>
git branch -u origin/<remote>   # 设置上游

# 标签
git tag v1.0
git tag -a v1.0 -m "release"
git push origin --tags
git tag -d v1.0
git push origin :refs/tags/v1.0
```

---

## 常用技巧

### 查看差异

```bash
git diff                     # 工作区 vs 暂存区
git diff --staged            # 暂存区 vs 上次提交
git diff HEAD                # 工作区 vs 上次提交
git diff <commit1>..<commit2>
git diff --stat              # 仅显示文件名
```

### 搜索

```bash
git log --grep="keyword"     # 按提交信息搜索
git log -S "string"          # 按代码内容搜索
git grep "pattern"           # 在工作树搜索
git blame <file>             # 每行最后修改
```

### 清理

```bash
git clean -n                 # 预览要删除的未跟踪文件
git clean -fd                # 删除未跟踪文件 + 目录
```

### 配置

```bash
git config --global user.name "name"
git config --global user.email "email"
git config --global core.editor "code --wait"
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.lg "log --oneline --graph --all -20"
git config --global pull.rebase true
```

### .gitignore 常见模式

```
.DS_Store
*.pyc
__pycache__/
.env
data/raw/*.nc
*.log
```

---

## 科研项目常见场景

### 开始一个新项目

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin <url>
git push -u origin main
```

### 开新分支做实验

```bash
git switch -c experiment   # 开实验分支
# ... 做完实验，对比结果
git switch main            # 回到主分支
# 如果好就合并：
git merge experiment
git branch -d experiment
# 如果不好直接删：
git branch -D experiment
```

### 紧急修复中途保存

```bash
git stash                  # 保存当前未提交的工作
git switch main
# 修 bug → commit → push
git switch <feature>
git stash pop              # 恢复现场
```

### 撤销错误的 commit（未推送）

```bash
git reset --soft HEAD~1    # 保留代码，重新提交
```

### 撤销已推送的 commit

```bash
git revert HEAD            # 安全：生成反向提交
git push
```

---

## 完整工作流示例

```bash
# 克隆或初始化
git clone <url>
cd <repo>
git switch -c feature/doc-processing

# 日常循环
git status
git add <changed_files>
git commit -m "处理 DOC netCDF 数据提取"
git fetch origin
git rebase origin/main     # 同步最新
git push -u origin feature/doc-processing

# 合并回 main
git switch main
git pull
git merge feature/doc-processing
git push
```

---

## 相关页面

- [[00_Index/Index|Index]]
- [[01_Log/Log|Log]]
