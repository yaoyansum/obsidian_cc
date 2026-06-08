# ee.Classifier 方法参考

源文件: `samples/javascript/apidocs/ee-classifier-*.js` / `samples/python/apidocs/ee_classifier_*.py`

## 分类器

| 方法 | 说明 | 源文件 |
|------|------|--------|
| `amnhmaxent` | MaxEnt 最大熵分类器 | `ee-classifier-amnhmaxent.js` |
| `confusionmatrix` | 从混淆矩阵构造 | `ee-classifier-confusionmatrix.js` |
| `explain` | 解释分类器 | `ee-classifier-explain.js` |
| `libsvm` | 支持向量机 (SVM) | `ee-classifier-libsvm.js` |
| `minimumdistance` | 最小距离分类器 | `ee-classifier-minimumdistance.js` |
| `smilecart` | CART 决策树 | `ee-classifier-smilecart.js` |
| `smilegradienttreeboost` | 梯度提升树 | `ee-classifier-smilegradienttreeboost.js` |
| `smileknn` | K 最近邻 (kNN) | `ee-classifier-smileknn.js` |
| `smilenaivebayes` | 朴素贝叶斯 | `ee-classifier-smilenaivebayes.js` |
| `smilerandomforest` | 随机森林 | `ee-classifier-smilerandomforest.js` |

## 训练与使用

- `train` — 训练分类器 (`ee-classifier-train.js`)

> 注意：分类器通常与 `ee.Image.classify()` 或 `ee.FeatureCollection.classify()` 配合使用。

## 相关开发指南

详见 [[Developer_Guides]]：
- `classification01.js` — 监督分类基础
- `classification02.js` — 分类器比较
- `classification03.js` — 多类分类
