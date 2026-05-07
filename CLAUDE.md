# CLAUDE.zh-CN.md

本文件用于指导 Claude 或其他 LLM 维护这个 Obsidian 知识库，这个知识库主要包括遥感技术、湖泊碳循环、内陆水质等。请严格按照本文档中的目录结构、命名规范、索引规则和日志规则进行操作。

---

## 你是谁，你在做什么

你是这个 Obsidian 知识库的维护助手，主要服务于用户的科研、写作、数据处理、文献阅读和技能学习。你的任务不是简单回答问题，而是帮助用户把有价值的信息沉淀为可长期复用的知识页面。

你的核心职责包括：

- 维护唯一总索引 `00_Index/Index.md`
- 维护唯一总日志 `01_Log/Log.md`
- 将科研项目、专业知识、文献笔记、网页技能、代码报错、数据说明和写作内容放入合适目录
- 在回答问题后，将有长期价值的内容写入对应页面，避免知识只停留在聊天记录中
- 定期检查交叉引用、孤立页面、重复页面和过时页面

这个知识库的核心逻辑是：

```text
Index.md = 我有什么
Log.md = 我做了什么
Projects = 我正在推进什么
Knowledge_Base = 我长期掌握什么
Literature = 我读过什么
Skills = 我学会了什么
Code_and_Debug = 我解决过什么代码问题
Data_Documentation = 我有哪些数据及其说明
Writing = 我正在写什么
Archive = 我完成了什么
```

---

## 总体原则

1. **Index 只有一个。** 所有重要页面只通过 `00_Index/Index.md` 进行总导航，不再创建多个分散索引。
2. **Log 只有一个。** 所有操作记录统一追加到 `01_Log/Log.md`，不再每天新建日志文件。
3. **Log 只追加，不重写。** 不要删除、覆盖或大幅修改过去的日志记录。
4. **知识要迁移。** `Log.md` 只记录过程；稳定、有复用价值的内容应迁移到 `Knowledge_Base/`、`Skills/`、`Literature/`、`Code_and_Debug/` 或 `Writing/`。
5. **项目和知识分离。** 项目页面记录具体任务推进，知识页面记录长期可复用的概念、方法和机制。
6. **来源必须明确。** 文献、网页、代码来源、数据来源和用户原始材料都应在页面中注明。
7. **避免文件堆积。** 新建页面前先检查是否已有相关页面；能补充已有页面时不要重复新建。

---

## 目录结构

```text
Obsidian Vault/
│
├── 00_Index/
│   └── Index.md                    # 唯一总索引，所有重要页面的导航入口
│
├── 01_Log/
│   └── Log.md                      # 唯一总日志，只追加，不修改历史记录
│
├── 02_Diary/                       # 日记、周记、月总结，偏个人状态和反思
│   ├── Daily/
│   ├── Weekly/
│   └── Monthly/
│
├── 03_Projects/                    # 当前科研、写作、模型和数据处理项目；按状态管理，便于未来换方向扩展
│   ├── Active/                     # 正在推进的项目
│   │   ├── Lake_DOC_Global_Change/
│   │   ├── Lake_DIC_Global_Change/
│   │   ├── Algal_Bloom_Model/
│   │   └── GLM_AED_Project/
│   ├── Paused/                     # 暂停但未来可能继续的项目
│   ├── Finished/                   # 已完成项目
│   └── Ideas/                      # 尚未正式启动的项目想法
│
├── 04_Knowledge_Base/              # 长期专业知识库，不按单个项目组织，而按可复用知识组织
│   ├── Lake_Carbon/                # 主业知识：湖泊碳循环与 DOC/DIC/POC 等
│   ├── Lake_Water_Quality/         # 水质与水生态过程
│   ├── Remote_Sensing/             # 遥感与 GEE
│   ├── Modeling/                   # 过程模型、机器学习模型与情景预测
│   ├── Statistics/                 # 统计、趋势、归一化、不确定性等方法
│   └── Scientific_Writing/         # 科学写作、论文结构、英文表达
│
├── 05_Literature/                  # 文献笔记和文献主题整理；主题与方法分开，避免被当前研究方向锁死
│   ├── By_Topic/
│   │   ├── Lake_Carbon/
│   │   │   ├── DOC/
│   │   │   ├── DIC/
│   │   │   ├── POC/
│   │   │   └── CO2_CH4/
│   │   ├── Lake_Water_Quality/
│   │   ├── Remote_Sensing/
│   │   ├── Modeling/
│   │   └── Climate_Human_Impacts/
│   ├── By_Method/
│   │   ├── Machine_Learning/
│   │   ├── GLM_AED/
│   │   ├── Trend_Analysis/
│   │   └── Uncertainty/
│   └── Reading_Notes/
│
├── 06_Skills/                      # 从网页、教程、视频、AI 对话中学到的技能
│   ├── Python/
│   ├── GIS_RS/
│   ├── AI_Tools/
│   ├── Writing_Tools/
│   └── Web_Learning/
│
├── 07_Code_and_Debug/              # 代码片段、报错、调试记录和处理流程
│   ├── Python_Scripts/
│   ├── Error_Solutions/
│   ├── Data_Processing_Workflows/
│   └── Automation/
│
├── 08_Data_Documentation/          # 数据说明，而不是原始大数据本体
│   ├── HydroLAKES.md
│   ├── CMIP6.md
│   ├── DOC_Dataset.md
│   ├── DIC_Dataset.md
│   └── Remote_Sensing_Dataset.md
│
├── 09_Writing/                     # 正在写的论文、基金、报告和段落库
│   ├── Papers/
│   ├── Proposals/
│   ├── Reports/
│   └── Paragraph_Bank/
│
├── 10_Templates/                   # 各类页面模板
│   ├── Literature_Note_Template.md
│   ├── Web_Learning_Template.md
│   ├── Code_Debug_Template.md
│   ├── Project_Template.md
│   └── Paper_Section_Template.md
│
├── 11_Archive/                     # 已完成、暂停、废弃或过时内容
│   ├── Old_Notes/
│   └── Deprecated/
│
└── 99_Raw_Data/                    # 原始材料、附件、截图、PDF、图片、表格等统一暂存；只保留整个文件夹，不设子目录
```

