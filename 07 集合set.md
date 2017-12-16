集合
===

### 创建集合
- 一般方法
    ```python
    set(iter)
    ```
- 创建不可变集合
    ```python
    S = frozenset(obj)
    ```
### 集合方法
- `Set.add()`
- `Set.clear()`
- `Set.copy()`
- `Set.difference(S1) #补集` 或`Set - S1`
- `Set.difference_update()`
- `Set.discard()`
- `Set.intersection()`
- `Set.intersection_update()`
- `Set.isdisjoint()`
- `Set.issubset()`
- `Set.issuperset()`
- `Set.pop() #从集合中删除并返回任意元素。`
- `Set.remove()`
- `Set.symmetric_difference(S1) #即(Set-S1)U(S1-Set)`
- `Set.symmetric_difference_update()`
- `Set.union()`
- `Set.update(S1) #把集合S1元素并入Set`

### 集合关系
- `==`
- `!=`
- `in`
---
