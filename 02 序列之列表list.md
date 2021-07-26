列表list
===
列表是序列的一种，可以进行序列的基本操作。
### 序列Sequence的基本操作
- 索引：`Iter[index]`
- 切片：`Iter[start:stop:step]`
- 加法：`Iter1+Iter2`表示拼接
- 乘法：`Iter*int`表示重复
- 成员资格：`obj in Iter`返回bool类型
- 长度：`len(Iter)`
- 最值：`max(Iter)`、`min(Iter)`


### 创建空列表
`L = []`
### 基本操作
- 赋值`L[start:stop:step] = a`
- 删除`del L[start:stop:step]`
- 切片`L[start:stop:step]`
###列表方法
- `L.append(obj) #在L末尾添加obj`
- `L.count(obj) #计算obj出现的次数`
- `L.extend(L1) #L1扩充到L，L = L + L1`
- `L.index(obj) #obj的第一次出现的index`
- `L.insert(index,obj)#将obj插入index位置`
- `L.pop([index])#默认弹出最后一个元素，否则弹出第index个元素`
- `L.remove(obj) #移除第一个obj`
- `L.reverse()#L原地反转`
- `L.sort(key=,reverse=True/False)#按照key排序，默认False倒序`


### 列表反转的方法
- `L.reverse() #原地反转`
- `L[::-1] #生成新列表`
- `list(reversed(sequence)) #生成新列表`
- `reversed(sequence) #生成迭代器`
