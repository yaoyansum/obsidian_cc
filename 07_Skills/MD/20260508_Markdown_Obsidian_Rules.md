# Markdown 与 Obsidian 使用规则

本文件用于规范 Obsidian 知识库中的 Markdown 文档编辑和 Obsidian 功能使用。

---

## 1. Markdown 基本语法规范

### 1.1 标题层级

```markdown
# 一级标题 (H1) - 文档标题，每个文件只用一次
## 二级标题 (H2) - 主要章节
### 三级标题 (H3) - 次要章节
#### 四级标题 (H4) - 小节标题
```

**规则：**
- 每个文件只使用一个 H1 作为文档标题
- 标题层级不超过 4 级
- 标题前留空行，标题后留空行（除非紧接列表）
- 不使用标题进行纯装饰性换行

---

### 1.2 列表格式

```markdown
**无序列表**
- 项目 1
- 项目 2
  - 子项目 (缩进 2 或 4 个空格)
- 项目 3

**有序列表**
1. 第一步
2. 第二步
3. 第三步

**任务列表**
- [ ] 待完成任务
- [x] 已完成任务
```

**规则：**
- 列表符号后加一个空格
- 子项目统一缩进 2 或 4 个空格，全库保持一致
- 任务列表用于 Log.md 待处理事项

---

### 1.3 代码块

````markdown
**行内代码**
使用 `变量名`、`函数名`、`文件名` 表示代码元素。

**代码块**
```python
# 指定语言以获得语法高亮
def function():
    pass
```

**不带语言的代码块**
```
纯文本代码块
```
````

**规则：**
- 行内代码用于文件名、变量名、命令
- 代码块必须标注语言（python、r、bash、yaml 等）
- 代码块前后留空行

---

### 1.4 强调与格式

```markdown
**粗体** - 用于关键词、重要概念
*斜体* - 用于术语、强调
~~删除线~~ - 用于标记过时内容
> 引用块 - 用于重要引文、注意事项
```

**规则：**
- 粗体用于核心概念和关键术语
- 斜体用于外来语、术语首次出现
- 引用块用于重要提示、注意事项、他人引文

---

### 1.5 分割线

```markdown
---
```

**规则：**
- 分割线前后留空行
- 用于分隔大章节，不滥用
- 用三个短横线 `---`，不用其他符号

---

## 2. Obsidian 专用语法

### 2.1 内部链接（Wikilink）

```markdown
**基本链接**
[[页面名称]]

**带别名的链接**
[[页面名称|显示文本]]

**链接到特定标题**
[[页面名称#标题]]

**嵌入页面**
![[页面名称]]

**嵌入特定标题**
![[页面名称#标题]]
```

**规则：**
- 使用 Wikilink 格式 `[[ ]]` 而非 Markdown 标准链接
- 所有内部链接使用完整文件名（含日期前缀）
- 用 `|` 设置显示名，让阅读更简洁
- 示例：`[[20260507_Lake_DIC|Lake DIC]]`

---

### 2.2 标签（Tags）

```markdown
**行内标签**
正文中的 #标签名

**YAML frontmatter 标签**
---
tags: [tag1, tag2, tag3]
---
```

**规则：**
- 使用 YAML frontmatter 中的 tags 字段
- 标签使用 snake_case 命名：`#lake_carbon`、`#remote_sensing`
- 避免过多标签，每个页面 3-5 个核心标签
- 标签用于跨目录检索，不替代目录结构

---

### 2.3 Callout 块

```markdown
> [!note] 标题
> 内容

> [!tip] 提示
> 有用的信息

> [!warning] 警告
> 需要注意的内容

> [!example] 示例
> 示例内容
```

**常用 Callout 类型：**
- `note` - 普通笔记
- `tip` - 有用提示
- `warning` - 警告事项
- `important` - 重要内容
- `example` - 示例
- `question` - 问题
- `quote` - 引用

---

