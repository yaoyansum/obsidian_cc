---
type: data_doc
title: WaterQuality 数据仓库总览
dataset_name: WaterQuality
path: K:\WaterQuality
time_range: 1960s–2024
spatial_range: 全球（北美、欧洲、中国、澳大利亚、南美、非洲、北极/寒区）
variables:
  - DOC, DIC, POC, TOC, TC, TIC
  - CO2, CH4, FCO2, FCH4, N2O
  - TN, TP, NO3, NO2, NH4, PO4, DIN, DIP
  - pH, Temp, Cond, Salinity, DO, TSS, Alkalinity
  - Chl-a, Rrs (350–900nm)
  - d13C, D14C, F14C
  - MAT, MAP, Lake area, Depth, Volume
created: 2026-05-25
last_updated: 2026-05-25
related_projects:
  - Lake_DOC_Global_Change
  - Lake_DIC_Global_Change
  - Algal_Bloom_Model
---

# WaterQuality 数据仓库总览

## 概述

`K:\WaterQuality` 是一个综合性水质数据仓库，主要聚焦湖泊碳循环（DOC、DIC、POC）、pH、温室气体（CO₂、CH₄）及各类水质参数。数据来源涵盖全球、区域和实测数据集，主要用于遥感与水质交叉研究。

总大小约 51 个顶层条目（文件夹 + 压缩包）。

---

## 目录结构与内容

### 核心整合数据

| 目录 | 内容 | 关键文件 |
|------|------|----------|
| `00.03.01.DIC汇总/` | 全球 DIC 整合（多来源合并） | `合并.xlsx`, `全球DIC.xlsx`, `EPA.xlsx`, `GEM.xlsx`, `meta.xlsx`，含 shapefile |
| `00.03.02.PH/` | pH 处理管线（26 个有序 notebook） | EPA/EEA/GEMS pH、CO₂ 通量、蒙特卡洛模拟；输出：`11_*_lake_DIC.csv`, `13_*_FCO2.csv`, `22_*_CO2_flux.xlsx` |
| `00湖泊ID写入Code/` | 观测点匹配 Hylak_id 代码 | 5 个 Jupyter notebook（匹配、缓冲、去空、年均、属性合并） |

### 全球河流/湖泊化学数据库

| 目录                      | 数据集                                     | 范围                 | 关键变量                                                  |
| ----------------------- | --------------------------------------- | ------------------ | ----------------------------------------------------- |
| `02.01.01.Glorich_V01/` | GLORICH 全球河流化学 v1                       | 全球河流，~12,000 站点    | 80+ 变量：TOC, DOC, POC, DIC, TIC, PIC, pH, Alk, 离子, 营养盐 |
| `02.02.01.GRQA/`        | Global River Water Quality Archive v1.4 | 全球河流，5 来源，延伸至 2023 | 43 参数：DOC, DIC, POC, TOC, TC, pH, DO, Temp, 营养盐       |
| `02.03.01SWC_ESSD/`     | SWatCh 全球地表水化学 v2 (ESSD)                | 全球地表水              | pH, 电导率, 主要离子, 营养盐                                    |

### 区域性数据

