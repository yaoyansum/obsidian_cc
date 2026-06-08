# ee.Feature, ee.FeatureCollection & ee.Filter 方法参考

## ee.Feature (1 个方法)

源文件: `samples/javascript/apidocs/ee-feature-buffer.js` / `samples/python/apidocs/ee_feature_buffer.py`

- `buffer` — 缓冲区

---

## ee.FeatureCollection (61 个方法)

源文件: `samples/javascript/apidocs/ee-featurecollection-*.js` / `samples/python/apidocs/ee_featurecollection_*.py`

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

### 过滤
- `filter` — 通用过滤
- `filterbounds` — 空间范围过滤
- `filterdate` — 时间范围过滤
- `distinct` — 去重
- `first` — 首个元素
- `limit` — 限制数量
- `sort` — 排序

### 空间操作
- `bounds` — 边界
- `distance` — 距离计算
- `geometry` — 获取几何
- `kriging` — 克里金插值
- `union` — 合并几何

### 分类与验证
- `classify` — 分类
- `cluster` — 聚类
- `errormatrix` — 误差矩阵
- `evaluate` — 验证评估

### 集合操作
- `aside` — 旁路操作
- `copyproperties` — 复制属性
- `draw` — 绘制
- `flatten` — 展平嵌套集合
- `iterate` — 迭代
- `map` — 映射函数
- `merge` — 合并集合
- `propertynames` — 属性名列表
- `randomcolumn` — 添加随机列
- `reducecolumns` — 列归约
- `reducetoimage` — 归约为图像
- `remap` — 值重映射
- `select` — 选择属性
- `serialize` — 序列化
- `set` — 设置属性
- `size` — 集合大小

### 访问与转换
- `get` — 获取属性
- `getarray` — 获取数组属性
- `getdownloadurl` — 获取下载 URL
- `getinfo` — 获取信息
- `getmap` — 获取地图（tiles）
- `getnumber` — 获取数值属性
- `getstring` — 获取字符串属性
- `makearray` — 创建数组列
- `todictionary` — 转字典
- `tolist` — 转列表
- `style` — 样式设置

### BigQuery 集成
- `loadbigquerytable` — 加载 BigQuery 表
- `runbigquery` — 运行 BigQuery 查询

---

## ee.Filter (12 个方法)

源文件: `samples/javascript/apidocs/ee-filter-*.js` / `samples/python/apidocs/ee_filter_*.py`

- `bounds` — 空间边界过滤
- `calendarrange` — 日历范围过滤
- `date` — 日期过滤
- `eq` / `equals` — 相等
- `greaterthan` — 大于
- `greaterthanorequals` — 大于等于
- `hastype` — 类型过滤
- `lessthan` — 小于
- `lessthanorequals` — 小于等于
- `maxdifference` — 最大差值
- `notequals` — 不等于
