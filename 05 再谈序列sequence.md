
序列Sequence
===
## 概述
序列是python中最基本的数据结构，序列中的每一个元素分配一个序号——元素的位置，即索引，第一个索引为0，第二个为1，依次类推，也可倒序，最后一个索引为-1，倒数第二个索引为-2，依次类推。


## 内建序列（6种）
#### 1. 列表


#### 2. 元组

#### 3. 字符串


> ##### list、tuple、string的异同与相互转换
> 1) 异同
> - list可以修改，tuple、string不可以修改
> - tuple可内嵌list达到修改的目的，string可使用切片方式修改
> 2) 相互转换
> - list to tuple：`tuple(list)`
> - tuple to list：`list(tuple)`
> - list to string：`string.split()`
> - string to list：`'[sep]'.join(list)`

#### 4. Unicode字符串

#### 5. buffer对象

#### 6. range对象

```python
a = range(start, stop[, step]) #返回一个range类型
```
可将其转换成list
```python
a = list(range(start, stop[, step])) #返回一个range类型
```
> 可以使用成员函数`in`、索引`r.index()`、查找index位置元素`r[index]`、切片`r[start,stop,step]`


## 序列Sequence的基本操作
- 索引：`Iter[index]`
- 切片：`Iter[start:stop:step]`
- 加法：`Iter1+Iter2`表示拼接
- 乘法：`Iter*int`表示重复
- 成员资格：`obj in Iter`返回bool类型
- 长度：`len(Iter)`
- 最值：`max(Iter)`、`min(Iter)`
