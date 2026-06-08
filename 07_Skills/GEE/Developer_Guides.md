# 开发指南参考

源文件: `samples/javascript/guides/` / `samples/python/guides/`

## 图像操作 (images01 ~ images18)

| 文件 | 主题 |
|------|------|
| `images01.js` | 图像概述 — 波段、像素值、元数据 |
| `images02.js` | 图像数学运算 |
| `images03.js` | 图像可视化 |
| `images04.js` | 图像颜色可视化 |
| `images041.js` | 图像调色板 |
| `images042.js` | 图像阈值 |
| `images043.js` | 图像可视化高级技巧 |
| `images05.js` | 图像关系运算、布尔运算与掩膜 |
| `images06.js` | 图像波段操作（添加、选择、重命名） |
| `images07.js` | 图像正则表达式（按名称选择波段） |
| `images08.js` | 图像投影 |
| `images09.js` | 图像变形（旋转、平移、偏移） |
| `images10.js` | 图像累积 |
| `images11.js` | 图像对象方法（边界、质心、凸包等） |
| `images12.js` | 图像缩放 |
| `images13.js` | 图像卷积（与核卷积） |
| `images14.js` | 图像的 reduceRegion 操作 |
| `images15.js` | 图像减少分辨率 |
| `images16.js` | 图像派生波段 |
| `images17.js` | 图像重投影与变形 |
| `images18.js` | 图像可视化 — 使用地形图像 |

## 影像集合 (image_collections01 ~ image_collections10)

| 文件 | 主题 |
|------|------|
| `image_collections01.js` | 集合概述 — 合并、过滤、可视化 |
| `image_collections02.js` | 集合信息与元数据 |
| `image_collections03.js` | 集合迭代、映射、过滤 |
| `image_collections04.js` | 集合归约（合成） |
| `image_collections05.js` | 集合的高级合成 |
| `image_collections06.js` | 集合的质量马赛克 |
| `image_collections07.js` | 集合的迭代方法 |
| `image_collections08.js` | 集合的 reduceRegion 与 reduceRegions |
| `image_collections085.js` | 集合合成与统计 |
| `image_collections09.js` | 集合的图表 |
| `image_collections10.js` | 集合的时间序列合成 |

## 分类 (classification01 ~ classification03)

| 文件 | 主题 |
|------|------|
| `classification01.js` | 监督分类 |
| `classification02.js` | 分类器比较（CART、RF、SVM、NB、kNN、GTB） |
| `classification03.js` | 多类监督分类 |

## 聚类

| 文件 | 主题 |
|------|------|
| `clustering.js` | 无监督聚类 |

## 归约器 (reducers01 ~ reducers15)

| 文件 | 主题 |
|------|------|
| `reducers00_overview.js` | 归约器概述与比较 |
| `reducers01.js` | 图像归约概述 |
| `reducers011.js` | 图像集合归约概述 |
| `reducers02.js` | 图像归约 — reducer 输出 |
| `reducers03.js` | 重投影与归约 |
| `reducers04.js` | 区域归约 — 分组 |
| `reducers05.js` | 图像集合归约 — 线性拟合 |
| `reducers06.js` | 递归归约 |
| `reducers07.js` | 编写自定义归约器 |
| `reducers08.js` | 柱状图归约器 |
| `reducers09.js` | 加权归约器 |
| `reducers10.js` | 归约器 kval 参数 |
| `reducers11.js` | 范围与像素比例 |
| `reducers12.js` | 添加 reducer 输出 |
| `reducers13.js` | 多输入、多输出归约器 |
| `reducers14.js` | 归约器 — count.everywhere |
| `reducers15.js` | 图像集合的多个归约 |

## 特征与要素集合 (features01 ~ features05)

| 文件 | 主题 |
|------|------|
| `features01.js` | 要素概述 |
| `features02.js` | 要素集合概述 |
| `features03.js` | 要素集合过滤 |
| `features04.js` | 要素集合矢量归约 |
| `features05.js` | 要素集合可视化 |

