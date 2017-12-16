下载：https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy
安装：`pip install 模块名`

`import numpy as np` #库的导入，这是约定俗成的写法

## numpy特点
- 一个强大的N维数组对象ndarray
- 广播功能函数
- 整合C++/C/Fortran代码的工具
- 线性代数、傅立叶变换、随机生成的功能
- 是Scipy、Pandas等的基础
- 优势：利用数组对象可以去掉不必要的循环，使一维向量更像单个数据

## 基本函数
`a = np.array(list)`  #生成ndarray数组
- 轴(axis)：数据的维度
- 秩(rank)：轴的数量
 #### array方法
- `a.ndim` 秩
- `a.shape` 尺度，矩阵的n行m列
- `a.size`  对象中元素的个数，即n*m的值
- `a.dtype` 对象中元素的类型，类型有：`bool`、`intc`、`intp`、`int8`、`int16`、`int32`、`int64`、`uint8`、`uint16`、`uint32`、`uint64`、`float16`、`float32`、`float64`、`complex64`复数、`complex128` 复数（实部`.real`，虚部`.imag`）                    
- `a.itemsize` #对象中每个元素的大小，以字节为单位
例：
```python
a = np.array([[1,2,3,4],
              [5,6,7,8]])
print(a)
print(a.ndim)     #输出结果为：2
print(a.shape)    #输出结果为：(2, 4)
print(a.size)     #输出结果为：8
print(a.dtype)    #输出结果为：int32
print(a.itemsize) #输出结果为：4
```
## ndarry数组的创建

1. 从python中的list/tuple等类型创建
    - `x = np.array(list/tuple)`
    - `x = np.array(list/tuple, dtype = np.float32)` 当不指定dtype时，自动匹配dtype类型
        - 列表类型 `a = np.array([1,2,3,4,5])`
        - 元组类型 `b = np.array((6,7,8,9,10))`
        - 列表/元组混合类型 `c = np.array([[1,2,3,4],(5,6,7,8)]) `
            ```python
            >>>a = np.array([[1,2,3,4],(5,6,7,8)])
            [[1 2 3 4]
             [5 6 7 8]]
            ```
2. 使用NumPy中的函数
- `np.empty(shape[, dtype, order])` 生成shape形状的数组，元素为随机数
- `np.empty_like(a[, dtype, order, subok])`以数组a的形状生成数组，元素为随机数
- `np.arange([start,] stop[, step,][, dtype])` 返回start到stop-1,步长为step的一维数组
- `np.ones(shape[, dtype, order])` 生成shape形状的全1数组
- `np.ones_like(a[, dtype, order, subok])` 根据数组a的shape创建一个全1数组
- `np.zeros(shape[, dtype, order])` 生成shape形状的全0数组
- `np.zeros_like(a[, dtype, order, subok])` 根据数组a的shape创建一个全0数组
- `np.full(shape, val[, dtype, order])` 生成shape形状的全val的数组
- `np.full_like(a, val[, dtype, order, subok])` 根据数组a的shape创建一个全val数组
- `np.eye(N[, M, k, dtype])` 生成N行M列（缺省为N）二维矩阵，第k对角线为1，其余为0
- `np.identity(n, dtype=None)`  生成n阶方阵，主对角线为1
    > 其中，`shape`为`(a,b,c,d,...)`    
    ```python
    >>>a = np.arange(10)
    [0 1 2 3 4 5 6 7 8 9]
    >>>a = np.ones((3,4))
    [[ 1.  1.  1.  1.]
     [ 1.  1.  1.  1.]
     [ 1.  1.  1.  1.]]
    >>>a = np.zeros((4,5))
    [[ 0.  0.  0.  0.  0.]
     [ 0.  0.  0.  0.  0.]
     [ 0.  0.  0.  0.  0.]
     [ 0.  0.  0.  0.  0.]]
    >>>a = np.full((2,3),4)
    [[4 4 4]
     [4 4 4]]
    >>>a = np.eye(4)
    [[ 1.  0.  0.  0.]
     [ 0.  1.  0.  0.]
     [ 0.  0.  1.  0.]
     [ 0.  0.  0.  1.]]
    >>>b = np.ones_like(a)
    >>>c = np.zeros_like(a)
    >>>d = np.full_like(a,3)
    ```

3. 使用Numpy中其他的函数
- `np.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None)`
    - 从`start`到`stop`等间距地填充`num`个数据，
    - `endpoint`表示是否包含`stop`，默认为`True`
    - `retstep`默认为`False`，若为`True`，则返回数组和步长的组合
- `np.concatenate((a1, a2, ...), axis=0)` 将a1、a2等数组按axis合并到一个数组

```python
>>>a = np.linspace(1, 10, 5, endpoint = False)
[ 1.   2.8  4.6  6.4  8.2]
>>>a = np.linspace(1, 10, 5, endpoint = True)
[  1.     3.25   5.5    7.75  10.  ]
```
## ndarray数组的变换

