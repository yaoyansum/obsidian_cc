# ee.Number, ee.Array & ee.Kernel 方法参考

## ee.Number (90 个方法)

源文件: `samples/javascript/apidocs/ee-number-*.js` / `samples/python/apidocs/ee_number_*.py`

### 算术运算
- `add` — 加
- `subtract` — 减
- `multiply` — 乘
- `divide` — 除
- `mod` — 取模
- `pow` — 幂
- `sqrt` — 平方根
- `cbrt` — 立方根
- `abs` — 绝对值
- `ceil` — 向上取整
- `floor` — 向下取整
- `round` — 四舍五入
- `clamp` — 限值
- `signum` — 符号
- `hypot` — 斜边
- `exp` — 指数
- `log` — 自然对数
- `log10` — 常用对数

### 三角函数
- `sin` / `sinh` — 正弦/双曲正弦
- `cos` / `cosh` — 余弦/双曲余弦
- `tan` / `tanh` — 正切/双曲正切
- `asin` — 反正弦
- `acos` — 反余弦
- `atan` — 反正切
- `atan2` — 二参数反正切

### 特殊函数
- `digamma` — Digamma 函数
- `trigamma` — Trigamma 函数
- `gamma` — Gamma 函数
- `gammainc` — 不完全 Gamma 函数
- `erf` — 误差函数
- `erfc` — 互补误差函数
- `erfinv` — 逆误差函数
- `erfcinv` — 逆互补误差函数
- `lanczos` — Lanczos 函数

### 位运算
- `bitcount` — 位计数
- `bitwiseand` — 按位与
- `bitwisenot` — 按位非
- `bitwiseor` — 按位或
- `bitwisexor` — 按位异或
- `leftshift` — 左移
- `rightshift` — 右移

### 比较运算
- `eq` — 等于
- `neq` — 不等于
- `gt` — 大于
- `gte` — 大于等于
- `lt` — 小于
- `lte` — 小于等于

### 逻辑运算
- `and` — 与
- `or` — 或
- `not` — 非

### 类型转换
- `byte` — 转字节（8 位）
- `double` — 转双精度浮点
- `float` — 转单精度浮点
- `int` — 转整型
- `int8` / `int16` / `int32` — 转指定位宽整型
- `long` — 转长整型
- `short` — 转短整型
- `uint8` / `uint16` / `uint32` — 转无符号整型
- `tobyte` / `todouble` / `tofloat` / `toint` 等 — 类型转换系列

### 其他
- `aside` — 旁路操作
- `evaluate` — 求值
- `expression` — 表达式
- `first` — 取首个
- `firstnonzero` — 首个非零值
- `format` — 格式化
- `getinfo` — 获取信息
- `max` — 取最大值
- `min` — 取最小值
- `parse` — 解析字符串
- `serialize` — 序列化
- `unitscale` — 单位缩放

---

## ee.Array (62 个方法)

源文件: `samples/javascript/apidocs/ee-array-*.js` / `samples/python/apidocs/ee_array_*.py`

### 创建
- `identity` — 单位矩阵

### 算术运算
- `add` / `subtract` / `multiply` / `divide` / `mod` / `pow`
- `dotproduct` — 点积

### 数学函数
- `abs` / `cbrt` / `ceil` / `floor`
- `cos` / `cosh` / `sin` / `sinh` / `tan` / `tanh`
- `acos` / `asin` / `atan`
- `exp` / `log` / `log10`
- `digamma` / `erf` / `erfc` / `erfcinv` / `erfinv`

### 比较与逻辑
- `eq` / `gt` / `gte` / `lt` / `lte` / `neq`
- `and` / `or` / `not`

### 操作
- `accum` — 累积
- `argmax` — 最大值索引
- `bitstoarray` — 位转数组
- `bitcount` — 位计数
- `bitwise_and` / `bitwise_or` / `bitwise_xor` / `bitwise_not`
- `byte` — 转字节
- `cat` — 拼接
- `cut` — 切割
- `eigen` — 特征值
- `first` / `first_nonzero` / `firstnonzero` — 首个元素
- `get` — 取值
- `mask` — 掩膜
- `max` / `min` — 最大/最小值
- `slice` — 切片

---

## ee.Kernel (22 个方法)

源文件: `samples/javascript/apidocs/ee-kernel-*.js` / `samples/python/apidocs/ee_kernel_*.py`

- `add` — 核相加
- `chebyshev` — 切比雪夫核
- `circle` — 圆形核
- `compass` — 罗盘核
- `cross` — 十字形核
- `diamond` — 菱形核
- `euclidean` — 欧几里得核
- `fixed` — 固定值核
- `gaussian` — 高斯核
- `inverse` — 反距离核
- `kirsch` — Kirsch 边缘检测核
- `laplacian4` — 4 邻域拉普拉斯核
- `laplacian8` — 8 邻域拉普拉斯核
- `manhattan` — 曼哈顿距离核
- `octagon` — 八边形核
- `plus` — 加号形核
- `prewitt` — Prewitt 边缘检测核
- `rectangle` — 矩形核
- `roberts` — Roberts 边缘检测核
- `rotate` — 旋转核
- `sobel` — Sobel 边缘检测核
- `square` — 正方形核
