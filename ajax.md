Ajax(异步无刷新技术，前后端交互)
## jqury调用ajax方法:
$.ajax({

    type : ""    get/post  (请求方式) post请求需要服务器支持，没有只能用get   

    url:  ""   请求地址url

    async: ""    是否异步,默认true表示异步

    data :{

        xxx:"ajax的数据 "      如果没有参数就不需要设置

    }     (发送到服务器的数据)  


    dataType(默认是文本): "json"   预期服务器返回的数据类型为json格式,如果是json格式,在接手到返回值时会自动封装成json对象(数组)..如果不是json,

    会转换成json(前提是要满足格式)

    contentType: ""   设置请求头

    success:function(形参名){

        代码

        console.log(形参名)   是字符串或者json数组

        var 随便一个变量名:=JSON.parse(形参名)   形参名代表返回的数据 把字符串转换成json中的数组,方便拿数据,如果本来就是json数据,不要再转换

        (在此dom操作,把数据放到body中)

        创造元素节点(ul等) 

        //遍历放回的数据数组

        for(var i=0;i<data.length; i++){

            (得到数组中每一个元素)

            var 变量名 =data[i];

            在此创造ul和li标签并把li放到ul内

            jQuery创建元素:

var 变量名 = $(" ul /ul ")或者是$(" li "+li中间的文本+" /li ")

                                        此文本可以是ajax调用数据中的变量,该使用方法  xx(上述接收数据的变量名).ajax数据中的变量名

将li放到ui中:   ul.append(li);

        }

        //将ul放到body中

        $("body").append(ul) ; 

    }  请求成功时调用此函数           


    error: ""   请求失败时调用此函数

    上述参数用不到就不写.可能就写下面这四个type,url,data,success

})

(可以把整个ajax放到button的点击触发函数中，嵌套即可)

## get

$.get调用请求(代替$.ajax)   

规定请求方式为get

1.只需要请求，没有参数没有返回值(只是发送一个数据给后台，不管后续只是发送)

2.发送请求，需要传参数给后台，没有返回值

3.发送请求，不需要传参数给他，有返回值

4.最完整:发送请求有参数有返回值

语法：

        $.get("请求地址","请求参数",function(形参){         形参用于接收返回的数据

                         请求参数没有用{}代替(不要引号)


        })


如果是post调用请求,就把get换成post就行

$.getJSON与上述post和get一样,区别是要求返回的数据格式是json格式

注:getjson方式要求返回的数据必须满足json格式
