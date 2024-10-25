html
## HTML文档包括:
文档类型声明：!DOCTYPE html
html标签对:html /html
html标签对中的head标签对和body标签对:head /head,body /body> 

## 符号标签:
1标题标签(加粗):h1 /h1--h6 /h6

2段落标签:p /p

3加粗字体标签b /b,,strong /strong

4斜体标签:i /i,,em /em

5下划线:u /u

6删除线:s /s

7无序列表:
ul

    lixxxx/li

    lixxxx/li

ul

8有序列表:

ol

    lixxx li

    lixxxx li

ol

9表格标签大类:

table border="1-n"(表格边框,数字表示宽度)

    tr

        th xxxxx th (表格每列标题)

        th xxxxx th

    tr

    tr(表格行)

        td xxxx  td ( 表格数据)

        td xxxxxxx td

    tr

table

10超链接:a,常与属性href="网站链接"使用,还加上target="打开方式",_self是当前窗口打开,_blank是新窗口打开,_parent表示在父窗口打开,_top是在顶层窗口
打开

11换行:br

12创造水平分割线hr

13图片img与属性src=""(括号内为图片路径链接)和alt=""(括号内为无法显示图片时的文字),其属性  wdith=""(设置图片宽度),height=""(设置图片高度)
HTML属性:标签都可以有多个属性例如table的border

15容器快标签:div,创建一个能包含其他元素的容器快,用于组织内容,用于布局结构,其属性class=""(nav用于创造导航栏,content用于包裹内容)

16span标签:内容样式化文本,包裹一部分文本，便于使用样式,css,js行为.

15.16通常与css和js一起使用。

17:表单标签:

(1)框架(表单内容在form标签内)

from(其属性action=""引号内为URL是服务器提供的API,为输入数据的传向地)

    xxx

from

(2)输入:input,其中属性有

1.type="text"创造输入框="radio"创造圆形选框(单选),="password"输入密码,="checkbox"创造方形多选框,="submit"创造提交按钮(一般位于表单尾部)

2.placeholder=""创建输入框的灰色字,

3.value=""创建输入框黑色字和更改"提交字样"

4.name=""让圆形择框变为单选,给多选方框添加属性,引号内内容一致

(3)在输入(勾选)标签前加入span或者label (其for属性使其可以与input,for=""引号内容为input属性id的内容)标签可以给出输入提示  

18.按钮:button ,可以与就是JS联合使用,在前一个<>内使用属性onclick=""

属性用法:在开始标签中接属性名="属性值"

属性:id,class

属性title="xxx"鼠标移到该标签上时显示文字xxx


## 块元素和行内元素：
块元素(单独成行,其中能包括行内元素和块元素):div,p,h1-h6,ul,ol,li,table,from等

行内元素(z在同一行呈现,不能包括块元素):span, a,strong,em,img,br,input

行内块元素(水平上排列，但是可以设置宽度，高度，内外边距等块级元素属性，可以包括行内元素或块级元素):img

元素之间转换:在元素中添加属性style="display:inline(改为行内元素)inline-block(改为行内块)bolck(改为块)>;"

## 响应式布局和移动端显示(后续自己查询)
响应式布局方法

1.通过rem,vw/vh等单位实现在不同设备上显示相同比例进而实现适配

2.响应式布局，通过媒体查询'@media'实现一套HTML配合多套CSS实现 


## rem和px
一样是长度单位,但是px是绝对长度单位,rem是相对长度

使用rem之前要先在head的style中写下

html{

    font-size:nnnpx;       nnn为数字

}

多少rem,长度就是上述的多少倍


