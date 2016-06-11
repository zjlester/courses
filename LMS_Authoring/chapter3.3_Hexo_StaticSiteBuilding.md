# Node.js、Hexo和Github制作专题学习网站

## 基本信息
* Node.js：
	Node.js是一个服务器端的JavaScript运行容器，如果觉得这话难以理解，你可以将它视为是一个类似IIS、配置了PHP解析器的Apache一样的环境，只不过这里解析的不是ASP.Net、PHP文件，而是服务器端的JavaScript。如果你还是不理解，那也没事，在这门课程里，我们只是利用它开部署一个本地的已有系统，不需要你用Node.js去作开发环境。
* Hexo：
	Hexo是一个基于Node.js的静态网站建站工具，它的主要工作思路是允许你用Markdown来进行纯粹的网站内容制作，然后你可以利用它，生成可以在互联网上发布的Web站点。
* Git与Github：
	Git是一个目前应用非常广泛的源代码版本控制系统，作者是大名鼎鼎的Linus，也就是Linux的创始人。而Github是互联网上采用Git技术的最著名的代码托管站点。

## 目标与主要内容
本节要实现

环境配置
Node.js(必须) 一路默认安装即可。
安装Git(必须) 一路默认安装即可。
Github账号(必须)
安装Hexo
nodejs和git安装完成后，打开’git bash’安装hexo

npm install -g hexo-cli
Start
新建一个文件夹(如E:\Hexo)，在此文件夹中执行命令

1 hexo init
2 npm install
本地查看
1 hexo server //hexo s
后在浏览器中输入 http://localhost:4000/

此时，会有一篇文章hello world,对应的文件为 E:\Hexo\source_posts\hello-world.md
文章用markdown语法写.

新建文章
1 hexo new "New article"
会新建一个名为’New article’的文章，执行以下命令之后查看。

hexo generate   //生成静态网页以及css js文件 存放于public文件夹中
hexo server
至此，本地博客搭建完毕。下一步移植到Github

Github
新建repository,项目名必须是:name.github.io(name是你的账号名)。
我的账号名是cnfanhua,新建的项目名也就是cnfanhua.github.io

部署
在你的hexo文件夹中有个重要的文件_config.yml,打开编辑,把’cnfanhua’换成你的账号名

1 deploy:
2   type: git
3   repository: https://github.com/cnfanhua/cnfanhua.github.io.git
4   branch: master
执行下列命令后部署(部署前，需要配置SSh，否则失败)。

1 hexo generate
2 hexo deploy　　//上传至github 代替 git push...
至此，个人博客搭建完成。
注意:每次修改后 需要 hexo g 命令保存 然后hexo d 命令上传

外配置SSh
打开git bash

设置username和email
 

1 git config --global user.name "test"
2 git config --global user.email "test@gmail.com"
生成秘钥
ssh-keygen -t rsa -C "test@gmail.com"
最后得到id_rsa和id_rsa.pub两个文件，把id_rsa.pub的内容粘贴到github中即可
NexT主题
下载
gitHub,clone到你的博客目录\themes目录下(E:\Hexo\themes下)

git clone git@github.com:iissnan/hexo-theme-next.git
使用
打开站点总配置_config.yml(即E:\Hexo下的_config.yml),找到theme换成next即可(theme: next),记得每一个冒号后面要有一个空格

NexT-配置
插件安装
npm install <插件名>
卸载插件
npm uninstall <插件名>
多说评论
使用多说前需要先在 多说 创建一个站点。具体步骤如下：

登录后在首页选择 “我要安装”。
创建站点，填写表单。多说域名 这一栏填写的即是你的 duoshuo_shortname
主题配置文件 中设置：
　　　　　　# 多说热评文章 true 或者 false
　　　　　　duoshuo_shortname: '多说域名'

Google 分析
登陆google分析网站获取ID
编辑 站点配置文件，新增字段 google_analytics，值设置成你的 Google 跟踪 ID。

google_analytics: UA-XXX...
社交链接，将在侧栏中显示
将以下代码放到站点配置文件

 

复制代码
1 social:
2   GitHub: your-github-url
3   Twitter: your-twitter-url
4   Weibo: your-weibo-url
5   DouBan: your-douban-url
6   ZhiHu: your-zhihu-url
7   # 等等
复制代码
 

文章目录
主题配置文件 中设置：

1 sidebar: post   #自动展示有目录的文章的目录
2 #sidebar: always    #总是展示
3 #sidebar: hide      #隐藏
添加云标签
hexo new page "tags"        //新增tags页面
　　编辑刚才的页面(path\source\tags\index.md)

1 ---
2 title: TagCloud
3 date: 2016-01-21 16:12:58
4 type: "tags"
5 comments: false     //关闭评论
6 ---
　　编辑主题配置文件,添加 tags 到 menu 中

1 menu:
2   home: /
3   archives: /archives
4   tags: /tags
添加high一下
在 Hexo\themes\next\layout_partials\header.swig 中的 ul 标签加入如下 li 代码：

 View Code
开启RSS功能
安装插件

npm install hexo-generator-feed --save
后编辑主题配置文件_config.yml,添加如下代码

rss: /atom.xml #rss地址  默认即可
报错
找不到git部署 ERROR Deployer not found: git
解决办法

npm install hexo-deployer-git --save
部署类型设置git
hexo 3.0 部署类型不再是github,而是git,修改主题配置文件_config.yml中deploy中的type为git

1 deploy:
2   type: git
3   repository: git@cnfanhua.github.com:cnfanhua/cnfanhua.github.io.git
4   branch: master

## 拓展阅读

1 [Node.js官方网站](https://nodejs.org/en/)
1 [Hexo官方文档](https://hexo.io/docs/)
1 [Git官方网站](https://git-scm.com/download/)
1 [Github官方网站](http://www.github.com)
1 [Node.js维基百科词条](https://en.wikipedia.org/wiki/Nodejs)
1 [Node.js中文网（备用）](http://nodejs.cn/download/)
1 [Hexo搭建Github静态博客](http://www.cnblogs.com/zhcncn/p/4097881.html)