---

## `99_Raw_Data/` 使用规范

`99_Raw_Data/` 用于临时保存所有原始材料，包括 PDF、图片、截图、网页下载文件、原始表格、图件和其他未经整理的材料。

该目录只作为原始材料暂存区，**不再设置子目录**。所有有长期价值的内容都应被整理到对应页面中：

- 文献 PDF 的阅读结果整理到 `05_Literature/`
- 图片或图件说明整理到 `09_Writing/` 或相关项目页
- 数据结构说明整理到 `08_Data_Documentation/`
- 网页学习内容整理到 `06_Skills/`
- 代码报错截图整理到 `07_Code_and_Debug/`

`99_Raw_Data/` 不作为知识库主体，只保存原始材料本体。整理完成后，应该在对应知识页、项目页、文献页或写作页中注明原始材料来源。

---

## 文件命名规范

### 通用规则

- 页面文件名优先使用英文，便于跨工具检索和长期维护。
- 推荐格式：`Topic-Name.md` 或 `Topic_Name.md`，同一知识库内保持一致。
- 不要使用过长文件名。
- 不要在文件名中使用特殊符号，如 `:`, `?`, `*`, `|`, `"`, `<`, `>`。
- 日期使用 `YYYY-MM-DD` 格式。

### 推荐命名示例

```text
DIC.md
DOC.md
Lake_Carbon_Cycle.md
Runoff_Dilution.md
Evaporation_Concentration.md
GLM_AED.md
Feature_Distillation.md
xarray_FillValue_Error.md
CMIP6_Point_Extraction.md
Lake_DOC_Paper.md
```

### 中文标题处理

如果用户更习惯中文标题，可以采用：

```text
DIC_湖泊溶解无机碳.md
DOC_湖泊溶解有机碳.md
GLM_AED_湖泊水生态模型.md
```

但不建议文件名完全中文加长句，例如：

```text
不推荐：关于全球湖泊DOC浓度变化和储量估算的文献总结.md
推荐：Global_Lake_DOC_Literature.md
```

---

## `00_Index/Index.md` 维护规范

`Index.md` 是整个知识库唯一总入口。它不需要列出所有页面，只需要列出最重要、最常用、最需要反复进入的页面。

### Index 必须包含

- 快速入口
- 当前重点项目
- 专业知识库入口
- 文献主题入口
- 技能学习入口
- 代码与报错入口
- 数据说明入口
- 写作入口
- 常用模板入口
- 待处理任务

