
`ThreeDAxes`是`Manim`中用于创建三维坐标系的类。


在数学、物理和工程等领域，三维坐标系的绘制是非常重要的。


`ThreeDAxes`使得用户能够在动画中直观地展示三维空间中的对象和关系，从而提高演示文稿和教学的效果。


`ThreeDAxes`提供了多种参数，如坐标轴的范围、长度、颜色、粗细等，以及光源位置和光泽度等，这些参数使得用户能够根据需要自定义坐标系的外观和行为。


# 1\. 主要参数


`ThreeDAxes`的主要参数有：




| **参数名称** | **类型** | **说明** |
| --- | --- | --- |
| x\_range | Sequence\[float] | X轴的范围，格式为（起始值，结束值，步长） |
| y\_range | Sequence\[float] | Y轴的范围，格式为（起始值，结束值，步长） |
| z\_range | Sequence\[float] | Z轴的范围，格式为（起始值，结束值，步长） |
| x\_length | float | X轴的长度 |
| y\_length | float | Y轴的长度 |
| z\_length | float | Z轴的长度 |
| z\_axis\_config | dict | 对Z轴的配置，如颜色、粗细等 |
| z\_normal | Vector3D | 定义Z轴的“正向”方向 |
| num\_axis\_pieces | int | 轴的细分数量 |
| light\_source | Sequence\[float] | 光源的位置，影响阴影和光照效果 |


`ThreeDAxes`也是继承自`Axes`的，所以也有`x_axis_config`和`y_axis_config`参数，这里没有再列出来。


# 2\. 主要方法


`ThreeDAxes`主要使用的是下面2个方法：




| **名称** | **说明** |
| --- | --- |
| get\_axis\_labels | 为每个轴添加标签 |
| add\_coordinates | 在坐标系中添加网格线或刻度标记 |


# 3\. 使用示例


下面通过几个示例展示`ThreeDAxes`的关键功能和应用场景，每个示例都聚焦于该类的一个或多个核心参数或方法。


## 3\.1\. 坐标轴范围和刻度


在这个示例中，我们使用`ThreeDAxes`的`x_range`, `y_range`, 和`z_range`参数来设置坐标轴的范围，


并通过`x_length`, `y_length`, `z_length`来调整坐标轴的长度。


示例中：


* 设置**x轴**范围为`(-5, 5)`，**y轴**范围为`(-3, 3)`，**z轴**范围为`(-2, 2)`
* 调整**x轴**长度为`10`个单位，**y轴**长度为`6`个单位，**z轴**长度为`4`个单位
* 设置**x轴**刻度单位为`1.5`，**y轴**刻度单位为`1`，**z轴**刻度单位为`0.5`



```
axes = ThreeDAxes(
    x_range=(-5, 5, 1.5),
    y_range=(-3, 3, 1),
    z_range=(-2, 2, 0.5),
    x_length=10,
    y_length=6,
    z_length=4,
)
axes.add_coordinates()

```

![](https://img2024.cnblogs.com/blog/83005/202411/83005-20241101183956721-209008857.gif)


## 3\.2\. 自定义坐标轴颜色和标签


本示例将展示如何使用`*_axis_config`参数来自定义坐标轴的**颜色**、**粗细**以及**标签**。


使用`x_axis_config`将**x轴**设置红色，轴的粗细设为`1`，


使用`y_axis_config`将**y轴**设置绿色，轴的粗细设为`3`，


使用`z_axis_config`将**z轴**设置蓝色，轴的粗细设为`5`。


然后，再为每个轴添加自定义标签，如**x轴**标签为**"人口"**，**y轴**标签为**"年龄"**，**z轴**标签为**"收入"**。



```
axes = ThreeDAxes(
    x_axis_config={
        "color": RED,
        "stroke_width": 1,
    },
    y_axis_config={
        "color": GREEN,
        "stroke_width": 3,
    },
    z_axis_config={
        "color": BLUE,
        "stroke_width": 5,
    },
).scale(0.6)
labels = axes.get_axis_labels(
    Text("人口", font_size=20, color=RED),
    Text("年龄", font_size=20, color=GREEN),
    Text("收入", font_size=20, color=BLUE),
)

axes.add_coordinates()

```

![](https://img2024.cnblogs.com/blog/83005/202411/83005-20241101183956908-1992801916.gif)


## 3\.3\. 绘制三维函数


二维坐标系`Axes`中绘制的是曲线函数，在三维坐标系`ThreeDAxes`中，可以使用`plot_surface`函数来绘制曲面函数。


本示例绘制一个 $ z \= x2\+y2 $的曲面。



```
axes = ThreeDAxes(
    x_range=[-3, 3],
    y_range=[-3, 3],
    z_range=[-1, 3],
    x_length=6,
    y_length=6,
    z_length=4,
)

graph = axes.plot_surface(
    lambda u, v: u**2 + v**2,
    u_range=[-1, 1],
    v_range=[-1, 1],
)

```

![](https://img2024.cnblogs.com/blog/83005/202411/83005-20241101183956528-874354256.gif)


# 4\. 附件


文中的代码只是关键部分的截取，完整的代码共享在网盘中（`threed_axes.py`），


下载地址: [完整代码](https://github.com) (访问密码: 6872\)


 本博客参考[楚门加速器](https://shexiangshi.org)。转载请注明出处！
