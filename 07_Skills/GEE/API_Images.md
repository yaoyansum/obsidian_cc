# ee.Image & ee.ImageCollection 方法参考

## ee.Image (56 个方法)

源文件: `samples/javascript/apidocs/ee-image-*.js` / `samples/python/apidocs/ee_image_*.py`

### 算术运算
- `add` — 图像相加
- `subtract` — 图像相减
- `multiply` — 图像相乘
- `divide` — 图像相除
- `mod` — 取模
- `pow` — 幂运算
- `gt` — 大于（比较运算）
- `not` — 逻辑非

### 波段操作
- `addbands` — 添加波段
- `select` — 选择波段
- `rename` — 重命名波段
- `remap` — 值重映射

### 数组操作
- `arrayaccum` — 数组累积
- `arrayargmax` — 数组 argmax
- `arraycat` — 数组拼接
- `arraydimensions` — 数组维度
- `arraydotproduct` — 数组点积
- `arrayflatten` — 数组展平
- `arrayget` — 数组取值
- `arraylength` — 数组长度
- `arraylengths` — 各维度长度
- `arraymask` — 数组掩膜
- `arraypad` — 数组填充
- `arrayproject` — 数组投影
- `arrayreduce` — 数组归约
- `arrayrepeat` — 数组重复
- `arrayreshape` — 数组重塑
- `arrayslice` — 数组切片
- `arraysort` — 数组排序
- `arraytranspose` — 数组转置

### 掩膜与裁剪
- `mask` — 掩膜
- `unmask` — 取消掩膜
- `updatemask` — 更新掩膜
- `selfmask` — 自掩膜（0/NoData）
- `clip` — 裁剪
- `cliptoboundsandscale` — 裁剪到边界并缩放
- `cliptocollection` — 裁剪到集合边界

### 空间分析
- `distance` — 距离计算
- `pixelarea` — 像素面积
- `pixellonlat` — 像素经纬度（图像）

### 分类与回归
- `classify` — 分类

### 表达式
- `expression` — 波段运算表达式
- `normalizeddifference` — 归一化差值（NDVI 等）

### 投影与重投影
- `changeproj` — 变更投影
- `reproject` — 重投影

### 采样与区域统计
- `sample` — 像素采样
- `sampleregions` — 区域采样
- `reduceregion` — 区域归约
- `reduceregions` — 多区域归约

### 输入/输出
- `constant` — 创建常量图像
- `loadgeotiff` — 加载 GeoTIFF
- `getdownloadurl` — 获取下载 URL
- `toarray` — 转数组

### 其他
- `arrayaccum` — 数组累积叠加

---

## ee.ImageCollection (46 个方法)

源文件: `samples/javascript/apidocs/ee-imagecollection-*.js` / `samples/python/apidocs/ee_imagecollection_*.py`

### 聚合统计
- `aggregate_array` — 聚合为数组
- `aggregate_count` — 计数
- `aggregate_count_distinct` — 非重复计数
- `aggregate_first` — 首个
- `aggregate_histogram` — 直方图
- `aggregate_max` — 最大值
- `aggregate_mean` — 均值
- `aggregate_min` — 最小值
- `aggregate_product` — 乘积
- `aggregate_sample_sd` — 样本标准差
- `aggregate_sample_var` — 样本方差
- `aggregate_stats` — 全统计
- `aggregate_sum` — 求和
- `aggregate_total_sd` — 总体标准差
- `aggregate_total_var` — 总体方差

### 图像合成
- `max` — 逐像素最大值
- `mean` — 逐像素均值
- `median` — 逐像素中位数
- `min` — 逐像素最小值
- `mode` — 逐像素众数
- `mosaic` — 镶嵌
- `product` — 逐像素乘积
- `qualitymosaic` — 质量镶嵌
- `sum` — 逐像素求和
- `reducetoimage` — 归约为图像

### 过滤
- `filter` — 通用过滤
- `filterbounds` — 空间范围过滤
- `filterdate` — 时间范围过滤
- `filtermetadata` — 元数据过滤

### 集合操作
- `count` — 集合大小
- `first` — 第一张图像
- `fromimages` — 从图像列表构造
- `merge` — 合并集合
- `select` — 选择波段
- `set` — 设置属性
- `size` — 集合大小（与 count 类似）
- `sort` — 排序

### 数据访问
- `get` — 获取属性
- `getarray` — 获取数组属性
- `getnumber` — 获取数值属性
- `getregion` — 获取区域数据
- `getstring` — 获取字符串属性

### 转换
- `toarrayperband` — 按波段转数组
- `tobands` — 转多波段图像
- `todictionary` — 转字典
- `tolist` — 转列表
