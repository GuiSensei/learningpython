 字符串str
 ===
字符串是序列的一种，可以进行序列的基本操作。
### 序列Sequence的基本操作
- 索引：`Iter[index]`取出元素
- 切片：`Iter[start:stop:step]`生成新的元组
- 加法：`Iter1+Iter2`两个元组拼接
- 乘法：`Iter*int`元组重复
- 成员资格：`obj in Iter`返回bool类型
- 长度：`len(Iter)`元组长度
- 最值：`max(Iter)`、`min(Iter)`

###字符串方法
- 查找子串，返回最左端索引：`S.find(sub[, start[, end]])-> int`
- 字符串大小写
    ```python
    S.upper()#S中的字母大写
    S.lower() #S中的字母小写
    S.capitalize() #首字母大写
    S.istitle() #S是否是首字母大写的
    S.isupper() #S中的字母是否便是大写
    S.islower() #S中的字母是否全是小写
    ```
- 字符串去空格
    ```python
    S.strip()去掉字符串的左右空格
    S.lstrip()去掉字符串的左边空格
    S.rstrip()去掉字符串的右边空格
    ```
- 字符串其他方法
    ```python
    S.center(width, [fillchar]) #中间对齐
    S.count(substr, [start, [end]]) #计算substr在S中出现的次数
    S.expandtabs([tabsize]) #把S中的tab字符替换没空格，每个tab替换为tabsize个空格，默认是8个
    S.isalnum() #是否全是字母和数字，并至少有一个字符
    S.isalpha() #是否全是字母，并至少有一个字符
    S.isspace() #是否全是空白字符，并至少有一个字符    
    S.ljust(width,[fillchar]) #输出width个字符，S左对齐，不足部分用fillchar填充，默认的为空格。
    S.rjust(width,[fillchar]) #右对齐
    S.splitlines([keepends]) #把S按照行分割符分为一个list，keepends是一个bool值，如果为真每行后而会保留行分割符。
    S.swapcase() #大小写互换
    S.replace(old, new[, count]) -> str，将old替换为new
    S.split(sep=None, maxsplit=-1) -> list of strings，join的逆方法
    S.translate(table) -> str，替换单个字符，但是可以同时替换
    S.join(iterable) #将S加到iterable中
    ```



### 字符串格式化
1. 方式一：%格式化
    - `%s`    字符串 (采用str()的显示)
    - `%r`    字符串 (采用repr()的显示)
    - `%c`    单个字符
    - `%b`    二进制整数
    - `%d`    十进制整数
    - `%i`    十进制整数
    - `%o`    八进制整数
    - `%x`    十六进制整数
    - `%e`   指数 (基底写为e)
    - `%E`    指数 (基底写为E)
    - `%f`    浮点数
    - `%F`    浮点数，与上相同
    - `%g`    指数(e)或浮点数 (根据显示长度)
    - `%G`   指数(E)或浮点数 (根据显示长度)
    - `%%`    字符"%"
    > 注：
    >   - 整体格式化：`string % tuple`
    >   - 字段宽度和精度：`%10.2f`，字段宽度为10，精度（必须有.）为2
    > - 可以使用*表示宽度和精度：`'%*.*s' % (6,4,'asdgadfh')`
    > - 宽度不足用0填充`'%010.2f' % math.pi`、`'%0*.*f' % (8,4,1.23456789)`
    > - 左对齐`-`：`'%-10.2f' % math.pi`
    > - 添加正负号`+`：`'%+10.2f' % math.pi`
    > - 空格表示在正数前加上空格：`'% 10.2f' % math.pi`

