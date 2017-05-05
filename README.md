##SVG 指可伸缩矢量图形 (Scalable Vector Graphics)
>必须使用 .svg 后缀来保存,也可以使写在html文件内.后面的图像会覆盖前面的图形

**使用 .svg 后缀来保存**
```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN"  "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg width="100%" height="100%" version="1.1" xmlns="http://www.w3.org/2000/svg">
    <circle cx="100" cy="50" r="40" stroke="black" stroke-width="2" fill="red"/>
</svg>
```
第一行包含了 XML 声明。请注意 standalone 属性！该属性规定此 SVG 文件是否是“独立的”，或含有对外部文件的引用。standalone="no" 意味着 SVG 文档会引用一个外部文件 - 在这里，是 DTD 文件。
第二行用了这个外部的 SVG DTD。该 DTD 位于 “http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd”。该 DTD 位于 W3C，含有所有允许的 SVG 元素。
第三行SVG 代码以 \<svg> 元素开始，包括开启标签 \<svg> 和关闭标签 \</svg> 。这是根元素。version为版本，xmlns为命名空间

**直接在html文件中使用**
```
<!DOCTYPE html>
<html>
<body>

<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
   <circle cx="100" cy="50" r="40" stroke="black" stroke-width="2" fill="red" />
</svg> 
 
</body>
</html>
```

###各种形状
1.矩形 <rect>
2.圆形 <circle>
3.椭圆 <ellipse>
4.线   <line>
5.折线 <polyline>
6.多边形 <polygon>
7.路径 <path>

* width:宽
* height:高
* x:距离左侧距离
* y:距离上侧距离
* style:样式
 opacity:透明度
 fill:填充颜色
 fill-opacity:填充透明度
 stoke:边框颜色
 stoke-width:边框宽度
 stroke-opacity:边框透明度
 
####矩形rect
```
<rect width="300" height="100" rx="20" ry="20"  style="fill:rgb(0,0,255);stroke-width:1;stroke:rgb(0,0,0)"/>
```
rx 和 ry 属性可使矩形产生圆角。

####圆形circle
```
<circle cx="100" cy="50" r="40" stroke="black" stroke-width="2" fill="red"/>
```
cx和cy属性定义圆点的x和y坐标。如果省略cx和cy，圆的中心会被设置为(0, 0)
r属性定义圆的半径

####椭圆ellipse
```
 <ellipse cx="300" cy="80" rx="100" ry="50" style="fill:yellow;stroke:purple;stroke-width:2"/>
```
cx属性定义的椭圆中心的x坐标
cy属性定义的椭圆中心的y坐标
rx属性定义的水平半径
ry属性定义的垂直半径

####直线line
```
 <line x1="0" y1="0" x2="200" y2="200"  style="stroke:rgb(255,0,0);stroke-width:2"/>
```
x1 属性在 x 轴定义线条的开始
y1 属性在 y 轴定义线条的开始
x2 属性在 x 轴定义线条的结束
y2 属性在 y 轴定义线条的结束

####多边形polygon
```
<polygon points="200,10 250,190 160,210"  style="fill:lime;stroke:purple;stroke-width:1"/>
```
points 属性定义多边形每个角的 x 和 y 坐标
points="x1,y1 x2,y2 x3,y3....."每个坐标以空格区分
* style
 fill-rule属性用于指定使用哪一种算法去判断画布上的某区域是否属于该图形“内部”
 fill-rule:填充规则 nonzero(默认) | evenodd | inherit  http://blog.csdn.net/mishiwjp/article/details/53484235
 
####曲线polyline
polyline元素是用于创建任何只有直线的形状
```
<polyline points="20,20 40,25 60,40 80,120 120,140 200,180"  style="fill:none;stroke:black;stroke-width:3" />
```

####路径path
```
<path d="M150 0 L75 200 L225 200 Z" />
```
* M = moveto(M X Y) ：将画笔移动到指定的坐标位置
* L = lineto(L X Y) ：画直线到指定的坐标位置
* H = horizontal lineto(H X)：画水平线到指定的X坐标位置
* V = vertical lineto(V Y)：画垂直线到指定的Y坐标位置
* C = curveto(C X1 Y1 X2 Y2 ENDX ENDY)：三次贝赛曲线
* S = smooth curveto(S X2 Y2 ENDX ENDY)
* Q = quadratic Belzier curve(Q X Y ENDX ENDY)：二次贝赛曲线
* T = smooth quadratic Belzier curveto(T ENDX ENDY)：映射
* A = elliptical Arc(A RX RY XROTATION FLAG1 FLAG ,X Y)：弧线
* Z = closepath()：关闭路径
>注意：以上所有命令均允许小写字母。大写表示绝对定位，小写表示相对定位。

####文本text 
```
<text x="0" y="15" fill="red"  transform="rotate(30 20,40)">I love SVG</text>
```
transform:变换

* 路径上的文字：
```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1"
xmlns:xlink="http://www.w3.org/1999/xlink">
   <defs>//定义
    <path id="path1" d="M75,20 a1,1 0 0,0 100,0" />
  </defs>
  <text x="10" y="100" style="fill:red;">
    <textPath xlink:href="#path1">I love SVG I love SVG</textPath>//xlink:href="#path1"根据id引用
  </text>
</svg>
```

* text元素可以安排任何分小组与<tspan> 元素的数量
```
<text x="10" y="20" style="fill:red;">Several lines:
    <tspan x="10" y="45">First line</tspan>
    <tspan x="10" y="70">Second line</tspan>
  </text>
```
* 分组元素 <g>，是 SVG 画布中的元素，意思是 group。此元素是将其他元素进行组合的容器


##SVG 动画
* \<set> 虽然set虽然不能触发连续的动画，但是，其还是可以实现基本的延迟功能。就是指：可以在特定时间之后修改某个属性值
* \<animate> 基础动画元素。实现**单属性**的动画过渡效果。
* \<animateColor>
* \<animateTransform> 实现transform变换动画效果的，如scale，rotate
* \<animateMotion> animateMotion元素可以让SVG各种图形沿着特定的path路径运动
上面的元素可以实现不同效果的动画。将动画动画元素放在需要运动的标签内

可以多个动画组合
```
 <text font-family="microsoft yahei" font-size="120" y="160" x="160">马
        <animate attributeName="x" from="160" to="60" begin="0s" dur="3s" repeatCount="indefinite" />
        <animate attributeName="opacity" from="1" to="0" begin="0s" dur="3s" repeatCount="indefinite" />
    </text>
```

1. attributeName = <attributeName>
要变化的元素属性名称，① 可以是元素直接暴露的属性，例如，对于本文反复出现的「马」对应的text元素上的x, y或者font-size; ② 可以是CSS属性。例如，透明度opacity.

2. attributeType = “CSS | XML | auto”
attributeType支持三个固定参数，CSS/XML/auto. 用来表明attributeName属性值的列表。x, y以及transform就属于XML, opacity就属于CSS. auto为默认值，自动判别的意思（实际上是先当成CSS处理，如果发现不认识，直接XML类别处理）。因此，如果你不确信某属性是XML类别还是CSS类别的时候，我的建议是不设置attributeType值，直接让浏览器自己去判断，几乎无差错。

3. from, to, by, values
from = “<value>“
动画的起始值。
to = “<value>“
指定动画的结束值。
by = “<value>“
动画的相对变化值。
values = “<list>“
用分号分隔的一个或多个值，可以看出是动画的多个关键值点。

4. repeatCount表示动画执行次数，可以是合法数值或者”indefinite“

5. dur 一次动画持续时间

6. begin 动画延迟多少时间执行
