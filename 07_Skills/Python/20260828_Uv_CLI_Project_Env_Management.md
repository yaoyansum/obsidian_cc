---
type: skill
title: uv 命令行使用与项目/环境管理技巧
domain: python
created: 2026-08-28
last_updated: 2026-08-28
tags: [uv, Python, 包管理, 虚拟环境, 项目管理]
related_pages: ["07_Skills/Git/01.20260522.Git_Commands.md", "07_Skills/Git/20260828_GitHub_CLI_Gh_Usage.md"]
---

# uv 命令行使用与项目/环境管理技巧

> 来源：本机 `uv 0.11.21` 实测 + `uv --help` / `uv help <command>` + 官方文档 https://docs.astral.sh/uv/
> 适用：科研 Python 项目（湖泊碳循环 / 水质遥感 / GLM-AED / GEE 数据处理）的环境隔离与复现

## 1. uv 是什么

`uv` 是 Astral（Ruff 团队）用 Rust 写的**极速 Python 包管理器**，单一二进制替代 `pip + pip-tools + virtualenv + pyenv + poetry/pdm` 的大部分功能。

```text
速度：比 pip 快 10-100x（并行解析 + 全局缓存）
定位：
  uv python  → 替代 pyenv（Python 版本管理）
  uv venv    → 替代 virtualenv / conda create
  uv pip     → 兼容 pip 接口（快 10x）
  uv add/sync/lock → 替代 poetry / pdm（项目管理）
  uv tool    → 替代 pipx（全局工具）
  uv run     → 替代 python main.py（自动进环境）
```

**核心优势（科研场景）：**

- 一个 `pyproject.toml + uv.lock` 锁死全部依赖，换机器 `uv sync` 一键复现
- 无需手动 `activate`，`uv run` 自动识别 `.venv`
- 自带 Python 安装，不再依赖系统 `python3.12`
- 工作空间（workspace）支持多子项目（如 `Lake_DOC` / `Lake_DIC` 共用环境）

---

## 2. 安装与升级

```bash
# Windows (winget / pip / 独立安装)
winget install --id=astral-sh.uv
# 或
pip install uv
# 或官方脚本 (PowerShell)
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"

# macOS / Linux
curl -LsSf https://astral.sh/uv/install.sh | sh
brew install uv

# 验证
uv --version           # uv 0.11.21
uv self update         # 自升级
uv --help              # 总览
uv help <command>      # 子命令帮助，如 uv help sync
```

Shell 补全：

```bash
uv generate-shell-completion bash >> ~/.bashrc
uv generate-shell-completion powershell >> $PROFILE
# 或 zsh / fish
```

---

## 3. Python 版本管理 (`uv python`)

无需再装 pyenv / 手动下载 Python。

```bash
# 查看可用/已安装版本
uv python list
uv python list --only-installed
uv python find 3.12          # 查找解释器路径

# 安装指定版本（自动下载，无需管理员）
uv python install 3.12
uv python install 3.11 3.12   # 多版本
uv python install cpython@3.12.3
uv python install pypy@3.10

# 卸载 / 升级
uv python uninstall 3.11
uv python upgrade            # 升级所有已装版本

# 固定项目 Python 版本（生成 .python-version）
uv python pin 3.12           # 写入 .python-version = "3.12"
cat .python-version          # obsidian_cc 可用此固定

# 临时指定
uv run --python 3.12 python --version
uv venv --python 3.11 .venv311
```

> 原理：`uv` 托管的 Python 在 `uv python dir`（Windows: `%LOCALAPPDATA%\uv\python`），`--managed-python` / `--no-managed-python` 控制是否使用。

---

## 4. 项目管理（推荐新项目用此流程）

这是 `uv` 最重要的能力：以 `pyproject.toml + uv.lock` 为中心的声明式管理。

### 4.1 初始化项目 (`uv init`)

```bash
# 在空目录初始化（默认 app 类型，不打包）
mkdir lake-doc-analysis && cd lake-doc-analysis
uv init                          # 生成 pyproject.toml + README + main.py + .python-version
uv init --name lake-doc          # 指定包名
uv init --lib                    # 库类型（带 src/ 布局 + build-system）
uv init --app --package          # 可发布的 app（带 [project.scripts]）
uv init --bare                   # 仅生成 pyproject.toml
uv init --python 3.12            # 指定 Python 版本

# 在已有项目中初始化（已存在 pyproject.toml 会报错）
# 若父目录已有项目，默认加入 workspace 成员，用 --no-workspace 禁用
```

