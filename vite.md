vitepress:
##  1.安装:
新建文件夹,在新文件夹内打开cmd窗口.输入 pnpm add -D vitepress 安装
查询pnpm版本:pnpm -v
查询node版本:node -v  在编写github工作流时候要用node版本

## 2.初始化vitepress:
 pnpm vitepress init,然后回车回车,主题选第二个,不使用TS,要添加npm脚本

## 3.启动:vscode
打开文件夹,然后启动项目,新建终端,输入:pnpm run docs:dev,然后等待网址,然后在浏览器输入网址

## 4.美化主页(9个地方):
9:最下方:在config.mjs, defineConfig themeConfig文件底部配置:
配置为:footer:{
    copyright:"Copyright@ 2023 Albert Zhang",        (footer上一行末端加个逗号)
}

2-6从上到下的中间字:在index.md文件中改,对应关系为name-2,,text--3,tagline--4,,actions-5,features-6,     
actions内部(两个按钮所以重复两次):
theme:有几个选项主题可以选
text: Markdown  按钮的文字
link: 跳转的地址,可以输入网址
features内部
details: 大按钮的文字
可以添加link: 地址

1.7.8顶部栏:在config.mjs中配置,对应关系为 title-1,nav-7,socialLinks-8   description不用改
nav内部:
text: '文字'
link: 跳转地址,可以是网址也可以是本地相对地址
nav设置下拉⬇:text后面的link换成items:[
{text:'',link:''}
{text:'',link:''}]
socialLinks内部:
icon:'图标名'
link:'图标点击后跳转地址'
添加社交图标(在前面的时候做这一步):在config.mjs的 sociallinks中新增一个
{
    icon:{
        svg: '复制的内容'
    },
    link: "跳转网址"
},

svg获得方法:在浏览器搜索iconfont,阿里开源,在其中搜索想要的图标,点击赋值svg代码

## 5.主页扩展
图片美化    找图片图标的网址:https://www.iconfont.cn/
下载好之后挪到public文件夹中(新建一个文件夹),然后在index.md中的hero内添加一个  image:
                                                                             src: /background.png   /后面的是public文件中的图片名
                                                                             alt: 背景图片   冒号后加空格!!
logo配置:在config.mjs的themeconfig中添加  logo:'/logo.png',

## 6.美化文章页官方默认是三边栏:
sidebar左侧目录栏(可以是数组可以是对象) (左边每一个导航都是一个markdown文件):
sldebar内部数组[]中包含多个{}每个{}之间在目录处会用横线隔开,一个{}中可以有多个文字跳转
text:'小标题'(不跳转)
items:[
{text:'文字',link:'跳转链接'},
{同上}]      有脚本可以自动化添加左边栏

右边栏是标题,是本页内的标题,点击后去到本页标题处
右边栏包括上方的大标题(不跳转),和小标题跳转:在config.mjs处themeConfig下增加
outlineTitle: "文字"
outline:[2,6],         (写了这两个之后就可以去相应的md文件中添加标题了  多少的#号就是几级标题 )

next page和last page 按钮处也可以自定义
## 7.文章页扩展
配置两边栏:在config.mjs的themeConfig配置
sidebar: false      关闭侧边栏
aside:"left",     设置右边栏左边显示  这两行代码放到下面
然后在vitepress theme style.css里面配置css调整位置,加到最后
css代码:浏览器F12中找到想要改的元素块,在右边样式里找到代码,然后复制放到css文件最后,删除[data -v],更改px大小,@media不要改

## 8.美化地址栏icon(网站最最顶部的图标):
在config.mjs defineConfig 下面直接配置:
配置内容为: head: [["link",{ rel: "icon", href: "/xxx.png"}]]      xxx.png为public文件内的图标名

## 9.设置搜索框
在config.mjs defineConfig内的themeconfig中配置
搜索框代码:
search:{
    provider: "local",
    opition: {
        translations: {
            button: {
                buttonText: "搜索文档",
                buttonArialabel: "搜索文档",
            },
            modal: {
                noResultsText: "无法找到相关结果",
                reserButtonTitle: "清楚查询条件",
                footer: {
                    selectText: "选择",
                    navigateText: "切换",
                },
            },
        },
    },
},


## 10.github pages部署(不需要服务器,支持CI/CD(修改之后自动更新)):
1直接创建仓库,不要README
2初始化仓库 git init  直接在vscode的终端中打入该代码(要先安装git)
3然后在大文件夹中添加文本文档名字为:.gitignore  (txt也要删除掉,不要扩展名),然后删除.git文件夹
在vscode中为.git添加内容:
node_modules
.DS_store
dist
dist-ssr
cache
.cache
.temp
*.local
表示忽略以上内容,不添加到github仓库中
4在终端处输入 git init
5添加本地所有文件到仓库:在终端输入 git add    会出现换行符不兼容问题不用管
6创建一次提交:在终端输入 git commit -m "first commit"
7添加远程仓库地址到本地:在终端输入 git remote add origin 一个地址(该地址在GitHub刚刚创建的仓库里的蓝色框下面的第一个浅蓝框内复制)该地址是github仓库地址
8推送项目到GitHub: 终端输入 git push -u origin master   -u表示以后再推送不用指定源(origin)和分支(master)   然后就可以再github仓库刷新看到了
9选择GitHub actions: 在GitHub中点击settings,然后点击pages,再点击source,选择GitHub actions
10设置工作流: 在GitHub中点击Actions,然后点击第三行蓝色字
11然后再重命名并设置deploy脚本:在vitepress官方文档 https://vitepress.dev/guide/deploy#github-pages 中复制代码到10出现的输入框中
11中,使用pnpm的话需要安装并添加到环境变量,pnpm版本要与node版本一样.     如果用npm部署参考该网站: https://hellohao096.github.io/hellohao/posts/GitHub%20Action一键部署个人博客.html
12重命名,点击提交: 重命名 :在刚刚的GitHub页面上的小输入框重命名为:deploy.yml 然后点右边的绿色按钮 继续点绿色
13等待,查看域名:等等之后在settings的pages内查看域名 蓝色网址
14添加(push)一下.nojekyll文件(直接在vscode的大文件夹里新建文件),空的就行.然后在终端输入
git add . 回车
git commit -m "添加.nojekyll文件" 回车
git push 回车 
如果失败,可能是本地版本和远程版本可能不一样解决方案:在终端输入 git pull origin master 回车之后然后再重新 git push 
然后回到仓库code有小棕色点是表示正在重新编译,需要等待很久




## 11.可以自定义域名(暂时用不到)

还有需要注意的点(提前做好):需要在config.mjs中的defineConfig 中(最前面就号)添加 
base: "/大文件名/"        在head中的href中图标地址的前面加上/大文件(仓库文件名)名/


添加新内容时,在原文件更改后在终端输入: git add . 回车之后 git commit -m "添加的新内容" 回车 然后在终端输入: git push origin master 
等待即可