# Python API 注意事项

## Python 特有方法

以下方法仅在 Python API 示例中存在：

| 方法 | 说明 |
|------|------|
| `ee.data.computeFeatures` | 计算要素数据 |
| `ee.data.computePixels` | 计算像素数据 |
| `ee.data.getPixels` | 获取像素数据 |

## 差异说明

### JS 有但 Python 无的 API 方法
- `ee.Image.constant` — Python 中直接 `ee.Image(val)` 替代
- `ee.FeatureCollection.aside` — Python 中少用
- `ee.Geometry.coveringGrid` — Python 暂缺
- `ee.Geometry.snap` — Python 暂缺
- `ee.Reducer.minmax` — Python 暂缺
- `ee.Join.simple` — Python 暂缺
- 大部分 `Map.*` 方法 — Python 使用 `geemap.Map()`
- 大部分 `ui.*` 方法 — Python 使用 `geemap` 和 `ipyleaflet`

### Python 有但 JS 无的 API 示例
- `ee.data.*` 方法系列（Python 特有的直接 API 调用）

### JS 有但 Python 无的开发指南

以下 JS 指南没有对应的 Python 版本：
- 图表类：`charts_*.js`（5 个文件）
- 入门指南：`gettingStarted01.js` ~ `gettingStarted11.js`（11 个文件）
- UI 相关：`ui01_intro.js` ~ `ui04_events.js`（4 个文件）
- Features: `features01.js`、`featureview_overview.js`
- 其他：`overlay.js`, `pca.js`, `interpolation.js`, `modules.js` 等

## Python 使用推荐

Python API 在 Colab 或本地 Jupyter 环境中使用时：

```python
import ee
import geemap

# 初始化
ee.Initialize()

# 创建地图（替代 Map）
Map = geemap.Map()
Map.addLayer(...)
Map.centerObject(...)
Map.display()  # 在 Jupyter/Colab 中显示
```

## 源文件对应关系

| JavaScript | Python |
|------------|--------|
| `samples/javascript/apidocs/ee-image-normalizeddifference.js` | `samples/python/apidocs/ee_image_normalizeddifference.py` |
| `samples/javascript/guides/images01.js` | `samples/python/guides/images01.py` |
| `samples/javascript/guides/classification01.js` | `samples/python/guides/classification01.py` |
| 同上模式 | 文件名改为下划线分隔 |