生成的 `pyproject.toml` 示例：

```toml
[project]
name = "lake-doc-analysis"
version = "0.1.0"
description = "Lake DOC global change"
requires-python = ">=3.12"
dependencies = ["numpy", "xarray", "pandas"]

[dependency-groups]
dev = ["pytest", "ruff"]

[tool.uv]
default-groups = ["dev"]
```

### 4.2 添加 / 移除依赖 (`uv add / remove`)

```bash
uv add numpy                     # 添加到 [project].dependencies
uv add "pandas>=2.0"             # 带版本约束
uv add ruff --dev                # 添加到 dev 组（等价 --group dev）
uv add --group test pytest
uv add --optional viz matplotlib # 可选依赖 extra
uv add -r requirements.txt       # 从文件批量添加

# 移除
uv remove pandas
uv remove --group dev ruff

# 查看依赖树
uv tree
uv tree --depth 2
uv tree --outdated
```

### 4.3 锁定与同步 (`uv lock / sync`)

```bash
uv lock                          # 解析并生成/更新 uv.lock
uv lock --upgrade                # 升级全部依赖到最新兼容版本
uv lock --upgrade-package numpy  # 仅升级单个
uv lock --check                  # CI 中检查锁文件是否过期（不等价于 --locked）
uv lock --dry-run                # 预览变更，不写盘

uv sync                          # 按 uv.lock 安装到 .venv（无 .venv 则新建）
uv sync --frozen                 # 不更新锁文件，直接按锁安装（CI 推荐）
uv sync --locked                 # 锁过期则报错（比 --frozen 更严格）
uv sync --extra viz              # 安装可选依赖
uv sync --all-extras
uv sync --group test
uv sync --no-dev                 # 不装 dev 组
uv sync --inexact                # 保留环境中多余的包（默认会删）

# 导出为 requirements 格式（给不用 uv 的协作者）
uv export --format requirements-txt -o requirements.txt
uv export --format requirements-txt --no-dev -o requirements-prod.txt
```

### 4.4 运行 (`uv run`)

无需 `activate`，自动同步环境后执行。

```bash
uv run python main.py            # 在项目环境中运行
uv run -- python -c "import numpy; print(numpy.__version__)"
uv run --with pandas python script.py  # 临时加依赖（不写 pyproject.toml）
uv run --extra viz python plot.py
uv run ruff check .              # 运行已安装工具
uv run --module pytest           # 等价 python -m pytest
uv run jupyter lab               # 若已 add jupyter

# 执行独立脚本（PEP 723 内联元数据）
uv run script.py                 # 脚本顶部可写 # /// script ... dependencies = [...]
uv run https://example.com/script.py  # 直接运行远程脚本
```

### 4.5 构建与发布 (`uv build / publish`)

```bash
uv build                         # 构建 sdist + wheel 到 dist/
uv build --wheel
uv publish                       # 上传到 PyPI
uv publish --index testpypi
```

### 4.6 版本管理

```bash
uv version                       # 查看当前版本
uv version --bump patch          # 0.1.0 → 0.1.1
uv version --bump minor
uv version --bump major
uv version 0.2.0                 # 设为指定版本
```

---

## 5. 环境管理（虚拟环境）

### 5.1 创建与原理 (`uv venv`)

```bash
uv venv                          # 默认 .venv（若在项目中）
uv venv .venv311 --python 3.11
uv venv --seed                   # 带 pip/setuptools/wheel（Python<3.12）
uv venv --clear                  # 清空重建
uv venv /path/to/env --no-project  # 不关联项目

# 环境变量改名（项目根目录生效）
$env:UV_PROJECT_ENVIRONMENT=".venv-dev"  # Windows
UV_PROJECT_ENVIRONMENT=.venv-dev uv sync # Linux/macOS
```

> 关键：`uv` 执行时会自动向上查找 `.venv` 或已激活的环境，**无需 `activate`**。
> 但若需手动激活（调试）：
>
> ```bash
> .venv\Scripts\activate          # Windows PowerShell
> source .venv/bin/activate       # Linux/macOS
> ```

### 5.2 pip 兼容接口 (`uv pip`)