## FeatureView

| 文件 | 主题 |
|------|------|
| `featureview_overview.js` | FeatureView 概述 |

## 数组 (arrays01 ~ arrays06)

| 文件 | 主题 |
|------|------|
| `arrays01.js` | 数组概述 |
| `arrays02.js` | 数组切片与正则化 |
| `arrays03.js` | 数组数学运算 |
| `arrays04.js` | 数组与图像转换 |
| `arrays05.js` | 数组排序、交换、归约 |
| `arrays06.js` | 高级数组操作 |

## 连接 (joins01 ~ joins08)

| 文件 | 主题 |
|------|------|
| `joins01.js` | 连接概述 |
| `joins02.js` | 简单连接 |
| `joins03.js` | 过滤连接 |
| `joins04.js` | 交叉连接 |
| `joins05.js` | 笛卡尔积连接 |
| `joins06.js` | 空间连接 |
| `joins07.js` | 连接（高级 — SaveBest 与迭代） |
| `joins08.js` | 连接应用的多个示例 |

## 图表 (charts_*)

| 文件 | 主题 |
|------|------|
| `charts_array.js` | 数组图表 |
| `charts_datatable.js` | 数据表图表 |
| `charts_feature.js` | 要素图表 |
| `charts_image.js` | 图像图表 |
| `charts_image_collection.js` | 图像集合图表 |

## Landsat (landsat01 ~ landsat03)

| 文件 | 主题 |
|------|------|
| `landsat01.js` | Landsat 概述 — 地表反射率 |
| `landsat02.js` | Landsat 高级合成 |
| `landsat03.js` | Landsat 辐射定标 |

## Sentinel-1

| 文件 | 主题 |
|------|------|
| `sentinel1.js` | Sentinel-1 SAR 操作 |

## 导出 (export_*)

| 文件 | 主题 |
|------|------|
| `export_map_tiles.js` | 地图瓦片导出 |
| `export_to_bigquery.js` | 导出到 BigQuery |

## 导入/导出 (import_export*)

| 文件 | 主题 |
|------|------|
| `import_export01.js` | 资产导入与导出 |
| `import_export02.js` | 导入/导出属性 |

## 入门指南 (gettingStarted01 ~ gettingStarted11)

| 文件 | 主题 |
|------|------|
| `gettingStarted01.js` | Landsat 8 真彩色合成 |
| `gettingStarted02.js` | 哨兵 2 真彩色合成 |
| `gettingStarted03.js` | Landsat 8 归一化 |
| `gettingStarted04.js` | 哨兵 2 归一化 |
| `gettingStarted05.js` | 计算 NDVI |
| `gettingStarted06.js` | 计算 EVI |
| `gettingStarted07.js` | 计算 NBR |
| `gettingStarted08.js` | 时间序列 |
| `gettingStarted09.js` | 聚类 |
| `gettingStarted10.js` | 影像导出 |
| `gettingStarted11.js` | 过滤和排序 |

## 其他指南

| 文件 | 主题 |
|------|------|
| `concepts.js` | Earth Engine 核心概念 |
| `debugging.js` | 调试技巧 |
| `modules.js` | 模块化代码 |
| `monitoring_usage.js` | 使用监控 |
| `overlay.js` | 叠加分析 |
| `pca.js` | 主成分分析 |
| `register.js` | 注册 |
| `resample.js` | 重采样 |
| `cumulativeCost.js` | 累积成本 |
| `interpolation.js` | 插值 |
| `quickstart.js` | 快速入门 |
| `tutorial_0.js` | 教程 0 |
| `tutorial_1.js` | 教程 1 |
| `tutorial_1_functional.js` | 函数式教程 |
| `tutorial_2_forest.js` | 森林教程 |

## UI (ui01 ~ ui04)

| 文件 | 主题 |
|------|------|
| `ui01_intro.js` | UI 入门 |
| `ui02_widgets.js` | UI 组件 |
| `ui03_panels.js` | UI 面板 |
| `ui04_events.js` | UI 事件 |
