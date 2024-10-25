JS
## 导入方式
1.使用标签scriptxxxx /script (xxxx为JS代码)可以放在head内或者body内

2.外部引入,在head中使用script src="" /script引号内为js代码路径

## 变量与数据类型

变量:

1.var x;声明一个正常变量，具有函数作用域(不常用)

2.let x=;声明一个变量，具有块级作用域，更安全灵活

3.const x=;声明一个常量

赋值为null为明确空值,声明但不赋值为undefined

## JS语言代码(最基础最重要)

1.console.log(''):在控制台内打印单引号内内容(也可以用于函数的执行括号内无引号直接跟变量名)

2.alert(""):在页面中弹窗

//注释  /*   xxx  */这个也是注释

## 控制语句

1.条件语句:if,else if,else

if (条件){

    xxxx

}

在上一个if条件为假时,判断else if

if和else if 都为假时,执行else 

2.循环语句for ,while ,do while.for一般用于有限循环,while一般用于无限循环

for(初始化表达式;循环条件;迭代器){

    循环代码

}

初始化表达式为给一个变量赋初始值

迭代器为每执行完一次需要执行的内容i++和i+=1是i=i+1的意思

while(循环条件){

    循环代码

    迭代代码

}

break和continue(可以与if使用):

break结束循环

continue跳过当前循环剩余代码,执行下一循环

等于是==


## 函数:自己定义一个函数便于后面使用.使用时再调用

声明(定义函数):

function 函数名(参数1,参数2,参数3){

    函数代码

    return 返回值;(如果没有返回值可以不写)

}

调用时:

函数名(参数值);

作用域:在函数内部声明的变量具有局部作用域，在外部声明的变量具有全局作用域.

事件处理(与用户交互相应):

## 事件(函数触发的条件):

onclick:点击

onmouseover:鼠标经过

onmouseout:鼠标移出

onchange:文本内容改变事件

onselect:文本框被选中

onfocus:光标聚集

onblur:移开光标

## 绑定(添加)事件的方式

1.HTML属性xxxx(上述属性值)="函数名()"(要先写好函数)

2.DOM属性

3.addEventlistener方法


## DOM(通常与JS一起使用,联系JS代码和html中的标签元素)

使用dom获取html标签元素的方法(js代码中使用):

1.var或者let   xxxx(变量名) =  document.getElementById('xxx')           //id="xxx"

2.var 或者let  xxxx(变量名) =  document.getElementVByClassName('xxx')[数字为索引查找第几个class,从0开始]    //xxx为类名

3var或者let    xxxx(变量名) =  document.getElementsByTagName('标签名')[索引值]     //div等

4.var或者ler   xxxx(变量名) =  document.getElement

5.var或者let   xxxx(变量名) =  document.getElement


然后可以进行如下操作   

变量名.innerHTML='xx'    用于修改文本,xx为系统可解析内容,变量名为文本的位置    

变量名.innerText='xxx'   用于修改文本,xxx问纯文本

变量名.color='颜色名(red等)'

变量名.fontSize='尺寸大小(20px等)'

变量名.style的属性= '' 

变量名.事件名=function(){

    函数代码

}

也可以使用

变量名.addEventListener('触发方式' (click等),function(){

    函数代码

})

  
关键字this,用在()内表示该参数   



## JS函数(通常要在前面加一个let/var 变量名= )

变量名.rows.length;(获取行数)

变量名.insertRow/Cell();插入行/列,括号内为插入位置,可以用索引0,1,2,3代替,插入第几行的列时，变量名为该行的变量名

变量名.parentNode;获取该节点的父节点

变量名.cells[];获取变量名行的第n列,[]内为0.1.2.3表示索引

变量名

prompt("");(浏览器自带的输入弹窗，""内为输入提示)




## DOM对象常用方法(在前面要加上变量名.)

appendChild()        把新的子节点添加到指定节点

removeChild()       删除子节点(括号内为子节点.前面为父节点 )

repleaceChild()      替换子节点

insertBefore()      在指定的子节点前面插入新的子节点

createAttribute()     创造属性节点

creatElement()      创造元素节点

creatTextNode()        创造文本节点

getAttribute()      返回特定属性值

function做函数名时为匿名函数,没有函数名,不能在别的地方调用