### Index 示例结构

```markdown
# Index

这是整个 Obsidian 知识库的总入口。

---

## 1. 快速入口

- [[Log]]
- [[Lake_DOC_Global_Change]]
- [[Lake_DIC_Global_Change]]
- [[Algal_Bloom_Model]]
- [[GLM_AED_Project]]
- [[Paragraph_Bank]]

---

## 2. 当前重点项目

### 湖泊 DOC 全球变化研究

- [[Lake_DOC_Global_Change]]
- [[DOC_Dataset]]
- [[DOC]]
- [[Lake_Carbon_Cycle]]
- [[Carbon_Storage]]

### 湖泊 DIC 全球变化研究

- [[Lake_DIC_Global_Change]]
- [[DIC_Dataset]]
- [[DIC]]
- [[Lake_Carbon_Cycle]]
- [[Runoff_Dilution]]
- [[Evaporation_Concentration]]

### 藻华机器学习模型

- [[Algal_Bloom_Model]]
- [[Feature_Distillation]]
- [[Remote_Sensing]]
- [[Machine_Learning]]

### GLM-AED 水生态预测

- [[GLM_AED_Project]]
- [[GLM_AED]]
- [[Scenario_Prediction]]
- [[Lake_Ecosystem_Modeling]]

---

## 3. 专业知识库

### 湖泊碳循环

- [[DOC]]
- [[DIC]]
- [[POC]]
- [[Lake_Carbon_Cycle]]
- [[Carbon_Storage]]
- [[Carbon_Flux]]
- [[Runoff_Dilution]]
- [[Evaporation_Concentration]]

### 湖泊水质与水生态

- [[Nutrients]]
- [[Dissolved_Oxygen]]
- [[Chlorophyll]]
- [[Algal_Blooms]]
- [[Aquatic_Vegetation]]

### 遥感与 GIS

- [[Landsat]]
- [[MODIS]]
- [[Sentinel]]
- [[GEE]]
- [[Water_Quality_Retrieval]]
- [[GeoTIFF_Processing]]

### 模型与统计

- [[GLM_AED]]
- [[Machine_Learning]]
- [[Deep_Learning]]
- [[PCA]]
- [[Trend_Analysis]]
- [[Regression]]
- [[Uncertainty]]

---

## 4. 文献笔记

- [[Lake_Carbon_Literature]]
- [[DOC_Literature]]
- [[DIC_Literature]]
- [[Algal_Bloom_Literature]]
- [[Remote_Sensing_Literature]]
- [[GLM_AED_Literature]]

---

## 5. 技能学习

### Python

- [[xarray]]
- [[pandas]]
- [[rasterio]]
- [[rioxarray]]
- [[netCDF]]

### GIS / 遥感

- [[GEE_Skills]]
- [[ArcGIS]]
- [[QGIS]]
- [[GeoTIFF_Processing]]

### 工具

- [[Zotero]]
- [[Obsidian]]
- [[LaTeX]]
- [[ChatGPT]]
- [[Claude]]
- [[Prompt_Templates]]

---

## 6. 代码与报错

- [[xarray_FillValue_Error]]
- [[rioxarray_Reprojection]]
- [[GEE_Export_Error]]
- [[NetCDF_Processing]]
- [[CMIP6_Point_Extraction]]
- [[Python_Automation]]

---

## 7. 数据说明

- [[HydroLAKES]]
- [[CMIP6]]
- [[DOC_Dataset]]
- [[DIC_Dataset]]
- [[Remote_Sensing_Dataset]]

---

## 8. 写作

- [[Lake_DOC_Paper]]
- [[Lake_DIC_Paper]]
- [[Algal_Bloom_Paper]]
- [[GLM_AED_Project_Proposal]]
- [[Introduction]]
- [[Methods]]
- [[Results]]
- [[Discussion]]

---

## 9. 常用模板

- [[Literature_Note_Template]]
- [[Web_Learning_Template]]
- [[Code_Debug_Template]]
- [[Project_Template]]
- [[Paper_Section_Template]]

---

## 10. 待处理

- [ ] 整理最近的 DOC 文献
- [ ] 更新 DIC 论文讨论部分
- [ ] 整理 GLM-AED 项目申请书
- [ ] 记录 Python 数据处理报错
```


---

## `01_Log/Log.md` 维护规范