1. ndarray数组的维度变换
    - np.reshape(a, newshape, order)#
        - 或a.reshape(newshape)#不修改a,创建新数组
    - np.resize(a, newshape)
        - 或a.resize(newshape)#直接修改数组a
    - np.swapaxes(a, axis1, axis2) #将a的维度进行调换
        - 或a.swapaxes(ax1, ax2)
    - a.flatten() #将数组a降到一维

2. ndarray数组的类型变换
    - `a.astype(dtype, order, casting='unsafe', subok=True, copy=True)`将a中数据转变成dtype类型
    - `a.tolist()`将数组a转变为list

## ndarray数组的索引和切片
一维数组的索引和切片与list相似
多维数组的索引：`a[第一维索引值,第二维索引值,第三维索引值,...]`
多维数组的切片：`a[第一维切片,第二维切片,第三维切片,...]`

## ndarray数组的运算
1. 一元函数
    - `np.abs(x)`
    - `np.sqrt(x)`
    - `np.square(x)`
    - `np.log(x)/np.log10(x)/np.log23(x)`
    - `np.ceil(x)/np.fllor(x)`
    - `np.rint(x)`
    - `np.modf(x)`
    - `np.cos(x)/np.sin(x)/np.tan(x)/np.cosh(x)/np.sinh(x)/np.tanh(x)`
    - `np.exp(x)`
    - `np.sign(x)` #返回各元素的符号值 1（+）， 0 ，-1（-）

2. 二元函数

    - `+`、`-`、`*`、`/`
    - `np.maximum(x, y)`/`np.fmax(x ,y)`
    - `np.minimun(x, y)`/`np.fmin(x ,y)`
    - `np.mod(x ,y)`#计算x和y的模
    - `np.copysign(x, y)`#将y中的各元素符号赋给x中的对应元素
    - `>`、`<`、`>=`、`<=`、`==`、`!=`

## CSV文件的写入和读入

1. 以下两个函数只能存储一维和二维数据
    - `np.savetxt(fname, X,[fmt='%.18e', delimiter=' ', newline='\n', header='', footer='', comments='# '])`
    - `np.loadtxt(fname,[dtype=np.int, comments='#', delimiter=None, converters=None, skiprows=0, usecols=None, unpack=False, ndmin=0])`
        - `fname`：要写入或读取的文件、文件名或生成器，也可以是.gz和.bz2的压缩文件
        - `X`：写进去的数组名称
        - `fmt`：写入的格式，可以是统一，也可对各元素分别进行格式化
        - `delimiter`：分割列符号
        - `newline`：分割行符号
        - `header`：写入表头
        - `footer`：写入表尾
        - `comments`：表头和表尾的注释文字
        - `dtype`：读取的数据类型
        - `unpack`：默认为`false`，表示读入同一数组变量；`true`表示读入的数据写进不同变量

2. 任意维度数据的存储
    - `ndarray.tofile(file[, sep = '', format = '%s'])`
        - `ffile`：文件或字符串
        - `sep`：分隔符
        - `format`：输出格式
    - `np.fromfile(file[, dtype = np.float, count = -1, sep = ''])`
        - `file`：文件或字符串
        - `count`：读入数据的数目，-1表示读取全部数据

    - `np.save('file.npy', array)`将数组array写到file.npy中(只能是.npy文件)
    - `np.load('file.npy')`将file.npy文件读取出来
    ```python
    a = np.arange(100).reshape(4,5,5)
    np.save('a.txt',a)
    b = np.load('a.txt')
    print(b)
    ```

## NumPy库的随机数子库random
- `np.random.rand(d0,d1,...,dn)` 根据shape(d0-dn)创建[0,1)之间的随机数组，所有数据符合均匀分布
- `np.random.randn(d0,d1,...,dn)`根据shape(d0-dn)创建[0,1)之间的随机数组，所有数据符合标准正态分布
- `np.random.randint(low[,high,shape,dtype])`根据shape创建[low,high)之间的随机整数或整数数组
- `np.random.seed(s)`随机数种子，s是给定的种子值

- `np.random.shuffle(x)` 根据数组x的第一轴进行随机排列，改变数组x
- `np.random.permutation(x)`根据数组x的第一轴进行随机排列，不改变数组x
- `np.random.choice(a[, size, replace, p])` 从一维数组a中以概率p抽取元素，形成size形状的新数组，replace表示是否可以重复使用元素

- `np.random.uniform(low, high, size)`产生均匀分布的数组，low起始值，high结束值，size形状
- `np.random.normal(loc, scale, size)`产生正态分布的数组，loc均值，scale标准差，size形状
- `np.random.poissom(lam, size)` 产生泊松分布分布的数组，lam随机时间发生概率，size形状


# 梯度函数
`np.gradient(f, *varargs, **kwargs)`

# 运算
`np.dot()` #矩阵运算
