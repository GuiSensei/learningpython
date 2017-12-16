`import matplotlib.pyplot as plt`

`plt.plot([1,2,3,4],[3,2,5,7])`  #分别表示横坐标和纵坐标
`plt.xlabel('class')`            #x轴标签
`plt.ylabel('grade')`            #y轴标签
`plt.savefig('test', dpi = 600)` #图片保存
`plt.axis([a,b,c,d])`            #x轴范围[a,b],y轴范围[c,d]
`plt.grid(True)`                 #显示网格
`plt.show() `                    #图片显示


## 绘图区域的分割

- `plt.subplot(nrows, ncols, plot_number)`  
    - `nrows`行，`ncols`列，`plot_number`个区域，可以不用逗号

## 绘图函数`plt.plot`
- `plt.plot(x, y, format_string, **kwargs)`
    - `x`:X轴数据，列表或数组，可选
    - `y`:Y轴数据，列表或数组
    - `format_string`：控制曲线的格式字符串，可选，有颜色字符、风格字符和标记字符组成
    - `**kwargs`：第二组或多组`(x, y, format_string)`当绘制多条曲线时，各条曲线的`x`不能省略

## pyplot的中文显示

1. 方法1：改变所有字体
    ```python
    import matplotlib

    matplotlib.rcParams['font.family'] = 'Kaiti'
    matplotlib.rcParams['font.size'] = 20
    plt.plot([3,4,6,8,2])
    plt.ylabel('纵轴（值）')
    plt.savefig('test', dpi = 600)
    plt.show()
    ```
    - `rcParams`属性：
        - `'font.family'`字体名称：黑体`'SimHei'`；楷体`'Kaiti'`；隶书`'Lisu'`；仿宋`'FangSong'`；幼圆`'YouYuan'`；宋体`'STSong'`
        - `'font.style'`字体风格：正常`normal`，斜体`italic`
        - `'font.size'`字体大小：整数字号或`'large'`、`'x-small'`
2. 方法2：改变特定位置的字体
```python
#在有中文输出的地方增加fontproperties、fontsize
plt.ylabel('纵轴（值）', fontproperties = 'Kaiti', fontsize = 20， color = 'green')
```

## pyplot文本显示方法
- `plt.xlabel()`#X轴增加文本标签
- `plt.ylabel()`#Y轴增加文本标签
- `plt.title()`#整体增加文本标签，图形的正上方
- `plt.text(x, y, 'text', fontsize = 13)`#任意位置增加文本
- `plt.annotate(s,xy = (a,b), xytext = (c,d), arrowprops = dict(facecolor = 'black', shrink = 0.1,width = 2))`#在图形中增加带箭头的注解
    - `s`为显示的文本，`xy`为箭头位置`(a,b)`，`xytext`为文本位置`(c,d)`，`arrowprops`箭头属性


## pyplot子绘图区域
1. 方法1
`plt.subplot2grid(GridSpec网格形状, CurSpec选中网格, colspan列的延伸 = 1, rowspan = 1)`设置网格，选择网格，确定区域数量，编号从0开始

2. 方法2
    ```python
    import matplotlib.gridspec as gridspec
    gs = gridspec.GridSpec(3,3)
    ax1 = plt.subplt(gs[0,:])
    ax2 = plt.subplt(gs[1,:-1])
    ax3 = plt.subplt(gs[1:,-1])
    ax4 = plt.subplt(gs[2,0])
    ax5 = plt.subplt(gs[2,1])
    ```