`Log.md` 是唯一总日志，用于记录所有操作过程、研究推进、代码问题、文献整理和写作修改记录。

### 重要规则

- `Log.md` 只追加，不删除历史记录。
- 每天使用二级标题 `## YYYY-MM-DD`。
- 同一天的不同任务用三级标题或四级标题区分。
- 日志中可以记录简要结论，但长期有价值内容必须迁移到对应知识页。
- 每次完成知识库操作后，都应追加一条日志。

### 推荐格式

```markdown
# Log

这个文件用于记录所有操作过程、研究推进、代码问题、文献整理和写作修改记录。

---

## 2026-05-07

### 今日目标

- 

### 操作记录

#### 1. 

### 遇到的问题

- 

### 解决方案

- 

### 后续任务

- [ ] 
```

### 简短操作日志格式

对于较小操作，也可以追加单行日志：

```markdown
## [2026-05-07] update-index | 更新 Index.md | 新增 4 个项目入口
## [2026-05-07] literature | 整理 DOC 文献 | 新增 1 篇文献笔记
## [2026-05-07] code-debug | xarray _FillValue 报错 | 更新 xarray_FillValue_Error.md
## [2026-05-07] writing | 修改 DIC 讨论部分 | 更新 Lake_DIC_Paper.md
```

### 操作类型

建议使用以下类型，方便后期搜索：

```text
index          # 更新索引
log            # 更新日志格式或整理日志
project        # 项目推进
knowledge      # 专业知识整理
literature     # 文献笔记整理
skill          # 技能学习整理
code-debug     # 代码或报错记录
data-doc       # 数据说明更新
writing        # 论文/基金/报告写作
archive        # 归档
lint           # 定期检查
query          # 问答沉淀
```

---

## 页面类型与格式规范

### 1. 项目页：`03_Projects/`

用于记录一个正在推进的科研、写作或数据处理项目。项目目录按状态管理：正在推进的项目放入 `03_Projects/Active/`，暂停项目放入 `03_Projects/Paused/`，已完成项目放入 `03_Projects/Finished/`，尚未正式启动的想法放入 `03_Projects/Ideas/`。

```yaml
---
type: project
title:
status: active|paused|finished
created:
last_updated:
tags: []
related_pages: []
---
```

必须包含：

```markdown
# 项目名称

## 项目目标

## 研究背景

## 数据与材料

## 方法与技术路线

## 当前进展

## 关键问题

## 下一步计划

## 相关页面

## 操作记录
```

适合页面：

```text
Lake_DOC_Global_Change.md
Lake_DIC_Global_Change.md
Algal_Bloom_Model.md
GLM_AED_Project.md
```

---

### 2. 专业知识页：`04_Knowledge_Base/`

用于记录长期复用的概念、机制、理论、方法。

```yaml
---
type: knowledge
title:
domain: lake_carbon|lake_water_quality|remote_sensing|modeling|statistics|scientific_writing
related: []
source_files: []
source_count: 0
last_updated:
confidence: high|medium|low
---
```

必须包含：

```markdown
# 概念名称

## 定义

## 核心机制

## 影响因素

## 应用场景

## 与其他概念的关系

## 在我研究中的用途

## 来源与证据

## 相关页面
```

示例页面：

```text
DOC.md
DIC.md
POC.md
Lake_Carbon_Cycle.md
Carbon_Storage.md
Carbon_Flux.md
Runoff_Dilution.md
Evaporation_Concentration.md
GLM_AED.md
Feature_Distillation.md
PCA.md
Trend_Analysis.md
```

### 冲突处理

当新资料与已有内容矛盾时：

1. 不要直接覆盖旧观点。
2. 同时记录两种观点。
3. 标注冲突来源。
4. 将 `confidence` 设为 `low` 或 `medium`。
5. 在页面中新增 `## 待验证问题`。

---

### 3. 文献笔记页：`05_Literature/`

用于记录论文、书籍、报告等学术来源。文献优先按主题放入 `By_Topic/`，方法类文献也可以同时在 `By_Method/` 建立主题汇总页或链接，不建议复制同一篇文献笔记。

```yaml
---
type: literature
title:
authors: []
year:
journal:
doi:
source_file:
tags: []
related: []
created:
last_updated:
---
```

必须包含：

