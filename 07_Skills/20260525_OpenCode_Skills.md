---
type: skill_index
title: OpenCode 可用技能索引
domain: development
created: 2026-05-25
last_updated: 2026-05-25
skills_count: 27
---

# OpenCode 可用技能索引

本页汇总当前 OpenCode 环境可调用的全部技能（skills）。每个技能是一套结构化指令，用于触发 LLM 执行特定领域的复杂任务。

---

## 论文与研究管线

### [academic-paper](/skills/academic-paper)
12-agent 学术论文写作管线。支持完整写作/规划/大纲/修改/摘要/文献综述/格式转换/引文检查 10 种模式。6 种论文类型、5 种引文格式、中英双语摘要、LaTeX/DOCX/PDF 输出。
- 触发词：*write paper, academic paper, 寫論文, 引導我寫論文, 審查意見*

### [academic-paper-reviewer](/skills/academic-paper-reviewer)
多视角学术论文评审。模拟 5 个独立审稿人（主编 + 3 同行 + 魔鬼代言人），支持完整评审/复审/快速评估/方法审查/苏格拉底引导/校准 6 种模式。
- 触发词：*review paper, peer review, simulate review, 审稿*

### [academic-pipeline](/skills/academic-pipeline)
完整学术管线编排器：研究 → 写作 → 诚信检查 → 评审 → 修改 → 复审 → 再修改 → 终检 → 定稿。协调 deep-research、academic-paper、academic-paper-reviewer 三大技能。
- 触发词：*academic pipeline, research to paper, full paper workflow*

### [deep-research](/skills/deep-research)
13-agent 深度研究管线。7 种模式：完整研究/快速简报/论文审阅/文献综述/事实核查/苏格拉底对话/系统综述（含 Meta 分析）。覆盖研究问题、方法论设计、系统文献搜索、来源验证、风险偏倚评估。
- 触发词：*deep research, literature review, systematic review, 深度研究, 文獻回顧*

### [citation-management](/skills/citation-management)
引文管理。搜索 Google Scholar 和 PubMed 获取论文元数据，验证引文，生成 BibTeX。
- 触发词：*citation, BibTeX, DOI, 参考文献*

---

## 头脑风暴与规划

### [brainstorming](/skills/brainstorming)
创意工作前的需求探索。在创建功能、构建组件、修改行为前必用。挖掘用户意图、需求、设计方案。
- 触发词：*在创建新功能/组件前自动触发*

### [writing-plans](/skills/writing-plans)
生成多步骤实现计划。有明确 spec 或需求后，编码前使用。
- 触发词：*有实现计划要编写时使用*

### [writing-skills](/skills/writing-skills)
创建、编辑和验证 skills 文件。开发新技能前使用。
- 触发词：*创建/编辑技能时使用*

---

## 中文毕业论文

### [chinese-thesis-workbench](/skills/chinese-thesis-workbench)
中国本科毕业论文工作台。从学校模板、任务书、开题报告、范文、源码、截图、数据库、API、测试、文献 PDF、Word 批注中标准化、起草、修改、查重降重、格式校验、打包输出。
- 触发词：*毕业论文, 毕业设计, thesis, 降重, AIGC 检测*

---

## 地学与遥感

### [geomaster](/skills/geomaster)
综合地理空间科学技能。覆盖遥感、GIS、空间分析、地球观测机器学习、30+ 科学领域。支持 Sentinel/Landsat/MODIS/SAR/高光谱影像处理、矢栅操作、空间统计、点云、网络分析、云原生工作流。8 种编程语言，500+ 代码示例。
- 触发词：*remote sensing, GIS, spatial analysis, 遥感, 地理信息*

### [geopandas](/skills/geopandas)
Python 地理空间矢量数据处理库。支持 shapefile/GeoJSON/GeoPackage 读写、空间分析、几何操作、坐标变换、空间连接、叠加分析、分级统计制图。
- 触发词：*geopandas, shapefile, 空间分析, 矢量数据*

---

## 演示文稿

### [codex-ppt](/skills/codex-ppt)
生成全图型 PowerPoint。每页幻灯片为 AI 生成的全幅图片，组装为 PPTX 文件。
- 触发词：*codex ppt, 图片型 PPT, image-based slides*