在**已有环境**（或非项目）中当 `pip` 的极速替代，用于兼容旧工作流（conda 导出、requirements.txt）。

```bash
# 安装（比 pip 快 10x）
uv pip install numpy pandas
uv pip install -r requirements.txt
uv pip install -e .              # 可编辑安装
uv pip install "xarray[io]>=2024.0"

# 编译与同步（pip-tools 替代）
uv pip compile requirements.in -o requirements.txt
uv pip sync requirements.txt     # 精确同步（删多余包）

# 查询
uv pip list
uv pip freeze                    # 导出
uv pip show numpy
uv pip tree
uv pip check                     # 检查依赖冲突
uv pip uninstall numpy

# 指定环境
uv pip install numpy --python .venv311\Scripts\python.exe
```

### 5.3 工具管理 (`uv tool`)

替代 `pipx`，全局安装命令行工具（black, ruff, jupyter 等），不污染项目环境。

```bash
uv tool install ruff             # 全局安装
uv tool install black --with jupyter  # 带额外依赖
uv tool list
uv tool upgrade ruff
uv tool uninstall ruff
uv tool run ruff -- check .      # 不安装直接运行（等价 uvx）
uvx ruff check .                 # 简写（uv tool run 的别名）
uv tool dir                      # 工具安装目录
uv tool update-shell             # 把工具目录加入 PATH
```

---

## 6. 工作空间（Workspace，多项目协同）

适合本知识库这类“多个子项目共享依赖”的场景：

```toml
# 根 pyproject.toml
[tool.uv.workspace]
members = ["03_Projects/*", "04_Knowledge_Base/*"]
exclude = ["99_Raw_Data"]

# 子项目 pyproject.toml
[tool.uv.sources]
lake-common = { workspace = true }
```

```bash
uv sync                          # 根目录一键同步所有成员
uv run --project 03_Projects/Lake_DOC python main.py
uv tree                          # 查看 workspace 整体依赖
uv workspace list
```

---

## 7. 配置与镜像

### 7.1 配置文件

优先级：`pyproject.toml [tool.uv]` > `uv.toml` > 环境变量 > 默认值

```toml
# pyproject.toml
[tool.uv]
default-groups = ["dev"]         # 默认安装的组
managed = true

[[tool.uv.index]]
name = "tsinghua"
url = "https://pypi.tuna.tsinghua.edu.cn/simple"
default = true

[[tool.uv.index]]
name = "aliyun"
url = "https://mirrors.aliyun.com/pypi/simple/"
explicit = true                  # 仅显式引用时使用

[tool.uv.sources]
my-private-pkg = { index = "aliyun" }
```

```toml
# uv.toml（用户级 ~/.config/uv/uv.toml 或项目级）
[install]
index-url = "https://pypi.tuna.tsinghua.edu.cn/simple"
```

### 7.2 常用镜像（科研内网推荐）

```bash
# 临时指定
uv add numpy --index https://pypi.tuna.tsinghua.edu.cn/simple
uv pip install numpy --index-url https://pypi.tuna.tsinghua.edu.cn/simple
uv sync --index https://mirrors.aliyun.com/pypi/simple/

# 环境变量
$env:UV_INDEX_URL="https://pypi.tuna.tsinghua.edu.cn/simple"  # Windows
export UV_INDEX_URL=https://pypi.tuna.tsinghua.edu.cn/simple  # Linux

# 配置文件永久生效见 7.1
```

### 7.3 缓存

```bash
uv cache dir                     # 查看缓存目录
uv cache clean                   # 清空
uv cache prune --ci              # CI 友好清理
uv --no-cache sync               # 本次不使用缓存
```

---

## 8. 科研项目实战技巧

### 8.1 新开一个湖泊分析项目（推荐模板）

```bash
mkdir Lake_DIC_2026 && cd Lake_DIC_2026
uv init --python 3.12 --lib --name lake-dic
uv add numpy pandas xarray netCDF4 matplotlib cartopy scikit-learn
uv add --group dev pytest ruff jupyter ipykernel
uv python pin 3.12
uv sync
uv run python -m ipykernel install --user --name lake-dic --display-name "Lake DIC (uv)"
# 后续在 VS Code / Jupyter 选择该 kernel
```

### 8.2 从 conda / pip 旧项目迁移