### 2.4 属性（Properties / YAML Frontmatter）

```yaml
---
title: 页面标题
type: knowledge|project|data_doc|writing
created: 2026-05-07
last_updated: 2026-05-07
tags: [tag1, tag2]
related: []
status: active|paused|finished
---
```

**规则：**
- 所有页面必须包含 YAML frontmatter
- 必填字段：`title`、`type`、`created`、`last_updated`
- 日期格式统一使用 `YYYY-MM-DD`
- 不同类型页面使用对应的 type 值

---

## 3. 文件命名规范

### 3.1 总体规则

```text
所有 Markdown 页面 = YYYYMMDD_英文主题名.md
```

**核心原则：**
1. 所有用户自建 Markdown 页面必须加日期前缀
2. 日期统一使用 `YYYYMMDD` 格式
3. 日期后用下划线 `_` 连接主题名
4. 文件名主体优先使用英文
5. 文件名表达主题，不写成一句话

---

### 3.2 各类页面命名

```text
知识页：YYYYMMDD_Topic.md
项目页：YYYYMMDD_Object_Task.md
数据页：YYYYMMDD_Object_Dataset.md
写作页：YYYYMMDD_Topic_Section.md
模板页：YYYYMMDD_Topic_Template.md
日记页：YYYYMMDD_Daily.md
```

---

### 3.3 禁止事项

- 不使用空格、中文标点
- 不使用 `: ? * | " < > / \`
- 不使用 `final`、`new`、`latest`、`最终版`
- 不使用 `2026-05-07` 或 `2026_05_07` 格式

---

## 4. 文档结构规范

### 4.1 页面模板结构

```markdown
---
title: 页面标题
type: knowledge
created: YYYY-MM-DD
last_updated: YYYY-MM-DD
tags: []
---

# 页面标题

## 主要内容章节

## 相关页面

## 来源与引用

