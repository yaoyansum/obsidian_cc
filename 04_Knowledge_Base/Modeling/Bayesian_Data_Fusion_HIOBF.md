---
type: knowledge
title: Hybrid Inversion-Observation Bayesian Data Fusion (HIOBF)
domain: modeling
related:
  - SWAT
  - MCMC
  - Uncertainty_Quantification
source_files:
  - 99_Raw_Data/A_Hybrid_Bayesian_Data_Fusion_Framework_to_Enhance.pdf
source_count: 1
last_updated: 2026-05-07
confidence: high
---

# 混合贝叶斯数据融合框架（HIOBF）

## 来源

- **论文**: Zhou, S., Yang, P., Gan, Y., & Tan, Q. (2026). A Hybrid Bayesian data fusion framework to enhance watershed nitrogen modeling by integrating in situ observations with spatial inversion data. *Water Resources Research*, 62, e2025WR041979.
- **DOI**: 10.1029/2025WR041979

---

## 核心思想

HIOBF 框架旨在解决流域水质建模中**稀疏地面监测站点**与**高分辨率空间反演数据**的系统融合问题。核心创新在于：

1. 用贝叶斯校准框架将两类误差结构不同的数据统一融合
2. 通过**地理驱动的空间外推模型**，解决无监测子流域（ungauged sub-basins）中反演数据的误差表征难题
3. 对空间反演数据的复杂、非平稳、时空自相关误差结构进行显式建模

---

## 贝叶斯校准（Bayesian Calibration, BC）基础

### 贝叶斯定理

$$p(\theta|Z) \propto L(\theta|Z) \cdot p(\theta)$$

- $p(\theta|Z)$：后验参数分布
- $L(\theta|Z)$：似然函数，量化给定参数集下观测数据的拟合优度
- $p(\theta)$：先验分布，反映参数的先验知识

### 观测与模型输出的关系

$$Z = Y(\theta) + \varepsilon + e$$

- $Y(\theta)$：模型模拟值
- $\varepsilon$：**模型总误差**（含结构、参数、输入误差）
- $e$：**观测误差**

在实际应用中，将 $\varepsilon$ 和 $e$ 合并为**残差项** $\epsilon$，假设其服从独立、异方差的高斯分布。

### 异方差高斯误差模型

残差的标准差建模为模型输出的指数函数：

$$\sigma_t = \exp(\alpha + \beta \cdot y_t)$$

- $\alpha, \beta$：通过最大似然估计（MLE）估计的参数
- 这一设计防止极端 $y_t$ 波动导致负标准差，同时通过对数线性依赖捕获异方差性

### 对数似然函数（原位观测数据）

$$\log L(\theta|\mathbf{Y}, \phi, \mathbf{Z}) = -\frac{T}{2}\log(2\pi) - \frac{1}{2}\sum_{t=1}^{T}\log(\sigma_t^2) - \frac{1}{2}\sum_{t=1}^{T}\frac{(z_t - y_t)^2}{\sigma_t^2}$$

其中 $\phi$ 表示标准差模型中的两个超参数（$\alpha$ 和 $\beta$）。

---

## 空间反演数据建模

### 反演数据与原位观测的回归关系

由于空间反演数据 $U$ 是原位观测 $Z$ 的"不完全代理"，两者关系建模为线性回归：

$$U = \theta_0 + \theta_1 \cdot Z_{\text{virtual}} + \epsilon$$

- $\theta_0, \theta_1$：截距和斜率
- $\epsilon \sim N(0, \sigma_\epsilon^2)$：回归误差项
- 其中 $Z_{\text{virtual}}$ 是无监测子流域的"虚拟"原位观测

### 复合残差结构

将 $Z_{\text{virtual}} = Y(\theta) + \epsilon$ 代入上式，得到复合残差：

$$e = \theta_1 \cdot \epsilon + \varepsilon$$

由于 $\epsilon$ 和 $\varepsilon$ 独立且服从正态分布，复合残差 $e$ 也服从均值为 0 的正态分布，其方差为：

$$\sigma_e^2 = (\theta_1 \cdot \sigma)^2 + \sigma_\epsilon^2$$

> **关键含义**：反演数据的误差方差不是独立推断的参数，而是由**观测误差传播**和**空间回归固有不确定性**共同决定的。

---

## 空间外推模型（核心创新）

### 问题

在无监测子流域，无法直接获得 $Z_{\text{virtual}}$，也无法直接估计 $\theta_0$ 和 $\theta_1$。HIOBF 采用**地理驱动的空间外推模型**来预测这两个参数。

### 方法："Cluster-then-Regress" 框架

1. **聚类（K-Means）**：基于集水区面积（CATCH_SKM）和年均流量（DIS_AV_CMS）将训练站点划分为水文相似类型
2. **回归（XGBoost）**：在每个聚类内训练 XGBoost 模型，学习地理特征与 $(\theta_0, \theta_1)$ 的非线性关系

预测函数：

