`itertools`模块（都是迭代器）
===
1. 无限迭代器
    - `itertools.count(start, [step])`：从start开始，以step为步长（默认为1），生成一个无限的迭代器，可用`for`循环或`next()`读取。
    - `itertools.cycle(p)` ：无限循环`p`中的元素
    - `itertools.repeat(elem [,n])` ：重复`elem`元素`n`次（默认无限次），超出`n`次将报错。
2. 按条件终止的迭代器
    - `itertools.accumulate(p [,func]) `：以`func`函数对`p`累进（默认累加），
    - `itertools.chain(*iterable)`：将`*iterable`中元素依次取出（可多个`iterable`）。
    - `itertools.chain.from_iterable(iterable)`将`iterable`中的元素依次取出(只能1个`iterable`，但可以将多个组装成一个，功能同上)。
    - `itertools.compress(data, selectors)`按照`selectors`对应`True`或者`False`确定是否保留`data`中的元素。
    - `itertools.dropwhile(pred, seq)`：当`seq`中的元素不满足`pred`条件时开始输出之后所有的元素。
    - `itertools.filterfalse(pred, seq)`：输出当`seq`中的元素不满足`pred`条件时的所有元素。与`filter()`类似。
    - `itertools.groupby(iterable[, keyfunc])`：与`for`或列表生成式在一起使用。根据关键字函数`keyfunc`对`iterable`进行分组。
    - `itertools.islice(seq, [start,] stop [, step] ) `
    - `itertools.starmap(func, seq ) `
    - `itertools.takewhile( pred, seq )`
    - `itertools.tee(it, n ) `
    - `itertools.zip_longest( p, q, … )`
3. 组合生成器