## 修改记录
```

---

### 4.2 必须包含的章节

| 页面类型 | 必须章节 |
|---------|---------|
| 知识页 | 定义、核心机制、影响因素、应用场景、来源 |
| 项目页 | 项目目标、当前进展、下一步计划、操作记录 |
| 数据页 | 数据路径、数据结构、变量说明、时间范围、空间范围 |
| 写作页 | 写作目标、当前版本、结构安排、正文草稿 |

---

## 5. 链接与引用规范

### 5.1 内部链接

```markdown
- [[20260507_Lake_DIC|Lake DIC]]
- [[20260507_Runoff_Dilution|径流稀释机制]]
- [[04_Knowledge_Base/Lake_Carbon/DIC|DIC 知识页]]
```

---

### 5.2 外部链接

```markdown
[链接文本](https://example.com)
```

**规则：**
- 外部链接使用标准 Markdown 格式
- 重要外部链接可添加到页面底部"来源"部分
- 学术引用优先使用 DOI 链接

---

### 5.3 来源引用

```markdown
**文献引用**
> 作者 (年份) - 论文标题, 期刊名

**数据来源**
> 数据集名称, 来源机构, 时间范围

**网页来源**
> 网站名称 - 页面标题, URL, 访问日期
```

---

## 6. 日志与更新规范

### 6.1 Log.md 格式

```markdown
## [YYYY-MM-DD] 操作类型 | 简要描述 | 详细说明
```

**操作类型：**
- `index` - 更新索引
- `project` - 项目推进
- `knowledge` - 知识整理
- `writing` - 写作修改
- `data-doc` - 数据说明
- `code-debug` - 代码问题
- `lint` - 知识库检查

---

### 6.2 修改记录

在页面末尾维护修改记录：

```markdown
## 修改记录

- [2026-05-07] 创建初始版本
- [2026-05-08] 补充核心机制章节
- [2026-05-09] 更新来源引用
```

---

## 7. 内容组织最佳实践

### 7.1 信息分层

```text
过程记录 → 01_Log/Log.md
长期知识 → 04_Knowledge_Base/
具体任务 → 03_Projects/
数据说明 → 08_Data_Documentation/
正式写作 → 09_Writing/
个人反思 → 02_Diary/
原始材料 → 99_Raw_Data/
```

---

### 7.2 知识沉淀流程

```text
1. 临时记录 → Log.md 或 Raw_Data
2. 整理归纳 → 对应知识页/数据页/写作页
3. 建立链接 → 更新 Index.md 和相关页面
4. 定期检查 → Lint 健检
```

---

### 7.3 避免信息孤岛

- 每个重要页面必须在 Index.md 中有入口
- 使用 `[[ ]]` 建立页面间关联
- 定期检查死链和孤立页面
- 重复内容及时合并

---

## 8. 协作与版本管理

### 8.1 Git 提交规范

```text
类型: 简短描述

类型包括：
- feat: 新增功能/页面
- fix: 修复错误
- docs: 文档更新
- refactor: 重构/整理
- lint: 知识库检查
```

---

### 8.2 版本控制

- 不在文件名中标注版本号
- 版本变化记录在页面"修改记录"中
- 重大版本保留快照：`YYYYMMDD_Topic_Snapshot.md`
- 使用 Git 管理历史版本

---

## 9. 常见错误与避免

### 9.1 命名错误

```text
❌ 关于湖泊DOC的文献总结.md
❌ 2026-05-07_Lake_DIC.md
❌ DIC_final_new.md

✅ 20260507_DOC_Literature_Notes.md
✅ 20260507_Lake_DIC.md
✅ 20260507_DIC.md
```

---

### 9.2 结构错误

```text
❌ 每天新建日志文件
❌ 创建多个索引文件
❌ 在 Raw_Data 中长期存放整理后的内容

✅ 使用唯一 Log.md
✅ 使用唯一 Index.md
✅ 及时迁移到对应目录
```

---

### 9.3 链接错误

```text
❌ [[Lake_DIC]] (无日期前缀)
❌ [[20260507_Lake_DIC|Lake_DIC]] (显示名不简洁)

✅ [[20260507_Lake_DIC|Lake DIC]]
✅ [[04_Knowledge_Base/Lake_Carbon/DIC|DIC]]
```

---

## 10. 快速参考卡片

### 10.1 新建页面检查清单

- [ ] 文件名格式：`YYYYMMDD_英文主题.md`
- [ ] 包含 YAML frontmatter
- [ ] 包含一级标题
- [ ] 建立与其他页面的链接
- [ ] 更新 Index.md（如为重要页面）
- [ ] 追加 Log.md 记录

---

### 10.2 日常操作检查清单

- [ ] 打开 Index.md 确认当前任务
- [ ] 操作过程记录到 Log.md
- [ ] 稳定知识迁移到 Knowledge_Base
- [ ] 数据说明迁移到 Data_Documentation
- [ ] 正式文字放入 Writing
- [ ] 原始材料放入 Raw_Data

---

### 10.3 页面类型速查

| 类型 | 目录 | 文件名格式 | type 值 |
|-----|------|-----------|---------|
| 知识页 | 04_Knowledge_Base/ | YYYYMMDD_Topic.md | knowledge |
| 项目页 | 03_Projects/ | YYYYMMDD_Object_Task.md | project |
| 数据页 | 08_Data_Documentation/ | YYYYMMDD_Dataset.md | data_doc |
| 写作页 | 09_Writing/ | YYYYMMDD_Topic_Section.md | writing |
| 模板页 | 10_Templates/ | YYYYMMDD_Topic_Template.md | template |

---

## 相关页面

- [[CLAUDE|CLAUDE.md - 知识库维护指南]]
- [[Index|Index.md - 总索引]]
- [[Log|Log.md - 总日志]]

---

## 修改记录

- [2026-05-08] 创建初始版本，整合 Markdown 和 Obsidian 使用规范