```bash
# 导出旧环境
conda env export > environment.yml
pip freeze > requirements.txt

# 新建 uv 项目并导入
uv init --bare
uv add -r requirements.txt       # 自动解析并写入 pyproject.toml
uv sync
# 或 pip 兼容模式（不改 pyproject.toml）
uv venv && uv pip install -r requirements.txt
```

### 8.3 可复现性保障（论文投稿前必做）

```bash
uv lock --check                  # 确保锁文件最新（CI 中）
uv sync --frozen                 # 严格按锁安装
uv tree > env_snapshot.txt       # 快照留档
uv export -o requirements_freeze.txt  # 给审稿人/协作者
git add pyproject.toml uv.lock .python-version
```

### 8.4 多 Python 版本测试

```bash
uv python install 3.10 3.11 3.12
for v in 3.10 3.11 3.12; do uv run --python $v pytest; done
# 或 tox / nox 结合 uv
```

### 8.5 常见坑位

| 问题 | 对策 |
|------|------|
| `uv sync` 删掉了手动 `pip install` 的包 | 默认 exact sync，用 `uv sync --inexact` 或把包 `uv add` 进项目 |
| 内网无法下载 Python | `uv python install --no-python-downloads` 或 `UV_PYTHON_DOWNLOADS=never` 并指定系统 Python |
| 锁冲突 / 解析慢 | `uv lock --upgrade` 重解析，`uv tree` 定位冲突，`[tool.uv.sources]` 覆盖源 |
| `.venv` 不在项目根 | `uv` 会向上查找，检查是否在父目录误建了 `.venv` |
| 与 conda 混用 PATH | 优先用 `uv python pin` + `uv venv`，`conda deactivate` 后再 `uv sync` |

---

## 9. 一页 Cheatsheet

```bash
# 安装与自检
uv --version && uv self update

# Python
uv python install 3.12 && uv python pin 3.12 && uv python list

# 项目从零到一
uv init --python 3.12
uv add numpy pandas xarray
uv add --dev ruff pytest
uv sync && uv tree

# 日常
uv add "pandas>=2.0" && uv remove old-pkg
uv lock --upgrade && uv sync --frozen
uv run python main.py
uv run --with pycowsay -- pycowsay "hello"

# 环境
uv venv --python 3.11 .venv311
uv pip list && uv pip show numpy

# 工具
uv tool install ruff && uvx black --check .

# 诊断
uv cache dir && uv pip check && uv tree --outdated
```

---

## 10. 与 conda / pip / poetry 对照

| 需求 | conda | pip/poetry | uv |
|------|-------|------------|----|
| 装 Python | `conda create -n env python=3.12` | `pyenv install 3.12` | `uv python install 3.12` |
| 建环境 | `conda create -n lake` | `python -m venv .venv` | `uv venv` |
| 装包 | `conda install numpy` | `pip install numpy` / `poetry add numpy` | `uv add numpy` / `uv pip install numpy` |
| 锁定 | `conda env export` | `pip freeze` / `poetry.lock` | `uv lock` → `uv.lock` |
| 复现 | `conda env create -f env.yml` | `pip install -r req.txt` | `uv sync --frozen` |
| 运行 | `conda activate lake` | `source .venv/bin/activate` | `uv run python ...`（免激活）|
| 全局工具 | `conda install -n base` | `pipx install` | `uv tool install` |

> 建议：新项目直接用 `uv`；旧 conda 项目可渐进迁移（`uv pip` 兼容期），最终统一 `pyproject.toml + uv.lock`。

---

## 相关页面

- [[07_Skills/Git/01.20260522.Git_Commands|Git 常用命令与技巧]] — `uv` 项目配合 `git push` 的版本控制
- [[07_Skills/Git/20260828_GitHub_CLI_Gh_Usage|GitHub CLI (gh) 使用与 push 实践]] — `gh repo/pr/release` 远程协作
- [[04_Knowledge_Base/Modeling/Machine_Learning|Machine_Learning]] — 机器学习项目依赖管理
- [[08_Data_Documentation/Remote_Sensing_Dataset|Remote_Sensing_Dataset]] — 遥感数据处理环境

## 操作记录

- 2026-08-28 创建本页，基于 `uv 0.11.21` 实测 `uv help` 全量命令，覆盖 `python/venv/pip/tool/init/add/sync/lock/run/build/publish/workspace/cache` 与科研实战技巧。
