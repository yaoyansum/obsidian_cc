# Google Earth Engine 代码参考

本目录整理了 Google Earth Engine 官方社区代码仓库的全部参考资源，包含约 1900 个代码示例。

## 仓库位置

`F:\100学习资料\earthengine-community-master\earthengine-community-master`

## 目录结构

| 路径 | 内容 | 数量 |
|------|------|------|
| `samples/javascript/apidocs/` | JavaScript API 方法示例（每个 ee.* 方法一个文件） | 831 |
| `samples/python/apidocs/` | Python API 方法示例 | 787 |
| `samples/javascript/guides/` | JavaScript 开发指南 | 109 |
| `samples/python/guides/` | Python 开发指南 | ~80 |
| `tutorials/` | 完整教程（.md + .ipynb） | 45 |
| `datasets/scripts/` | 数据集可视化脚本 | 6 |
| `guides/linked/` | 外部集成 Colab 笔记本 | 23 |
| `examples/` | 额外示例（ADK Agents, Cloud Next 2025） | 2 |
| `experimental/` | 实验性脚本 | 4 |

## 参考文件索引

- [[API_Images]] — ee.Image、ee.ImageCollection 方法
- [[API_Features]] — ee.Feature、ee.FeatureCollection、ee.Filter 方法
- [[API_Geometry]] — ee.Geometry 方法（含所有子类型）
- [[API_Math]] — ee.Number、ee.Array、ee.Kernel 方法
- [[API_DataTypes]] — ee.String、ee.List、ee.Dictionary、ee.Date、ee.DateRange、ee.ConfusionMatrix
- [[API_Classification]] — ee.Classifier
- [[API_Other]] — ee.Reducer、ee.Terrain、ee.Algorithms、ee.Chart、ee.Join 等
- [[Developer_Guides]] — 开发指南（JS + Python）
- [[Tutorials]] — 完整教程列表
- [[Datasets_and_Integrations]] — 数据集脚本与外部集成

## 使用方法

### 查找特定 ee.* 方法

API 参考文件按类分组，每个方法标注了对应的源文件路径。例如：
- `ee.Image.normalizedDifference()` → `samples/javascript/apidocs/ee-image-normalizeddifference.js`
- `ee.Classifier.smileRandomForest()` → `samples/javascript/apidocs/ee-classifier-smilerandomforest.js`

### 查找概念或工作流

使用 [[Developer_Guides]] 查找主题相关指南，如分类、归约、连接、数组操作等。

### 查找完整教程

使用 [[Tutorials]] 查看按主题分类的教程列表。

### 跨语言查找

大多数示例有 JavaScript 和 Python 两个版本。API 参考中标注了两种语言的源文件路径。
