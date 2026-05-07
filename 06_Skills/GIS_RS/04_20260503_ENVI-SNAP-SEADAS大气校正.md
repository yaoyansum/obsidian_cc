# ENVI / SNAP / SEADAS 大气校正

## ENVI

### FLAASH

**Reference：**

[ENVI学习总结（五）—辐射定标和大气校正(FLAASH/QUAC)](https://blog.csdn.net/weixin_43626557/article/details/103942766)

FLAASH (Fast Line-of-sight Atmospheric Analysis of Spectral Hypercubes) 是基于 MODTRAN 的辐射传输模型的大气校正方法。

**主要界面：**

![](https://cdn.nlark.com/yuque/0/2024/png/49668464/1729582680190-6878c4f2-487a-459f-a754-9b9bd8eacf37.png)

**基本设置：**

![](https://cdn.nlark.com/yuque/0/2024/png/49668464/1729582267911-5c3e224e-5fb6-4c89-903a-ffedbcdb92da.png)

**高级设置 (Advanced Settings)：**

包括：
- TOMS 光谱仪定义
- 观测几何（天顶角、方位角）
- 气溶胶参数
- 海拔高度
- CO₂ 混合比
- 瓦片处理大小
- 邻域校正
- MODTRAN 分辨率
- 输出反射率缩放因子
- DISORT 多散射模型

![](https://cdn.nlark.com/yuque/0/2024/png/49668464/1729582241995-13b30c85-3122-4147-bb97-abaa5ef76975.png)

### QUAC (Quick Atmospheric Correction)

QUAC 是一种快速大气校正方法，基于图像本身的统计信息，不需要传感器参数和大气参数，适用于快速处理。

> 简单快速，精度低于 FLAASH。

![](https://cdn.nlark.com/yuque/0/2024/png/49668464/1729583162502-37e0323f-7a74-41ad-a91d-a01695d35bdc.png)

---

## SNAP

SNAP (Sentinel Application Platform) 是 ESA 提供的 Sentinel 卫星数据处理平台。

### C2RCC (Case 2 Regional Coast Colour)

C2RCC 是基于神经网络的大气校正方法，适用于 Case-2 水体（近岸、内陆水体）。

**Reference：**

[Python调用C2RCC实现批量数据的大气校正](https://blog.csdn.net/mrzhy1/article/details/108410567)

![](https://cdn.nlark.com/yuque/0/2024/png/49668464/1730104534724-6b5e1a1d-2c4d-45b5-8adc-61e6c608729f.png)

### FUB

(待补充)

### iCOR (插件)

iCOR (Image Correction for atmospheric effects) 是 SNAP 的大气校正插件。

**Reference：** [iCORpluginUserManual_OLCIv3.0.pdf](https://f.hubspotusercontent00.net/hubfs/2834550/iCOR_2021/iCORpluginUserManual_OLCIv3.0.pdf)

### Sen2Cor (插件)

Sen2Cor 是 Sentinel-2 的大气校正和场景分类处理器，可生成 L2A 产品。

---

## SEADAS

SEADAS 是 NASA 的海洋色彩数据处理系统，基于 SNAP 平台。

**References：**

- [使用SeaDas对Sentinel-3(OLCI)、Sentinel-2(MSI)进行大气校正](https://blog.csdn.net/mrzhy1/article/details/109158112)
- [seadas/seadas-toolbox: SeaDAS toolbox for SNAP](https://github.com/seadas/seadas-toolbox)
- [SeaDAS OCSSW及大气矫正 2022年使用指北](https://lifeodyssey.github.io/posts/182a5f48.html)
- [NASA 海洋色彩](https://oceandata.sci.gsfc.nasa.gov/ocssw/)
