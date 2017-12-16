 元组tuple
===

元组是序列的一种，可以进行序列的基本操作。
### 序列Sequence的基本操作
- 索引：`Iter[index]`取出元素
- 切片：`Iter[start:stop:step]`生成新的元组
- 加法：`Iter1+Iter2`两个元组拼接
- 乘法：`Iter*int`元组重复
- 成员资格：`obj in Iter`返回bool类型
- 长度：`len(Iter)`元组长度
- 最值：`max(Iter)`、`min(Iter)`


### 创建元组
```Python
T = () #创建空元组
T = (a,) 或 T = a, #创建单元素元组
T = a,b,c 或T = (a,b,c) #创建元组
tuple(iterable) #将可迭代类型转换成元组
```
- 创建tuple以'(,)'为标志，括号可以省略，但逗号不可省略
- tuple可以切片，切片后还是tuple
### 元组方法（仅有两种）
- `T.count(obj)`
- `T.index(obj)`
