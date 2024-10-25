css
## CSS:使用模板：

选择器{

    属性一:属性值一;

    属性二:属性值二;

}

## 属性
有:1.color(颜色),2.font-size(字体大小),3.background-color(背景颜色)

4.font-family(设置字体 ),5.font-weight(字体粗细0),6font(包括所有字体设置)

7.line-height(设置行距),(块元素和行内块元素可以定义宽高,图片设置一个就可以按照比例放缩 )8.width(宽度),9.height(高度)

10.border-....,11.content-....,12.padding-....,13.margin-....
(四个方向的属性时对应顺序为上右下左)

14.text-align(调节行内位置,文字居中等等),border-collapse:collapse;(合并边框)

## 选择器：
1元素选择器:直接写元素名

2类选择器:.类名(就是class=""中引号内的内容)

3id选择器:#id名(就是id=""中引号内的内容)

4通用选择器(选择所有元素)

5子元素选择器

6后代选择器

7并集选择器

8伪类选择器

## 导入方式:优先级1>2>3

1内联样式:在标签中用style=""属性定义

2内联样式表:在head /head标签中用style定义

如

    style

        h3{

            属性:属性值;

        }

    /style

3外联样式表(允许在多个网页使用相同css样式):将css单独文件,在head中使用 link rel="stylesheet" href="" 导入,引号内是css文件地址

## 盒子模型:

属性名(都是复合属性):

内容(content)

内边距(padding)

边框(border):属性值设置宽度(直接写宽度大小),设置样式(直接写样式名),设置颜色(直接写颜色名)等

外边距(margin)

## 网页布局：
1.标准流

2.浮动(子元素使用):可以让多个块级元素在同一行排列且不会有缝隙(行内块有缝隙)且会根据宽度是否另起一行，只会在父元素内部浮动

特性:脱离标准。多个浮动，一行显示，顶部对齐。具备行内块元素特性 

选择器{

    float:left/right/none;

}

3.定位(控制元素位置)

1相对定位:相对于元素在文档流中的正常位置进行上下左右移动

position:relative;left:xx;right:xx;top:xx;bottom:xx:表示距离原本位置最左右上下偏离xxx距离

2绝对定位:相对于最近的定位后的父级元素进行定位(脱离文档流!!!)

position:absolute;left:xx;right:xx;top:xx;bottom:xx:表示距离原本位置最左右上下偏离xxx距离

3固定定位:相对于浏览器窗口进行定位(脱离文档流)(类似广告)

position:fixed;left:xx;right:xx;top:xx;bottom:xx:表示距离页面左右上下的距离

4.flex和grid(自适应布局)

Flex弹性盒子
概念:采用flex布局的元素被称为flex容器(flex container),容器中的子元素被称为flex项目(flex item),是容器成员
水平轴是主轴,开始于main start,结束于main end
竖直轴是交叉轴,开始于cross start,结束于cross end
子元素的水平大小为main size,竖直大小为cross size

设置方法在大盒子中css的style中使用display:flex;


## Flex容器
属性:
flex-direction;决定主轴的方向(项目的排列方向),属性值如下:
1.row(默认值)   主轴为水平，从左往右
2.row-reverse   主轴为水平，从右往左
3.column        主轴为竖直，从上往下
4.column-reverse 主轴为竖直，从下往上 

flex-wrap;设置换行方式,属性值如下:
1.nowrap(默认值)   不换行(列)
2.wrap            主轴为横向时：从上到下换行。主轴为纵向时，从左到右换行
3.wrap-reversze   主轴为横向时：从下到上换行。主轴为纵向时，从右到左换行

flex-flow;它是flex-direction和flex-wrap的简写形式;

justify-content;定义项目在主轴上的对齐方式，属性值有:
1.flex-start(默认)     与主轴起点对齐
2.flex-end           与主轴终点对齐
3.center           与主轴中点对齐
4.space-between     两端与主轴起点和终点对齐，项目之间间隔相等
5.space-around      每个项目两侧间隔相等，项目之间间隔比项目与边框的间隔大一倍
6.space-evenly      同上，但任何间隔都相等

align-items;定义项目在交叉轴上的对齐方式,属性值有:
1.如上
2.如上
3.如上
4.baseline      项目的第一行文字的基线对齐
5.stretch(默认值)      如果项目未设置高度或者设置为auto,项目将占满整个容器的高度

align-content;多轴线(一个主轴和一个交叉轴一起算一个轴线)对齐方式,属性值与如上两个相同

