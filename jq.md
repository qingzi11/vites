JQury:

## 引入：
在head /head中 使用script src=""  /script引号内为jq代码路径

## 使用：
script  /script中输入代码:

$(document).ready(function(){          简洁版:$(function(){

    输入所需代码                                  输入所需代码

})                                            })


进阶简洁版(联系JQ代码和html中的标签元素等):         (用则这个和下面那个)

$(父标签名  "#id名"或者".class名"或者"标签名").on("事件",function(){

    代码                  (若是标签名则选中所有标签)

})

(父标签名可以没有，有的话表示选中该父标签中的子标签

事件有,click(单击),dbclick(双击),mouseenter(鼠标经过),mouseleave(鼠标移开),mousedown(鼠标按下),mouseup(松开鼠标)

以下为使用该版的事件：

该版

$(同上).事件名(function(){

    代码

})

事件有:hover(鼠标经过和移开,需要两个用,隔开的fuction对应两个事件),focus(点击此处后获取光标同时可以获取一个值)

      blur(点击别处后失去光标),

代码(通常嵌套在事件中，事件发生后执行),使用方式:$(xx).代码名()

show()(显示，通常嵌套在别的$中show()括号中没有function直接结束),hide()(隐藏,使用同上),toggle()(显示时隐藏，隐藏时显示使用同上)

fadeIn()(淡入，括号内为淡入过程时间，使用同上),fadeOut(淡出，使用同上),slideDown(滑入,使用同上),slideUp(滑出，使用同上),slideToggle

css("css属性","css属性值")  

选中奇偶项标签，在上述标签(或者id,classm名)后面加:even选择奇数,加odd选择偶数

选中某一项标签,在上述$(xx)后加入  .eq(索引值)

## 动画
animate():

使用(常嵌套在事件中):$(xx).animate({

    属性(多个属性之间换行时，每行后用","隔开)

})

属性有:left/right/up/down:"npx"    (表示前进到距离最原本位置最左右上下偏离n距离,使用前需要更改使得标签position为绝对定位或者相对定位)

     opacity:'xx'     (xx为透明度)         上述可以变成动态,可以设置left等:后的值为一个变量，使得每点一次就前进一点

     width:""

     height:""

       例如;属性是color,属性值为white

在属性前加上.stop() ,表示事件不触发立马停止

链:多个代码可以同时在一个$中使用,

如:$(xx).代码1().代码2({

    代码2中代码

}).代码3()

## 获取

获取文本格式:$(xx).text()

获取标签格式$(xx).html()

获取输入框内的文本$(xx).val("")    ""内为更改后的属性值     

获取当前点击的值时$(this).xxxx

获取属性值:$().attr("属性名","xxxx")   xxxx表示更改后的属性值(可以是文字，路径等等)

获取父级元素:$(子元素).parent("")  括号内为父级标签后加s可以获取父级的父级

获取子级元素:$(父元素).children()

获取一系列的亲属$(该元素).find("亲属标签")

获取兄弟:$("父级元素   该元素").siblings("指定获取某个兄弟")

获取下一个兄弟                .next

获取上面一个兄弟              .prev

获取下面全部的兄弟            .nextAll

留言出现:$(出现的位置).slideDown().append("<>"+$(xxx).xx()+"<>") 俩引号内为想让留言出现的标签形式  

                 留言要先隐藏       如果想要新留言出现在前面,不用append用prepend而before,after分别在留言框前后追加

留言删除（需要绑定其他事件）:$().remove()   前()为删除的内容