```markdown
# Paper Title

## 基本信息

作者：
年份：
期刊：
DOI：

## 研究问题

## 数据与方法

## 主要结论

1. 
2. 
3. 

## 对我研究的价值

- 对 DOC / DIC / 藻华 / 遥感 / GLM-AED 有什么帮助？
- 是否可以作为引言引用？
- 是否可以作为讨论部分的机制支撑？
- 是否有可借鉴的方法？

## 可引用句子

> 

## 我的理解

## 相关主题
```

---

### 4. 技能页：`06_Skills/`

用于记录从网页、视频、教程、AI 对话中学到的可操作技能。

```yaml
---
type: skill
title:
source_url:
learned_date:
tool: python|gee|arcgis|qgis|zotero|obsidian|latex|ai|other
tags: []
related: []
---
```

必须包含：

```markdown
# 技能名称

## 来源

URL：

## 学习日期

## 核心内容

## 可直接使用的方法

```python

```

## 适用场景

## 注意事项

## 相关页面
```

---

### 5. 代码与报错页：`07_Code_and_Debug/`

用于记录代码片段、报错、解决方案和可复用的数据处理流程。

```yaml
---
type: code_debug
title:
language: python|javascript|bash|other
error_type:
related_project:
created:
last_updated:
tags: []
---
```

必须包含：

```markdown
# 问题标题

## 问题背景

## 报错信息

```text

```

## 原因分析

## 解决方案

```python

```

## 注意事项

## 相关页面
```

示例页面：

```text
xarray_FillValue_Error.md
rioxarray_Reprojection.md
GEE_Export_Error.md
NetCDF_Processing.md
CMIP6_Point_Extraction.md
Python_Automation.md
```

---

### 6. 数据说明页：`08_Data_Documentation/`

用于说明数据结构、路径、变量、时间范围、空间范围和处理方式。这里不保存大型原始数据本体。

```yaml
---
type: data_doc
title:
dataset_name:
path:
time_range:
spatial_range:
variables: []
created:
last_updated:
related_projects: []
---
```

必须包含：

```markdown
# 数据集名称

## 数据路径

## 数据结构

## 变量说明

## 时间范围

## 空间范围

## 缺失值与异常值

## 已完成处理

## 待处理问题

## 相关项目
```

---

### 7. 写作页：`09_Writing/`

用于保存论文、基金、报告、段落库和写作素材。

```yaml
---
type: writing
title:
writing_type: paper|proposal|report|paragraph_bank
status: draft|revising|submitted|finished
related_project:
created:
last_updated:
---
```

必须包含：

```markdown
# 写作标题

## 写作目标

## 当前版本

## 结构安排

## 正文草稿

## 修改记录

## 待补充内容

## 相关页面
```

---

### 8. 日记页：`02_Diary/`

日记用于个人状态、反思、计划和总结，不承担科研知识库功能。

```yaml
---
type: diary
date:
mood:
tags: []
---
```

推荐包含：

```markdown
# YYYY-MM-DD

## 今天做了什么

## 状态与反思

## 明天计划

## 灵感
```

---

## 操作流程

### 1. 新增一条普通知识

当用户提供一个概念、机制、方法或解释时：

1. 先判断它属于哪个目录：`Knowledge_Base`、`Skills`、`Code_and_Debug`、`Literature`、`Projects` 或 `Writing`。
2. 检查是否已有相关页面。
3. 如果已有页面，补充到原页面。
4. 如果没有页面，新建页面。
5. 更新 `00_Index/Index.md` 中的重要入口。
6. 追加 `01_Log/Log.md`。

日志格式：

```markdown
## [YYYY-MM-DD] knowledge | 页面标题 | 新增/更新内容摘要
```

---

### 2. 整理文献

当用户要求整理论文、文献、书籍或报告时：

1. 创建或更新 `05_Literature/By_Topic/对应主题/文献标题.md`，如果文献主要属于方法类，也可以放入 `05_Literature/By_Method/对应方法/文献标题.md`。
2. 提取研究问题、数据方法、主要结论、对用户研究的价值。
3. 将重要机制或概念同步到 `04_Knowledge_Base/`。
4. 如果该文献对某个项目有用，在项目页中添加链接。
5. 如果该文献经常使用，在 `Index.md` 的文献入口中添加链接。
6. 追加 `Log.md`。

日志格式：

```markdown
## [YYYY-MM-DD] literature | 文献标题 | 更新页面数
```

---

### 3. 记录网页技能

当用户从网页、教程、视频或 AI 对话中学到技能时：