| 目录 | 区域 | 内容 |
|------|------|------|
| `01.01.00.Australia/` | 澳大利亚 | 各州水质数据（QLD, SA, WA, TAS, WMIS），主要为物理属性 |
| `01.02.02.Australia_pH/` | 澳大利亚 | pH 测量数据（北领地、昆士兰、塔斯马尼亚、SA） |
| `01.03.00.BRAZA/` | 巴西 | 水体光学测量：Rrs 光谱、站点信息、QC flags |
| `01.04.00.ECCCC/` | 加拿大 | 全国水质（22 流域，2000–至今）：DOC, POC, pH, Cond, 营养盐 |
| `01.05.00.EEA/` | 欧洲 | WISE6 水质数据：DOC, POC, Alk, pH, TN, TP 等 |
| `01.06.00.EPA/` | 美国 | US EPA NLA 及历史数据（1984–2023）：DOC, POC, DIC, Chl-a, TSS, Salinity |
| `01.07.00.GEM_Yang/` | 联合国 GEMStat | 全球水质监测数据，含 DOC/POC 提取 |
| `01.07.02.GFQA_v2/` | GEMStat 整理版 | 按参数拆分（85 个 CSV）：DIC, DOC, POC, pH, CHLa, COD, 盐度 |
| `01.07.02.GFQA_v3_202602/` | GFQA v3 | 新版本（当前为空） |
| `01.07.03.补充数据/` | GEMStat 补充 | 额外下载的补充数据 |
| `01.07.03.补充ph_gems/` | GEMStat pH 补充 | pH 数据提取与坐标匹配 |
| `01.08.01.GLORIA-2022/` | 全球湖泊 | 湖泊遥感反射率数据库：Rrs @350–900nm, Es, Lsky, Lt, Lu, Lw |
| `01.09.00.OzRiCa/` | 澳大利亚 | 内陆水体碳数据：DIC, DOC, CO₂, CH₄, POC, 同位素 |

### 论文碳数据与文献数据

| 目录                                 | 描述                                                                                                                                                               |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `01.20251106论文碳数据/`                | 大型全球湖泊碳数据汇编，~100 个文件，涵盖北极/加拿大湖泊（Axel Heiberg, Bathurst, Banks 等）、俄罗斯湖泊（贝加尔、雅库特、勒拿河）、印度 Chilka 湖、埃塞俄比亚 Turkana 湖、亚马逊 Curuai 湖、Cond 系列（PANGAEA, 25 数据集）、冻土/永久冻土系列等 |
| `100.01.00.MORE_POC/`              | Modern River POC Archive v1.1：全球河流 POC，含 d13C, D14C, C/N                                                                                                         |
| `100.02.00.其他/`                    | 杂项论文数据：Stanley 湖泊碳、LTER 数据（ARC, MCM, NTL, SEV）、Giguet-Covex 2011、Lindborg 2016 等                                                                                 |
| `03.01.00CO2/`                     | CO₂ 专项数据：雅库特、Chilka 湖、亚马逊、北方温带湖泊                                                                                                                                 |
| `03.02.02.CoastDOM_Version1/`      | ==沿海 DOM 数据库==：DOC, DON, DOP, POC, PN, PP, DIC, AT                                                                                                               |
| `04.01.00.GH4-EmIly-2016/`         | 全球 CH₄ 数据库（Emily 2016）：CH₄ 浓度、通量、站点、论文                                                                                                                           |
| `04.02.00.GHG_525_Global_CO2&CH4/` | **GasHype 项目**：525 湖泊 CO₂ 和 CH₄ 数据，含湖泊属性                                                                                                                         |
| `04.03.00.GHG-CIWD/`               | **冰冻圈内陆水 GHG**：冰川/冻土区 CO₂ + CH₄，含升尺度 R 代码                                                                                                                        |

### 中国专项数据

| 目录                                             | 描述                                                                                                       |
| ---------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| `1000.01.00.中国实测/`                             | 中国实地数据：太湖 2007–2015 监测、DIC 两批次、全国 pH/DOC/Cond、洪泽湖采样                                                      |
| `1000.01.00.中国地表水数据/`                          | 中国国家地表水水质监测数据（同 03.01.03）：连续在线监测                                                                         |
| ‘’                                             |                                                                                                          |
| `03.01.03.Chinese water quality dataset-2024/` | 中国水质 2024 数据集：full_dataset, daily/weekly/monthly 聚合                                                      |
| `中国卫星反演数据/`                                    | **2000–2023 中国湖泊水库高分辨率水质**（RF 模型反演）：DO, TN, Cond, DOC, pH, CODMn, TP, Turbidity，按月输出，289 湖泊 + 289 水库 CSV |
| `1000.01.00.太湖实测光谱/`                           | 太湖卫星过境时间数据（光谱匹配）                                                                                         |

### 其他

| 目录 | 描述 |
|------|------|
| `其他shp/` | 湖泊/河流 pH 和 DIC 观测 shapefile ~20 个，含 ArcGIS 工程文件 |
| `中国卫星反演数据/` | 见上方中国专项 |
| 各类 `.zip` | 对应文件夹的压缩备份 |

