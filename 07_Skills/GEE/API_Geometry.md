# ee.Geometry 方法参考

源文件: `samples/javascript/apidocs/ee-geometry-*.js` / `samples/python/apidocs/ee_geometry_*.py`

> ee.Geometry 有 320 个方法，覆盖多种几何子类型。方法按功能分组如下。

## 基础几何类型（均支持以下方法）

包含子类型：
- `ee.Geometry`（基础）
- `ee.Geometry.BBox`（边界框）
- `ee.Geometry.LinearRing`（线性环）
- `ee.Geometry.LineString`（折线）
- `ee.Geometry.MultiLineString`（多折线）
- `ee.Geometry.MultiPoint`（多点）
- `ee.Geometry.MultiPolygon`（多多边形）
- `ee.Geometry.Point`（点）
- `ee.Geometry.Polygon`（多边形）
- `ee.Geometry.Rectangle`（矩形）

### 空间测量
- `area` — 面积
- `length` — 长度
- `distance` — 距离
- `perimeter` — 周长（BBox）

### 空间关系
- `containedin` — 被包含
- `contains` — 包含
- `disjoint` — 不相交
- `intersects` — 相交
- `withindistance` — 在距离内（BBox）

### 空间操作
- `buffer` — 缓冲区
- `centroid` — 质心
- `closestpoint` — 最近点
- `convexhull` — 凸包
- `cutlines` — 切线
- `difference` — 差异
- `dissolve` — 溶解
- `intersection` — 交集
- `symmetricdifference` — 对称差
- `union` — 并集
- `simplify` — 简化（BBox）

### 属性与信息
- `bounds` — 边界
- `coordinates` — 坐标
- `edgesaregeodesics` — 边是否测地线
- `geodesic` — 测地线
- `geometries` — 子几何
- `getinfo` — 获取信息
- `isunbounded` — 是否无界
- `projection` — 投影
- `type` — 几何类型（BBox）

### 序列化与转换
- `evaluate` — 求值
- `serialize` — 序列化
- `togeojson` — 转 GeoJSON（BBox）
- `togeojsonstring` — 转 GeoJSON 字符串（BBox）

### 其他
- `coveringgrid` — 覆盖网格（非 BBox）
- `coveringgrid` — 覆盖网格