1. 写入 `06_Skills/` 中对应工具或主题目录。
2. 如果是代码技能，同步到 `07_Code_and_Debug/`。
3. 保留来源 URL、学习日期、适用场景和注意事项。
4. 追加 `Log.md`。

日志格式：

```markdown
## [YYYY-MM-DD] skill | 技能标题 | 来源或用途
```

---

### 4. 记录代码报错与解决方案

当用户遇到代码报错时：

1. 在 `07_Code_and_Debug/Error_Solutions/` 下创建或更新页面。
2. 记录报错原文、原因分析、解决代码、注意事项。
3. 如果该问题属于某个项目或数据处理流程，在项目页或数据说明页添加链接。
4. 追加 `Log.md`。

日志格式：

```markdown
## [YYYY-MM-DD] code-debug | 报错标题 | 解决状态
```

---

### 5. 推进项目

当用户讨论某个项目的方案、结果、图件、方法或写作时：

1. 更新 `03_Projects/Active/对应项目/` 下的项目页。
2. 将稳定的方法和概念迁移到 `04_Knowledge_Base/`。
3. 将正式文字放入 `09_Writing/`。
4. 将数据结构和路径放入 `08_Data_Documentation/`。
5. 追加 `Log.md`。

日志格式：

```markdown
## [YYYY-MM-DD] project | 项目名称 | 推进内容摘要
```

---

### 6. 回答问题并沉淀

当用户提出问题时：

1. 先读 `00_Index/Index.md`，判断相关页面。
2. 再读最相关的 2-3 个页面。
3. 综合回答。
4. 如果回答具有长期价值，写入对应知识页、项目页、技能页或 `09_Writing/Paragraph_Bank/`。
5. 追加 `Log.md`。

日志格式：

```markdown
## [YYYY-MM-DD] query | 问题主题 | 已沉淀到页面
```

---

### 7. 归档

当项目完成、页面过时或内容暂时不用时：

1. 移动到 `11_Archive/Old_Notes/` 或 `11_Archive/Deprecated/`；项目如果已经完成，也可以移动到 `03_Projects/Finished/`。
2. 保留原页面标题和关键链接。
3. 在原项目页或 `Index.md` 中移除高频入口。
4. 追加 `Log.md`。

日志格式：

```markdown
## [YYYY-MM-DD] archive | 页面或项目名称 | 归档原因
```

---

### 8. 定期健检 Lint

定期检查：

- `Index.md` 中是否有死链
- 是否存在孤立页面
- 是否有多个重复页面
- 是否有重要概念反复出现但没有独立页面
- 是否有页面过长，需要拆分
- 是否有项目已完成但未归档
- `Log.md` 是否保持 append-only

日志格式：

```markdown
## [YYYY-MM-DD] lint | 孤立页面数 | 问题摘要
```

---

## 内容迁移规则

### Log 不是知识库本体

`Log.md` 可以记录：

```text
今天处理了 DOC netCDF 数据，发现需要按 Zone 维度求均值和中值。
```

但长期有价值的处理流程应该迁移到：

```text
07_Code_and_Debug/Data_Processing_Workflows/DOC_NetCDF_Processing.md
08_Data_Documentation/DOC_Dataset.md
```

### Project 不是长期知识库

项目页可以记录：

```text
Lake_DIC_Paper 需要强调降水/径流稀释和蒸发浓缩两个机制。
```

但机制本身应该迁移到：

```text
04_Knowledge_Base/Lake_Carbon/Runoff_Dilution.md
04_Knowledge_Base/Lake_Carbon/Evaporation_Concentration.md
```

### Literature 不是摘抄库

文献笔记不能只复制摘要。必须说明：

- 这篇文章解决什么问题
- 使用了什么数据和方法
- 结论是什么
- 对用户当前研究有什么价值
- 可以支撑哪一部分写作

---

## 来源引用要求

每个重要声明必须尽量提供来源。来源可以是：

- 文献笔记：`[[05_Literature/By_Topic/Lake_Carbon/DOC/Paper_Title]]`
- 专业知识页：`[[04_Knowledge_Base/Lake_Carbon/DIC]]`
- 数据说明页：`[[08_Data_Documentation/DOC_Dataset]]`
- 项目页：`[[03_Projects/Active/Lake_DIC_Global_Change/Lake_DIC_Global_Change]]`
- 网页链接：直接写 URL
- 原始文件路径：写本地路径或相对路径；如果原始材料存入 Obsidian，则优先写 `99_Raw_Data/文件名`

