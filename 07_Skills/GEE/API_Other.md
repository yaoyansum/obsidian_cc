# ee.Reducer, ee.Terrain, ee.Algorithms, ee.Chart 及其他

## ee.Reducer (2 个方法示例)

源文件: `samples/javascript/apidocs/ee-reducer-*.js` / `samples/python/apidocs/ee_reducer_*.py`

> Reducer 是 Earth Engine 的核心概念，用于聚合统计。以下为 API 示例文件，完整的红ucer 使用见开发指南 `reducers00_overview.js` ~ `reducers15.js`。

- `count` — 计数红ucer
- `minmax` — 最小最大值红ucer

---

## ee.Terrain (4 个方法)

源文件: `samples/javascript/apidocs/ee-terrain-*.js` / `samples/python/apidocs/ee_terrain_*.py`

- `aspect` — 坡向
- `hillshade` — 山体阴影
- `products` — 地形产品（坡度、坡向、山体阴影）
- `slope` — 坡度

---

## ee.Algorithms (3 个方法)

源文件: `samples/javascript/apidocs/ee-algorithms-*.js` / `samples/python/apidocs/ee_algorithms_*.py`

- `If` — 条件判断
- `Image.Segmentation.SNIC` — SNIC 超像素分割
- `ObjectType` — 对象类型

---

## ee.Chart (5 个方法)

源文件: `samples/javascript/apidocs/ee-chart-*.js` / `samples/python/apidocs/ee_chart_*.py`

> 完整的图表指南见 `samples/javascript/guides/charts_*.js`

- 图表系列方法（5 个文件）

---

## 其他单文件方法

| 源文件 | 说明 |
|--------|------|
| `ee-Image.js` | ee.Image 构造函数 |
| `ee-Feature.js` | ee.Feature 构造函数 |
| `ee-FeatureCollection.js` | ee.FeatureCollection 构造函数 |
| `ee-Geometry.js` | ee.Geometry 构造函数 |
| `ee-Array.js` | ee.Array 构造函数 |
| `ee-String.js` | ee.String 构造函数 |
| `ee-Number.js` | ee.Number 构造函数 |
| `ee-List.js` | ee.List 构造函数 |
| `ee-Dictionary.js` | ee.Dictionary 构造函数 |
| `ee-Date.js` | ee.Date 构造函数 |
| `ee-DateRange.js` | ee.DateRange 构造函数 |
| `ee-ConfusionMatrix.js` | ee.ConfusionMatrix 构造函数 |
| `ee-ErrorMargin.js` | ee.ErrorMargin 构造函数 |
| `ee-PixelType.js` | ee.PixelType 构造函数 |
| `ee-Projection.js` | ee.Projection 构造函数 |
| `ee-Blob.js` | ee.Blob 构造函数 |
| `ee-Data.js` (×2) | ee.Data 相关方法 |
| `ee-Table.js` | ee.Table 相关方法 |

## UI 组件

源文件: `samples/javascript/apidocs/`

| 组件 | 源文件 |
|------|--------|
| Map | `ee-Map.js`, `ee-map-addlayer.js`, `ee-map-add.js`, `ee-map-setcenter.js`, `ee-map-setoptions.js`, `ee-map-setzoom.js`, `ee-map-getscale.js`, `ee-map-getbounds.js`, `ee-map-getcenter.js`, `ee-map-getzoom.js` |
| Button | `ee-Button.js` |
| Checkbox | `ee-Checkbox.js` |
| DateSlider | `ee-DateSlider.js` |
| Label | `ee-Label.js` |
| Panel | `ee-Panel.js` |
| Select | `ee-Select.js` |
| Slider | `ee-Slider.js` |
| SplitPanel | `ee-SplitPanel.js` |
| Table | `ee-Table.js` |
| Textbox | `ee-Textbox.js` |
| Thumbnail | `ee-Thumbnail.js` |

## ee.Join (1 个文件)

源文件: `samples/javascript/apidocs/ee-join.js` / `samples/python/apidocs/ee_join.py`

> 完整的连接操作指南见 `samples/javascript/guides/joins01.js` ~ `joins08.js`