2. 方式二：format方法（**推荐使用**）
    - `:`后面与`%`类似：`{0:10}`
    - 一般写法：`'{0}, {1}, {2}'.format('a', 'b', 'c') #{}中不写数字，默认从0开始`
    - 访问指定位置：`'{2}, {1}, {0}'.format('a', 'b', 'c')`、`'{0}{1}{0}'.format('abra', 'cad')`
    - `{}`转义：使用两层，如`{{{0}}}`
    - 访问可变参数：`'{2}, {1}, {0}'.format(*'abc') `
    - 访问关键字参数（两种方式）：

         ```python
         >>> 'Coordinates: {latitude}, {longitude}'.format(latitude='37.24N', longitude='-115.81W')
         ```

         ```python
         >>> coord = {'latitude': '37.24N', 'longitude': '-115.81W'}  
         >>> 'Coordinates: {latitude}, {longitude}'.format(**coord)
         ```
    - 访问函数属性
        ```python
        >>> c = 3-5j
        >>> ('The complex number {0} is formed from the real part {0.real} and the imaginary part {0.imag}.').format(c)
        ```
    - 访问可迭代类型的参数项items
        ```python
        >>> coord = (3, 5)
        >>> 'X: {0[0]};  Y: {0[1]}'.format(coord)
        ```    
    - 替换`%s`和`%r`字符串
        ```python
        >>> "repr() shows quotes: {!r}; str() doesn't: {!s}".format('test1', 'test2')
        ```  
    - 对齐文本并指定宽度
        ```python
        >>> '{:<30}'.format('left aligned')
        >>> '{:>30}'.format('right aligned')
        >>> '{:^30}'.format('centered')
        '{:*^30}'.format('centered')  # use '*' as a fill char
        ```  
    - 替换`%+f`、`%-f`、和`% f`并指定符号
        ```python
        >>> '{:+f}; {:+f}'.format(3.14, -3.14)  # show it always
        '+3.140000; -3.140000'
        >>> '{: f}; {: f}'.format(3.14, -3.14)  # show a space for positive numbers
        ' 3.140000; -3.140000'
        >>> '{:-f}; {:-f}'.format(3.14, -3.14)  # show only the minus -- same as '{:f}; {:f}'
        '3.140000; -3.140000'
        ```
    - 替换`%x`、`%o`并转换进制
        ```python
        >>> # format also supports binary numbers
        >>> "int: {0:d};  hex: {0:x};  oct: {0:o};  bin: {0:b}".format(42)
        'int: 42;  hex: 2a;  oct: 52;  bin: 101010'
        >>> # with 0x, 0o, or 0b as prefix:
        >>> "int: {0:d};  hex: {0:#x};  oct: {0:#o};  bin: {0:#b}".format(42)
        'int: 42;  hex: 0x2a;  oct: 0o52;  bin: 0b101010'
        ```  
    - 使用逗号作为千的分隔符    
        ```python
        >>> '{:,}'.format(1234567890)
        '1,234,567,890'
        ```
    - 百分数表示
        ```python
        >>> points = 19
        >>> total = 22
        >>> 'Correct answers: {:.2%}'.format(points/total)
        'Correct answers: 86.36%'
        ```
    - 使用特定类型的格式化        
        ```python
        >>> import datetime
        >>> d = datetime.datetime(2010, 7, 4, 12, 15, 58)
        >>> '{:%Y-%m-%d %H:%M:%S}'.format(d)
        '2010-07-04 12:15:58'
        ```
    - 嵌套参数和更复杂的示例
        ```python
        >>> for align, text in zip('<^>', ['left', 'center', 'right']):
        ...     '{0:{fill}{align}16}'.format(text, fill=align, align=align)
        ...
        'left<<<<<<<<<<<<'
        '^^^^^center^^^^^'
        '>>>>>>>>>>>right'
        >>>
        >>> octets = [192, 168, 0, 1]
        >>> '{:02X}{:02X}{:02X}{:02X}'.format(*octets)
        'C0A80001'
        >>> int(_, 16)
        3232235521
        >>>
        >>> width = 5
        >>> for num in range(5,12):
        ...     for base in 'dXob':
        ...         print('{0:{width}{base}}'.format(num, base=base, width=width), end=' ')
        ...     print()
        ...
            5     5     5   101
            6     6     6   110
            7     7     7   111
            8     8    10  1000
            9     9    11  1001
           10     A    12  1010
           11     B    13  1011

        ```

3. 方式三：模板字符串
    ```Python
    from string import Template
    S = Template('$x,nihao$x!')    
    S.substitute(x = '我')#打印结果：'我,nihao我!'
    ```
    - 替换的是单词的一部分，需要加{}:
        ```Python
        S = Template('${x}tion')
        ```
    - 美元符号需要两个$:
        ```Python
        S = Template('$$')
        ```
    - 还可以用dict
        ```Python
        S = Template('$A is $B')
        d = {'A':'wo','B':'ni'}
        S.substitute(d)
        ```


###### string模块（与上述方法类似）
```python
import string
```


> 注：字符串不可改变，只能通过生成新的字符串覆盖旧的字符串，而不能在原先的字符串上修改。