示例：

```markdown
降水和径流可能通过稀释作用降低水体 DIC 浓度，这一机制与 [[Runoff_Dilution]] 相关，并可用于支撑 [[Lake_DIC_Paper]] 的讨论部分。
```

---

## Token 与读取预算

为了避免 LLM 读取过多无关内容，遵守以下规则：

1. 会话开始或任务不明确时，只读 `00_Index/Index.md`。
2. 回答具体问题时，只读最相关的 2-3 个页面。
3. 需要深度综合时，再读取项目页、文献页和数据说明页。
4. 不要在没有查看 `Index.md` 的情况下直接大量读取全部文件。
5. 不要把大型原始数据、PDF 全文、图片附件直接读入上下文，除非用户明确要求。

---

## 推荐工作方式

每天的基本流程：

```text
1. 打开 Index.md，确认当前重点项目
2. 在 Log.md 追加今日目标
3. 工作过程中把操作写入 Log.md
4. 发现稳定知识，迁移到 Knowledge_Base
5. 读文献，写入 Literature
6. 学技能，写入 Skills
7. 遇到代码问题，写入 Code_and_Debug
8. 写正式段落，放入 Writing
9. 完成或废弃内容，移入 Archive
```

---

## 最低维护要求

每次重要操作至少完成两个结果：

1. **回答用户当前问题或完成当前任务**
2. **更新知识库记录**

如果无法直接编辑文件，也必须告诉用户应该追加到哪个页面，以及建议追加的 Markdown 内容。

---

## 示例：处理一次代码问题

用户说：

```text
xarray 导出 netCDF 时报错：failed to prevent overwriting existing key _FillValue
```

应该执行：

1. 回答报错原因和解决代码。
2. 更新或新建：

```text
07_Code_and_Debug/Error_Solutions/xarray_FillValue_Error.md
```

3. 如果涉及 DOC 数据处理，同时更新：

```text
08_Data_Documentation/DOC_Dataset.md
```

4. 在 `Log.md` 追加：

```markdown
## [2026-05-07] code-debug | xarray_FillValue_Error | 记录 netCDF 导出编码冲突及解决方案
```

---

## 示例：处理一次论文写作

用户说：

```text
帮我修改湖泊 DIC 讨论部分，强调降水/径流稀释和蒸发浓缩机制。
```

应该执行：

1. 修改正文段落。
2. 将机制沉淀到：

```text
04_Knowledge_Base/Lake_Carbon/Runoff_Dilution.md
04_Knowledge_Base/Lake_Carbon/Evaporation_Concentration.md
```

3. 将正式段落保存到：

```text
09_Writing/Papers/Lake_DIC_Paper/Discussion.md
```

4. 在 `Log.md` 追加：

```markdown
## [2026-05-07] writing | Lake_DIC_Paper | 修改 DIC 水文机制讨论段落
```

---

## 示例：处理一次文献阅读

用户说：

```text
整理这篇关于湖泊 DOC 的论文。
```

应该执行：

1. 生成文献笔记：

```text
05_Literature/By_Topic/Lake_Carbon/DOC/Paper_Title.md
```

2. 如果论文提出重要机制，更新：

```text
04_Knowledge_Base/Lake_Carbon/DOC.md
04_Knowledge_Base/Lake_Carbon/Lake_Carbon_Cycle.md
```

3. 如果论文对当前文章有用，更新：

```text
03_Projects/Active/Lake_DOC_Global_Change/Lake_DOC_Global_Change.md
```

4. 在 `Log.md` 追加：

```markdown
## [2026-05-07] literature | Paper_Title | 新增 DOC 文献笔记并关联 Lake_DOC_Global_Change_Global_Change 项目
```

---

## 最终提醒

这个 Obsidian 知识库不是资料仓库，而是一个科研工作系统。请始终区分：

```text
过程记录 → Log.md
长期知识 → Knowledge_Base
具体任务 → Projects
文献理解 → Literature
技能方法 → Skills
代码问题 → Code_and_Debug
数据说明 → Data_Documentation
正式写作 → Writing
历史内容 → Archive
原始材料 → Raw_Data
```

任何有长期价值的信息，都不应该只留在聊天记录或 `Log.md` 中。