### [ppt-master](/skills/ppt-master)
创建、编辑、分析 PowerPoint 演示文稿。支持模板、布局、演讲者备注、评论。
- 触发词：*deck, slides, presentation, pptx, powerpoint*

### [pptx](/skills/pptx)
PowerPoint 文件的通用处理（读/写/编辑/合并/拆分/提取文本）。涉及 .pptx 文件时必用。
- 触发词：*任何涉及 .pptx 文件的操作*

### [sjtu-ppt-template](/skills/sjtu-ppt-template)
上海交通大学风格可编辑 PPT。从 DOCX/笔记/大纲/报告/论文/数据集中生成交大风格演示文稿。支持数据可视化、科研图表、演讲稿。
- 触发词：*上海交通大学, SJTU, 交大 PPT, 答辩幻灯片*

---

## 文档与数据处理

### [docx](/skills/docx)
Word 文档创建/读取/编辑/操作。支持目录、标题、页眉页脚、图片插入、查找替换、修订跟踪。
- 触发词：*Word doc, .docx, 报告, 信函, 模板*

### [xlsx](/skills/xlsx)
电子表格文件处理（.xlsx/.xlsm/.csv/.tsv）。支持打开、编辑、公式计算、格式化、图表、数据清洗、格式转换。
- 触发词：*xlsx, spreadsheet, 表格, csv, Excel*

### [pdf](/skills/pdf)
PDF 文件全能处理。读取/提取文本表格、合并拆分、旋转、水印、创建、表单填写、加密解密、图片提取、OCR。
- 触发词：*.pdf, PDF, 扫描件, Acrobat*

---

## Obsidian 集成

### [json-canvas](/skills/json-canvas)
JSON Canvas（.canvas 文件）的创建与编辑。支持节点、边、分组、连接。Obsidian Canvas 思维导图、流程图。
- 触发词：*.canvas, Canvas, 思维导图, 流程图*

### [obsidian-bases](/skills/obsidian-bases)
Obsidian Bases（.base 文件）的创建与编辑。支持视图、筛选器、公式、汇总。数据库式笔记视图。
- 触发词：*.base, Bases, 数据库视图, 表格视图*

### [obsidian-cli](/skills/obsidian-cli)
通过 CLI 与 Obsidian 交互。笔记创建/搜索/管理、任务管理、属性操作、插件/主题开发与调试。
- 触发词：*obsidian CLI, vault 操作, 插件开发*

### [obsidian-markdown](/skills/obsidian-markdown)
Obsidian 风格 Markdown 编写。wikilinks、embeds、callouts、properties 等 Obsidian 特有语法。
- 触发词：*.md, wikilinks, callouts, frontmatter, Obsidian 笔记*

---

## Web 与浏览器

### [defuddle](/skills/defuddle)
从网页提取纯净 Markdown。去除无关导航和干扰内容以节省 Token。对标准网页替代 WebFetch。
- 触发词：*网页内容提取, URL 读取, web page reading*

### [playwright-cli](/skills/playwright-cli)
浏览器自动化。网页测试、交互、截图。
- 触发词：*浏览器自动化, Playwright, web testing*

### [playwright-trace](/skills/playwright-trace)
Playwright trace 文件检查。从命令行列出 actions、requests、console、errors、snapshots、screenshots。
- 触发词：*trace 文件, Playwright 调试*

---

## 配置与工具

### [customize-opencode](/skills/customize-opencode)
仅用于编辑 OpenCode 自身配置：opencode.json、.opencode/、~/.config/opencode/。创建或修复 agents、subagents、skills、plugins、MCP servers、permission rules。
- 触发词：*opencode 配置, 编辑 opencode.json, 创建 skill/plugin*

### [executing-plans](/skills/executing-plans)
在独立会话中按书面实现计划执行，带审查检查点。
- 触发词：*执行计划, implementation plan execution*

---

## 相关页面

- [[00_Index/Index|Index]]
- [[01_Log/Log|Log]]
- [[07_Skills/Git/20260522_Git_Commands|Git 常用命令与技巧]]
