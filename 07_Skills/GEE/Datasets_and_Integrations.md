# 数据集脚本与外部集成

## 数据集脚本

源文件: `datasets/scripts/`

| 文件 | 说明 |
|------|------|
| `GOES-16-17_FireDetection.js` | GOES-16/17 火灾检测 |
| `GOES-16-17_FireReclassification.js` | GOES-16/17 火灾重分类 |
| `Hydro_Visualization.js` | 水文可视化 |
| `LCMS_Visualization.js` | LCMS 可视化 |
| `SMAPL3_meancomposite.js` | SMAP L3 月均值合成 |
| `SMAPL3dailyanomaly.js` | SMAP L3 日异常 |

---

## 外部集成指南

源文件: `guides/linked/`（均为 Colab 笔记本 `.ipynb`）

### TensorFlow 集成

| 文件 | 说明 |
|------|------|
| `Earth_Engine_TensorFlow_AI_Platform.ipynb` | EE + TensorFlow AI Platform |
| `Earth_Engine_TensorFlow_Decision_Forests.ipynb` | EE + TensorFlow 决策森林 |
| `Earth_Engine_TensorFlow_DNN_from_scratch.ipynb` | EE + 从头构建 DNN |
| `Earth_Engine_TensorFlow_logistic_regression.ipynb` | EE + TensorFlow 逻辑回归 |
| `Earth_Engine_TensorFlow_tree_counting_model.ipynb` | EE + TensorFlow 树木计数 |
| `Earth_Engine_TensorFlow_Vertex_AI.ipynb` | EE + TensorFlow Vertex AI |
| `TF_demo1_keras.ipynb` | TensorFlow Keras 演示 |
| `UNET_regression_demo.ipynb` | U-Net 回归演示 |

### PyTorch 集成

| 文件 | 说明 |
|------|------|
| `Earth_Engine_PyTorch_Vertex_AI.ipynb` | EE + PyTorch Vertex AI |

### Vertex AI 与 AutoML

| 文件 | 说明 |
|------|------|
| `Earth_Engine_AutoML_Vertex_AI.ipynb` | EE + AutoML Vertex AI |
| `Earth_Engine_Vertex_AI_training_demo.ipynb` | EE + Vertex AI 训练演示 |
| `AI_platform_demo.ipynb` | AI Platform 演示 |
| `Yggdrasil_decision_forests_earthengine_vertex_ai.ipynb` | Yggdrasil 决策森林 + EE + Vertex AI |

### REST API

| 文件 | 说明 |
|------|------|
| `Earth_Engine_REST_API_Quickstart.ipynb` | REST API 快速入门 |
| `Earth_Engine_REST_API_compute_image.ipynb` | REST API 图像计算 |
| `Earth_Engine_REST_API_compute_table.ipynb` | REST API 表格计算 |

### 训练数据生成

| 文件 | 说明 |
|------|------|
| `Earth_Engine_training_patches_computePixels.ipynb` | 使用 computePixels 生成训练块 |
| `Earth_Engine_training_patches_getPixels.ipynb` | 使用 getPixels 生成训练块 |

### 其他

| 文件 | 说明 |
|------|------|
| `Earth_Engine_PCA.ipynb` | Earth Engine PCA |
| `Earth_Engine_benchmarking_toolkit.ipynb` | EE 基准测试工具包 |
| `ee-api-colab-setup.ipynb` | Earth Engine Colab 环境设置 |
| `Uploading_image_tiles_as_a_single_asset_using_a_manifest.ipynb` | 使用清单上传影像瓦片 |
| `cloud-monitoring/` | 云监控相关 |
| `generated/` | 自动生成内容 |

---

## 额外示例

| 路径 | 说明 |
|------|------|
| `examples/adk_agents/` | ADK Agents 示例 |
| `examples/google-cloud-next-2025/` | Google Cloud Next 2025 演示 |

## 实验性项目

| 路径 | 说明 |
|------|------|
| `experimental/cbgb_benchmark/` | CBGB 基准测试 |
| `experimental/data_journeys/` | 数据之旅 |
| `experimental/functionsmith/` | FunctionSmith 工具 |
| `experimental/scienceai_ee_dataset_explorer/` | ScienceAI EE 数据集浏览器 |
