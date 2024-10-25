Node.js

## 创建应用程序,初始化

创建xx.js之后，在终端输入npm init再回车，然后通过设置回车之后就创建号json可以运行脚本了

## ESM规范：

引入数据（导入对象）： import obj from"数据的地址"

数据地址的代码最后需要使用：export default{xxx,xxx,xxx}xxx为变量名或方法      方法的定义：let 方法名=() =>"地址"

使用数据(变量)obj.变量名

使用方法，在package.json中{下方新建一行添加"type":module   方法二:将扩展名改为mjs 也可以运行代码    

## CJS规范

导入对象: const obj=require("地址")

导出:module.exports={xx,xx,xx }

不需要添加type或者更改扩展名
  



以下为使用ESM规范

## URL模块

使用 let 变量名(DRUrl等) new URL('地址') 将输入的字符串解析成一个url对象

想要查询下方的数据:

完整的url  变量名.href

协议   xx.protocol

域名   xx.hostname

端口    xx.port

域名和端口   xx.host 

协议、域名、端口   xx.origin

路径   xx.pathname

查询字符串   xx.searchParams

id      xx.searchParams.get('id')

哈希    xx.hash

获取当前文件路径  import.meta.url   是url格式路径 使用场景为兼容跨平台和url的操作

转化为windows路径

导入url :import url from 'url'  然后定义一个变量:let 变量名(__filename等) = url.fileURLTopath(import.meta.url)       

## path
获取当前文件所在目录的路径:导入path模块 : import path from 'path'  然后定义一个变量 let 变量名(__dirname等) = path.dirname(__filename)   括号内为上一行变量名

获取路径中的文件名: path.basename(__filename)  文件名包含扩展名

获取路径中的扩展名: path.extname(__filename)

路径解析：path.parse(__filename).xx     可以将一个路径拆分为多个部分   分解部分有:root(windows的盘符),dir(目录的路径),base(文件名),ext(扩展名),name(不包含扩展名的文件名)

                        有".xx"可以获取某一个部分，没有获取的是多个部分

拼接路径:path.join(__dirname,"/文件名")   join不会将/解析为根目录即C盘D盘

拼接路径2:path.resolve(__dirname,"/")   这个会将/解析为根目录即C盘D盘

分隔符:path.sep    在windows上是\在linux上是/

## buffer

buffer对象可以看作是固定长度的数组专门用于处理二进制数据用于读取文件图像处理等，node中很多API返回的是buffer

创建buffer:  Buffer.alloc(xx)   这样创建一般用于内存分配                  xx表示创建的buffer是xx字节大小的并且使用0进行填充     在打印buffer时编译器会将其中存储的2进制转换为16进制

获取buffer长度:在上述代码后添加 .length

将字符串转化成buffer: let 变量名(urlbuffer等)=Buffer.from('dengruicode.com','utf8')   创建一个包含字符串'dengruicode.com'的Buffer 字符串格式为utf8，   这里的buffer就是包含字符串的recode.com的buffer

将buffer转换为字符串:buffer名(urlbuffer等).toString(utf8)      String(文件名)  强制把buffer转换成字符串

buffer与base64字符串的转换同上,utf8改成base64 

## fs模块

用于读取写入编辑删除文件和创建删除目录的

首先要导入:import fs from  'fs'

创建多级目录(async和await是以同步的方式编写异步代码 )；

const createDir =async (path)=>{

    try{                                                    下方表示允许创建多级目录   

        await fs.promises.mkdir(路径也就是传递进来的参数path,{recursive: true})   // recursive: true允许递归创建多级目录

        console.log("目录创建成功")

    } catch(err){

        console.log('目录创建失败:${err}')

    }

}

let dir ="DR/log/"    目录名

createDir(dir)   创建多级目录 (创建的最后一步)

写入文件:

const writeFile = async(参数一文件的路径path,参数二写入的内容content)=>{

    try{

        await fs.promises.writeFile(path,content)

        console.log("文件写入成功")

    } catch(err){

        console.log(`文件写入失败:${err}`)

    }

}

let name ="xxx.mmm"   xxx.mmm是文件名

let path =dir +name    dir 是上述创建的目录

let content = "dengruicode.com"   content是文件内的内容,会覆盖之前的内容

writeFile(path,content)

追加文件:

const appendFile = async(参数一文件的路径path,参数二写入的内容content)=>{

    try{

        await fs.promises.appendFile(path,content)

        console.log("追加写入成功")

    } catch(err){

        console.log(`追加写入失败:${err}`)

    }

}

let appendContent = "\nxxx"   \n换行,xxx为追加内容

appendFile(path,appendContent)

读取文件:

const readFile = async(参数一文件的路径path)=>{

    try{

        const data=  await fs.promises.readFile(path)

        console.log(String(data))

    } catch(err){

        console.log(`文件读取失败:${err}`)

    }

}

readFile(path)

检查文件或者目录是否存在

const fileOriDriExist = async(参数一文件的路径path)=>{

    try{

        await fs.promises.access(path,fs.promises.constants.F_OL)    R_OK  W_OK  X_OK分别表示检查文件是否可读，是否可写，是否可执行

        console.error("文件或者目录存在")

    } catch(err){

        console.error(`文件或者目录不存在:${err}`)

    }

}


fileOriDriExist("DR/log")  目录名

fileOriDriExist("DR/log/web.js")  目录名和文件名

获取目录或者文件的详细信息

const fileOriDriStats = async(参数一文件的路径path)=>{

    try{

        let stats=  await fs.promises.stat(path)

        console.log(stats)

        if (stats.isFile()){ 

            console.log(`${path}是文件`)        检查是否是文件

            return

        }

        if (stats.isDirectory()){

            console.log(`${path}是目录`)

            return

        }

    } catch(err){

        console.log(`获取文件和目录详细信息时出错:${err}`)

    }

}

fileOriDriStats("DR/log")        文件目录

fileOriDriStats("DR/log/web.js")    文件名

文件或者目录重命名:

const fileOriDriRename = async(oldParh,newPath)=>{

    try{

        await fs.promises.rename(oldParh,newPath)    

        console.error("文件或者目录重命名成功")

    } catch(err){

        console.error(`文件或者目录重命名失败:${err}`)

    }

}

fileOriDriRename("DR/log","DR/newlog")

fileOriDriRename("DR/newlog/web.txt","DR/newlog/newWeb.txt")

删除文件:

const deleteFile = async(path)=>{

    try{

        await fs.promises.unlike(path)    

        console.error("文件删除成功")

    } catch(err){

        console.error(`文件删除失败:${err}`)

    }

}

deleteFile("DR/newlog/newQeb.txt")

删除目录:

const deleteDir = async(path)=>{

    try{

        await fs.promises.rm(path,{recursive:true})      recursive:true 允许递归删除多级目录   

        console.error("目录删除成功")

    } catch(err){

        console.error(`目录删除失败:${err}`)

    }

}

deleteDir("DR")



## Stream流

这是一种处理数据的方式可以用于读取写入文件，可以逐步处理数据而不是一次性将整个文件加载到内存中，可以节省资源避免内存溢出

写入文件

const writeFile = (path,content)=> {

    const writeStream = fs.createWriteStream(path)   path是路径

    writeStream.on('error',err=>{

        console.error(`文件写入失败:${err}`)

        writeStream.close()                     出错时关闭流

    })


    writeStream.on('finish',()=>{

        console.log("文件写入成功")

    })

    writeStream.write(content,'utf8')    内容和格式

    writeStream.end()     结束流       

}

let path="web.txt"

let content="xxxx"    

writeStream(path,content)    path为写入的地址

追加文件

const appendFile = (path,content)=> {

    const appendStream = fs.createWriteStream(path,{flags:'a'})     a表示append是追加的意思

    appendStream.on('error',err=>{

        console.error(`追加写入失败:${err}`)

        writeStream.close()                     出错时关闭流

    })

    appendStream.on('finish',()=>{

        console.log("文件写入成功")

    })

    appendStream.write(content,'utf8')    内容和格式

    appendStream.end()     结束流        

}

let appendStream = "xxx"

appendStream(path,appendContent)   path 为地址

读取文件

const readFile = (path)=> {

    const readtream = fs.createReadStream(path)   path是路径

    let content =''

    readStream.on('data',chunk=>{

        console.log(chunk)          chunk指的是在流中传递的数据块

        contant += chunk.toString('utf8')    将buffer转换为字符串           

    })

    readStream.on('end',()=>{

        console.log(contant)

    })

    readStream.on('error',err=>{

        console.error(`文件读取失败: ${err}`)

    })           

}

readFile(path)



## OS模块   用于获取系统信息
导入:import os from 'os'


const bytesToGB = bytes =>(bytes/(1024*1024*1024)).toFixed(2)       将bytes转换为GB

内核版本     os.version()   win11,win10

操作系统类型   os.type()    windows等

系统架构    os.arch()     X64等

主机名    os.hostname()      

总内存(GB)   bytesToGB(os.totalmem())   

空闲内存(GB)   bytesToGB(os.freemem())   

CPU核心数     os.cpus().length   

当前用户的主目录     os.homedir()   

当前用户的信息      os.userInfo()    


## crypto模块
提供了加密和解密功能，支持各种哈希算法，对称加密和非对称加密等

导入: import crypto from 'crypto'

md5和sha-1函数,在网站中通常用于加密用户的密码

md5,作用是使用md5算法生成数据的哈希值

const md5= data(是个参数) =>{

    const   hash =crypto.creatHash("md5")   创造一个md5的哈希对象

    hash.update(data)     更新哈希对象,处理并传入哈希的数据

    return hash.digest("hex")    计算哈希值并以16进制字符串的形式返回,hex是一个字符串

}

sha-1

const sha1= data(是个参数) =>{

    const   hash =crypto.creatHash("sha1")   

    hash.update(data)    

    return hash.digest("hex")    
}


之后

console.log("md5:",md5("xxxx"))   xxx为传入的变量名

console.log("sha1:",sha1("Xxx"))

生成指定长度的随机字符串--常用于生成临时代码

const randomStr= length =>{

    const bytesNeed = Math.ceil(length/2)    获取所需字节数

    const randomBytes = crypto.randomBytes(bytesNeed)   获取到随机的字节

    const hexStr = randomBytes.toString('hex')    字节转换成16进制字符串

    return hexStr.slice(0,length)       截取指定长度的字符串,确保字符串符合要求

}

console.log("随机字符串:",randomStr(xx))   xx为数字表示字符串长度

对称加密算法AES

对称加密指的是加密和解密使用相同的密钥

AES-GEM模式进行加密

const aesGcmEncrypt = (plaintext, key)=>{               plaintext是要加密的原文本, key是用于加密和解密的密钥    

    const nonce = crypto.randomBytes(12)               nonce表示只使用一次的数字,确保相同的明文也不会产生相同的密文

    const cipher =crypto.creatCipheriv('aes-256-gcm',key,nonce)        创建加密器            三者是分别是加密的算法,给定的密钥和nonce

    let encrypted = cipher.update(plaintext,'utf8','hex')           使用加密器对明文进行加密,并将结果转化和你成16进制字符串

    encrypted+=cipher.final ('hex')                          加密后的密文数据

    const authTag =  cipher.getAuthTag().toString('hex')       获取认证标签并将其转换成16进制字符串  认证标签用于防止篡改和假冒

    const encryptedJson = JSON.stringify({                  将加密后的数据,nonce,和认证标签合并成一个json字符串

        nonce:nonce.toString('base64'),                   将nonce转换成base64编码便于存储   nonce默认是buffer类型

        encrypted:encrypted

        authTag:authTag

    })

    return encryptedJson

}

AES-GE模式解密

const aesGcmDecrypt = (encryptedJson, key)=>{                

    const {nonce,encrypted,authTag}= JSON.parse(encryptedJson)     从json中解析出加密数据,nonce,和认证标签

    const decipher = crypto.createDecipheriv('ace-256-gcm',key,nonceBuffer)    创建解密器,使用aes-256-gcm算法,给定密钥和nonceBuffer

    decipher.setAuthTag(Buffer.from(authTag,'hex'))          设置解密时校验的认证标签

    let decrypted = decipher.updated(encrypted,'hex','utf8')

    decrypted += decipher.final('utf8')                       这两行是使用解密器对数据进行解密将16进制的密文转换成utf8形式

    return decrypted

}



const key = crypto.randomBytes(32)          创建用于加密和解密的密钥

const plaintext = 'xxx'    xxx为要加密的原始文本

const encryptedJson = aesGcmEncrypt(plaintext,key)

const decryptedText = aesGcmDecrypt(encryptedJson,key)


console.log('加密:',encryptedJson)

console.log('解密',decryptedText)


## util模块

提供一些常用的工具函数 这两个函数在项目日志时经常使用

导入:import util from 'util'

格式化字符串:(举例)

const url ='xxx'

const user = 100

const msg =util.format('网站:%s,在线人数：%d',url,user)

console.log(msg)

将对象转换成字符串

const webObj ={url:'xxxxx.com',user:200}

console.log('webObj:',typeof webObj)

const webStr = util.inspect(webObj)

console.log('webStr:',typeof webStr,webStr)


## http模块-
创建并启动http服务器

导入http模块:import http from 'http'

本地回环地址是一个特殊的ip地址(通常为127.0.0.1),主要用于同一台主机的通信和测试

const hostname = '127.0.0.1'         服务器监听的ip地址(本地回环地址),意味着服务器只能接受来自本机的网络请求

const port = 8008      服务器监听的端口号(端口号是自定义的)

以下是创建一个http服务器实例

const server = http.createSercer((request,response)=>{

    response.write("xxxx.com")    发送相应数据

    response.end()       结束响应

})


以下是启动http服务器,并在指定的ip地址(127.0.0.1)和端口8008上监听链接请求

server.listen(port,hostname,()=>{

    console.log(`服务器已启动:http://${hostname}:${port}`)     打印服务器链接,可以在浏览器上使用

})

http模块

请求request和响应response

请求

获取请求链接和请求方法

console.log(`${request.method}${request.url}`)    前后分别是方法和链接

获取请求的头部信息

console.log('request.headers')    这个也可以通过浏览器F12,网络,根路径的请求标头

当想要获取header词之下的属性时直接在request.headers后加.属性名,但是当想获取的属性其中有中划线-时不能用此方法,需要在后面加['属性名']

响应

在设置之前返回的数据是纯文本,在此设置响应的通信息让浏览器认识html

response.statusCode = 200     200 状态码表示请求成功

response.setHeader('Content-Type','text/html;charset=UTF-8')   内容设置类型

response.write("h3  ssss  /h3")

response.end()

请求和响应两部分代码跟在启动服务器前面

http模块-获取参数
....





自动重启工具nodemon

可以让我们每次修改代码时不需要手动重启刷新项目

