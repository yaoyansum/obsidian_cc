# 源文件映射

仓库根目录: `F:\100学习资料\earthengine-community-master\earthengine-community-master`

## 快速文件查找

### JavaScript API 参考

`(repo)/samples/javascript/apidocs/`

文件名格式: `ee-{class}-{method}.js`

示例:
- `ee-image-normalizeddifference.js` → `ee.Image.normalizedDifference()`
- `ee-featurecollection-filter.js` → `ee.FeatureCollection.filter()`
- `ee-classifier-smilerandomforest.js` → `ee.Classifier.smileRandomForest()`
- `ee-geometry-point-buffer.js` → `ee.Geometry.Point.buffer()`

### Python API 参考

`(repo)/samples/python/apidocs/`

文件名格式: `ee_{class}_{method}.py`

示例:
- `ee_image_normalizeddifference.py` → `ee.Image.normalizedDifference()`
- `ee_featurecollection_filter.py` → `ee.FeatureCollection.filter()`
- `ee_classifier_smilerandomforest.py` → `ee.Classifier.smileRandomForest()`

### JavaScript 开发指南

`(repo)/samples/javascript/guides/`

文件名格式: `{topic}{NN}.js`

示例: `images01.js`, `classification01.js`, `reducers01.js`

### Python 开发指南

`(repo)/samples/python/guides/`

文件名格式: `{topic}{NN}.py`

示例: `images01.py`, `classification01.py`, `reducers01.py`

### 教程

`(repo)/tutorials/{topic}/index.md` 或 `index.ipynb`

示例: `tutorials/beginners-cookbook/index.md`

### 数据集脚本

`(repo)/datasets/scripts/`

### 外部集成 (Colab)

`(repo)/guides/linked/`

## 各路径文件数量

| 路径 | 格式 | 数量 |
|------|------|------|
| `samples/javascript/apidocs/` | `.js` | 831 |
| `samples/python/apidocs/` | `.py` | 787 |
| `samples/javascript/guides/` | `.js` | 109 |
| `samples/python/guides/` | `.py` | ~80 |
| `tutorials/` | `index.md` / `index.ipynb` | 45 |
| `datasets/scripts/` | `.js` | 6 |
| `guides/linked/` | `.ipynb` | 23 |

## 如何使用此参考

1. 确定需要的 ee.* 类和方法 → 在对应 API 参考文件中查找
2. 打开源文件查看完整示例代码（含注释）
3. 如需完整工作流 → 查看开发指南
4. 如需分步教程 → 查看教程目录