$$\hat{\theta}_0(i) = f_0(\text{CATCH\_SKM}_i, \text{DIS\_AV\_CMS}_i, \sum_{j \in S} \omega_j \cdot \text{Dist}_{i,j})$$

$$\hat{\theta}_1(i) = f_1(\text{CATCH\_SKM}_i, \text{DIS\_AV\_CMS}_i, \sum_{j \in S} \omega_j \cdot \text{Dist}_{i,j})$$

预测变量：
- **CATCH_SKM**：子流域排水面积（km²）
- **DIS_AV_CMS**：年均流量（m³/s）
- **Dist$_{i,j}$**：无监测子流域 $i$ 与有监测子流域 $j$ 之间的空间邻近度
- $\omega_j$：空间权重

### 效果

在独立验证中，预测的 $U$ 与观测 $U$ 之间的 R² 达到 0.80-0.89，RMSE 保持在 0.12-0.16 之间，证明该外推方法可靠。

---

## 时间自相关校正

### 问题

空间反演数据的残差 $e$ 存在显著的时间自相关，违背似然函数的独立性假设。

### 解决方案：AR(1) 预白化

采用一阶自回归模型（AR(1)）将原始残差转换为不相关的调整残差 $e_{ar}$：

$$e_{ar}[1] = e[1]$$

$$e_{ar}[t] = \phi \cdot e_{ar}[t-1] + (e[t] - \phi \cdot e[t-1]), \quad t = 2, 3, ..., T$$

- $\phi$：滞后 1 阶自相关系数
- 该变换后，Durbin-Watson 统计量从 ~0.05-0.22（显著自相关）提升至 ~2.34-2.55（接近理想值 2）

### 校正后的似然函数（反演数据）

$$\log L(\theta|\mathbf{Y}, \phi, \mathbf{U}) = -\frac{T}{2}\log(2\pi) - \frac{1}{2}\sum_{t=1}^{T}\log(\sigma_{e,t}^2) - \frac{1}{2}\sum_{t=1}^{T}\left(\frac{e_{ar,t}}{\sigma_{e,t}}\right)^2$$

---

## 混合融合（HIOBF）：联合似然函数

### 联合似然

假设两类数据的误差条件独立，联合对数似然为两者之和：

$$\log L(\theta, \phi|\mathbf{Z}_{\text{real}}, \mathbf{U}) = \log L(\theta|\mathbf{Y}, \phi, \mathbf{Z}_{\text{real}}) + \log L(\theta|\mathbf{Y}, \phi, \mathbf{U})$$

### 后验采样

采用 **DREAM$_{zs}$**（MCMC 算法）从高维后验分布中采样：
- 生成最多 500,000 个样本
- 舍弃前 30% 作为 burn-in
- 使用后 50% 的样本进行参数推断和不确定性量化
- 使用 **Gelman-Rubin 诊断**判断链收敛

---

## 三种融合方案对比

| 方案 | 全称 | 数据来源 | 作用 |
|------|------|---------|------|
| POBF | Pure Observation Bayesian Data Fusion | 仅原位观测（3 个子流域） | 传统方法基线 |
| PIBF | Pure Inversion Bayesian Data Fusion | 仅空间反演数据（6 个子流域） | 反演数据单独效果 |
| **HIOBF** | **Hybrid Inversion-Observation Bayesian Data Fusion** | **原位观测 + 反演数据联合** | **核心方法** |

### 主要结果

- HIOBF 相比 POBF，**NSE 平均提升 55%**（Longchuan 站点提升超过 119%）
- R² 平均提升 41%，预测区间宽度（PINAW）平均减少 9.2%
- 系统性偏差（PBIAS）从 10% 降至 8%
- 即使在仅有 1 个原位站点的情况下，融合反演数据也能使 NSE 提升约 81%

---

## 方法关键要点总结

1. **分层校准策略**：先确定性校准水文参数（DE 算法），再贝叶斯校准水质参数（MCMC）
2. **异方差处理**：用指数函数 $\sigma_t = \exp(\alpha + \beta \cdot y_t)$ 显式建模模型输出的异方差性
3. **空间外推**：用 K-Means + XGBoost 将有限监测站的信息扩展到无监测区域
4. **自相关校正**：AR(1) 预白化确保似然函数的统计有效性
5. **联合似然**：条件独立假设下，原位观测和反演数据贡献各自似然函数
6. **MCMC 采样**：DREAM$_{zs}$ 算法高效探索高维后验分布

---

## 在我研究中的用途

- 可借鉴将**遥感反演数据**（如湖泊 DOC/DIC 反演产品）与**原位观测数据**（野外采样点）融合的思路
- 空间外推模型（K-Means + XGBoost）可用于将有限采样点的水质推断扩展到更大区域
- AR(1) 预白化处理对时间序列数据建模有通用参考价值
- 联合似然框架可推广到其他多源异构数据融合场景

---

## 相关页面

- [[MCMC]]
- [[Uncertainty_Quantification]]
- [[SWAT]]
- [[Machine_Learning]]
