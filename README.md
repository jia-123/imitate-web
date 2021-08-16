# imitate-web
imtate hope-studio's web layouts
## 网址
[demo](https://jia-123.github.io/imitate-web/)
## 需求
一、主题内容
1. screen > 958px logo和hero横向并列显示；
2. screen < 958px logo和hero竖向并列显示；
3. 当screen再小时，hero中的“工作室介绍”和“加入我们”再竖排并列显示。页脚的文字也竖排并列显示。

二、导航栏
1. screen > 958px 正常显示；
2. screen < 958px 搜索框变小，只有一个放大镜图标；当点击时又展开；
3. screen < 718px 导航栏再表化，具体的菜单隐藏，点击从左边出来。

三、其他
1. 鼠标悬停时，显示下拉菜单；鼠标点击从左侧出来隐藏菜单。
## CSS知识
1. 响应式布局：根据不同的屏幕尺寸引入应用不同的CSS样式；
```
@media screen and (min/max-width:1080px) {
  /*应用的样式*/
}
```
也可以在html`head`中通过`link`引入，但是没有成功；

2. `flex`：弹性布局
>给某个元素的display属性设置为flex后，它的子元素自动成为容器成员。
- `flex-direction`属性

决定子元素在主轴上的排列方向。默认水平为主轴，从左到右排列。

它有四个值：
```
row（默认值）：主轴为水平方向，起点在左端。
row-reverse：主轴为水平方向，起点在右端。
column：主轴为垂直方向，起点在上沿。
column-reverse：主轴为垂直方向，起点在下沿。
```
- `flex-wrap`属性

它有三个值：
```
nowrap（默认）：不换行。
wrap：换行，第一行在上方。
wrap-reverse：换行，第一行在下方。
```
- `flex-flow`

`flex-flow`属性是`flex-direction`属性和`flex-wrap`属性的简写形式，默认值为`row nowrap`。

- `justify-cotent`属性

这个定义了项目在主轴上的对齐方式。

它可能取6个值，具体对齐方式与轴的方向有关。下面假设主轴为从左到右。

```
flex-start（默认值）：左对齐
flex-end：右对齐
center： 居中
space-between：两端对齐，项目之间的间隔都相等。
space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。
space-evenly：可以使每个元素之间和元素距离边距的距离都相等。
```
- `align-items`属性

`align-items`属性定义项目在交叉轴上如何对齐。

它可能取5个值。具体的对齐方式与交叉轴的方向有关，下面假设交叉轴从上到下。
```
flex-start：交叉轴的起点对齐。
flex-end：交叉轴的终点对齐。
center：交叉轴的中点对齐。
baseline: 项目的第一行文字的基线对齐。
stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。
```
- `align-content`属性
`align-content`属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。

该属性可能取6个值。
```
flex-start：与交叉轴的起点对齐。
flex-end：与交叉轴的终点对齐。
center：与交叉轴的中点对齐。
space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
stretch（默认值）：轴线占满整个交叉轴。
```
### 子元素的属性
1. `flex-grow`属性

`flex-grow`属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。

如果所有项目的`flex-grow`属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的`flex-grow`属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。

2.`flex-shrink`属性

`flex-shrink`属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。

如果所有项目的`flex-shrink`属性都为1，当空间不足时，都将等比例缩小。如果一个项目的`flex-shrink`属性为0，其他项目都为1，则空间不足时，前者不缩小。

负值对该属性无效。

3.`flex-basis`属性

`flex-basis`属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。

它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间。

4.`flex`属性

`flex`属性是`flex-grow`, `flex-shrink`和 `flex-basis`的简写，默认值为0 1 auto。后两个属性可选。

该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。

建议优先使用这个属性，而不是单独写三个分离的属性，因为浏览器会推算相关值。

5. `align-self`属性

`align-self`属性允许单个项目有与其他项目不一样的对齐方式，可覆盖`align-items`属性。默认值为auto，表示继承父元素的`align-items`属性，如果没有父元素，则等同于`stretch`。

该属性可能取6个值，除了auto，其他都与align-items属性完全一致。