---

## 主要变量清单

| 类别 | 变量 |
|------|------|
| 有机碳 | DOC, POC, TOC, DON, DOP, PON, POP |
| 无机碳 | DIC, TIC, PIC, PC, DC, AT（总碱度）, HCO₃, CO₃ |
| 温室气体 | CO₂, CH₄, FCO₂, FCH₄, N₂O |
| 营养盐 | TN, TP, TDP, TDN, DIN, DIP, NO₃, NO₂, NH₄, TKN, PN, PP, PO₄, SRP |
| 理化参数 | pH, Temp, Cond, Salinity, DO, DOSAT, TSS, SPM, 浊度 |
| 光学参数 | Rrs (350–900nm), Es, Lsky, Lt, Lu, Lw, Chl-a, CODMn |
| 同位素 | d13C-DOC, d13C-DIC, d13C-POC, d13C-CO₂, d13C-CH₄, D14C, F14C |
| 气候/湖泊属性 | MAT, MAP, P_atm, 无冰天数, 表面积, 最大/平均深度, 容积, 停留时间 |

---

## 空间与时间覆盖

### 空间范围

| 区域 | 主要数据集 |
|------|-----------|
| **全球** | GLORICH (河流), GRQA (河流), SWatCh, GHG_525, GH4 (CH₄), CoastDOM, GLORIA (Rrs), MOREPOC (POC), GHG-CIWD (冰冻圈) |
| **北美** | EPA (美国), ECCC (加拿大) |
| **欧洲** | EEA WISE6 |
| **中国** | 中国水质 2024, 卫星反演 (2000–2023), 实测 (太湖/洪泽湖) |
| **澳大利亚** | OzRiCa, Australia_pH, Australia WQ |
| **南美** | BRAZA (巴西), Curuai (亚马逊) |
| **非洲** | Turkana (埃塞俄比亚), Malawi/Nyasa |
| **北极/寒区** | 雅库特, 勒拿河, 加拿大高北极, 永久冻土湖泊, 贝加尔湖 |

### 时间范围

| 时段 | 数据集 |
|------|--------|
| 1960s–2023 | GRQA (延伸至 2023), EPA (1984–2023) |
| 2000–至今 | 中国卫星反演 (月/年), ECCC (加拿大) |
| 1984–2024 | 整合 pH/DIC/CO₂ 通量时间序列 |
| 各研究专项 | 各 CSV/XLSX 中的具体日期 |

---

## 已完成处理

- EPA/EEA/GEMS/中国实测的 pH 数据已提取、匹配 Hylak_id、计算 CO₂ 通量（含蒙特卡洛模拟）
- 多来源的 DOC/POC 数据已从原始格式提取为宽表和长表格式并添加 Hylak_id
- GLORICH 数据已完成 DOC 提取和非空条件筛选
- EEA WISE6 数据已拆分并提取 DOC/POC
- 全球 DIC 数据已合并为汇总表（含 shapefile）

---

## 待处理工作

- [ ] GFQA_v2 数据标为"不完全"，需进一步验证
- [ ] 论文碳数据 (`01.20251106`) 中的 ~100 个文件需统一格式与坐标
- [ ] 中国卫星反演数据的 578 个 CSV 文件需整合为统一时序
- [ ] 各来源 DIC 数据需交叉验证和统一

---

## 相关项目

- [[20260507_Lake_DOC_Global_Change|Lake_DOC_Global_Change]]
- [[20260507_Lake_DIC_Global_Change|Lake_DIC_Global_Change]]
- [[20260507_Algal_Bloom_Model|Algal_Bloom_Model]]
- [[20260507_GLM_AED_Project|GLM_AED_Project]]

## 相关数据页面

- [[20260507_DOC_Dataset|DOC_Dataset]]
- [[20260507_DIC_Dataset|DIC_Dataset]]
- [[20260507_Remote_Sensing_Dataset|Remote_Sensing_Dataset]]
