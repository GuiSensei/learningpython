字典dict
===
### 创建字典
- 直接创建
    ```python
    D = {key1:value1,key2:value2,key3:value3,...}
    ```
- 序列创建
    ```python
    items = [('name','Ai'),('age','12')]
    D = dict(items)
    ```
- 关键字参数创建
    ```python
    D = dict(name = 'Ai', age = 12)    
    ```
### 字典的基本操作
- `len(D)`
- `D[key]`
- `D[key] = value`
- `del D[key]`
- 成员资格：`key in D #只能查找键`
- key类型：任意的不可变量，如float、int、str、tuple
### 字典方法
- `D.clear()`
- `D.copy() #a shallow copy of D`
- `D.get(key[,d])`
- `D.fromkeys(iterable, value=None, /)`
- `D.items()`
- `D.keys()`
- `D.pop(key)`
- `D.popitem() #弹出最后一个`
- `D.setdefault()`
- `D.update()`
- `D.values()`
