---
title: "Hugo 博客搭建"
date: 2020-06-12T14:36:06+08:00
categories:
- Hugo
- Blog
tags:
- Hugo
- Blog
keywords:
- Blog
thumbnailImagePosition: left
thumbnailImage: /hdlBlog/images/image.jpg
#thumbnailImage: //example.com/image.jpg
---
博客搭建
<!--more-->
1. Hugo环境安装配置
* 安装
    [hugo的官方github仓库](https://github.com/gohugoio/hugo/releases) 下载对应的操作系统版本的Hugo二进制文件
    下载安装包 以windows64位操作系统为例，下载对应的Windows-64bit.zip
    ![pic](/images/blog1/1.jpg)
    解压安装包
    ![pic](/images/blog1/2.jpg)
* 配置环境
    我们把hugo.exe解压到了D:\hugo下面。所以hugo命令只能在该目录下才能识别。但是我们想要把博客目录建到其他目录下，这就需要配置环境变量。
    此电脑->右键->点击属性：
    ![pic](/images/blog1/3.jpg)
    点击高级系统设置：
    这里也可以查看到自己电脑操作系统是多少位
    ![pic](/images/blog1/4.jpg)
    点击环境变量
    ![pic](/images/blog1/5.jpg)
    系统变量中找到path，再点击编辑
    ![pic](/images/blog1/6.jpg)
    点击新建，填入hugo解压的文件目录，比如我们解压在D:\hugo就填的是D:\hugo
    ![pic](/images/blog1/7.jpg)
    配置好后全部点击确定，然后打开cmd命令行程序就可以在任意位置使用hugo命令了。
2. Hugo新建博客
* 新建博客
    win+R键打开运行框，输入cmd打开命令行。
    输入命令 hugo new site 路径
    例如：hugo new site E:/hugo/myBlog就在E盘hugo文件夹下新建了一个叫myBlog的hugo站点。
    ![pic](/images/blog1/8.jpg)
    ![pic](/images/blog1/9.jpg)
3. 配置Hugo主题
* [hugo官方主题列表](https://themes.gohugo.io/) 挑选自己想要的主题
    我们这里以Tranquilpeak主题为例来安装主题。github仓库地址[Tranquilpeak主题github仓库](https://themes.gohugo.io/hugo-tranquilpeak-theme/)
    将主题clone 到 我们的 themes 文件夹下
    ![pic](/images/blog1/10.jpg)
    cmd 命令行 1.进入到themes文件下 cd themes 2.将主题clone到themes中 git clone https://github.com/kakawait/hugo-tranquilpeak-theme.git（如果git clone 太慢或者出错 可以直接下载主题压缩包解压到themes文件夹下）
    ![pic](/images/blog1/11.jpg)   
* 配置主题
    找到Tranquilpeak主题下的myBlog\themes\hugo-tranquilpeak-theme\exampleSite\config.toml
    ![pic](/images/blog1/12.jpg)
    复制其内容到根目录下的myBlog\config.toml中，接着修改根目录下的配置文件

   ```
    baseURL = "你的github pages的仓库名"
    # Tips: 必须配置，否则上传的博客在GitHub Pages无法找到css文件，不产生样式
    languageCode = "en-us"
    defaultContentLanguage = "zh-cn"
    # Tips: 配置中文
    title = "xxx Blog"
    # Tips: 博客名称
    theme = "hugo-tranquilpeak-theme"
    # Tips: 配置主题
    themesDir = "./themes/"
    ddisqusShortname = "valine"
    # Tips: 评论系统
    paginate = 10
    # Tips: 每个页面显示的文章数
    canonifyurls = true
    publishDir = "docs"
    # Tips: 生成静态博客到docs文件夹，部署在GitHub Pages上时，一次性部署博客源码与发布博客

    [permalinks]
      post = "/:year/:month/:slug/"

    [taxonomies]
      tag = "tags"
      category = "categories"
      archive = "archives"
      # Tips: 定义的博客分类与逻辑关系

    [author]
      name = "your_name"
      # Tips: 博客侧边栏名字
      bio = "web"
      # Tips: 博客侧边栏个人简介
      job = "Front-end"
      # Tips: 博客侧边栏职业
      location = "北京"
      # Tips: 博客个人资料页面地址
      gravatarEmail = "youremail@qq.com"
      # Tips: 博客个人头像，取自WordPress头像

      # Tips: 定义的侧边栏菜单，icon取自Font-awesome
      [[menu.main]]
        weight = 1
        identifier = "home"
        name = "Home"
        pre = "<i class=\"sidebar-button-icon fa fa-lg fa-home\"></i>"
        url = "/"
      [[menu.main]]
        weight = 2
        identifier = "categories"
        name = "Categories"
        pre = "<i class=\"sidebar-button-icon fa fa-lg fa-bookmark\"></i>"
        url = "/categories"
      [[menu.main]]
        weight = 3
        identifier = "tags"
        name = "Tags"
        pre = "<i class=\"sidebar-button-icon fa fa-lg fa-tags\"></i>"
        url = "/tags"
      [[menu.main]]
        weight = 4
        identifier = "archives"
        name = "Archives"
        pre = "<i class=\"sidebar-button-icon fa fa-lg fa-archive\"></i>"
        url = "/archives"
      [[menu.main]]
        weight = 5
        identifier = "about"
        name = "About"
        pre = "<i class=\"sidebar-button-icon fa fa-lg fa-question\"></i>"
        url = "/#about"

      [[menu.links]]
        weight = 1
        identifier = "github"
        name = "GitHub"
        pre = "<i class=\"sidebar-button-icon fa fa-lg fa-github\"></i>"
        url = "https://github.com/xxxx"

      [[menu.misc]]
        weight = 1
        identifier = "rss"
        name = "RSS"
        pre = "<i class=\"sidebar-button-icon fa fa-lg fa-rss\"></i>"
        url = "/index.xml"

      [params]
        dateFormat = "2006年1月2日"
        syntaxHighlighter = 'highlight.js'
        clearReading = true
        hierarchicalCategories = true
        # 侧边框的参数，表示宽度，可以自己调成喜欢的大小
        sidebarBehavior = 2
        thumbnailImage = true
        thumbnailImagePosition = "right"
        autoThumbnailImage = true
        coverImage = "images/cover.jpg"
        favicon = "/favicon.ico"
        imageGallery = true

        [[params.sharingOptions]]
          name = "Facebook"
          icon = "fa-facebook-official"
          url = "https://www.facebook.com/sharer/sharer.php?u=%s"

        [[params.sharingOptions]]
          name = "Twitter"
          icon = "fa-twitter"
          url = "https://twitter.com/intent/tweet?text=%s"

        [[params.sharingOptions]]
          name = "Google+"
          icon = "fa-google-plus"
          url = "https://plus.google.com/share?url=%s"

        [params.header.rightLink]
          class = ""
          icon = ""
          url = "/#about"

        [params.gitment]         
          owner = ".....   "      # Your GitHub ID
          repo = ""               # The repo to store comments
          clientId = ""           # Your client ID
          clientSecret = ""       # Your client secret
        # 这里添加Valine评论系统的相关参数
        [params.valine]
          enable = true
          appId = 'your appid'
          appKey = 'your appkey'
          notify = false
          avatar = 'robohash'
          placeholder = '说点什么吧...'
          visitor = true

        # 页底签文字
        [params.footer]
          copyright = "<a href=\"https://github.com/xxx\">xxx</a>"
   ```
    这只是必要的一些配置 也可以详细看一下主题文档 都有介绍 
    目前评论系统可以先放一下 后面再配置

* 创建页面 
    创建页面 cmd命令行 hugo new first.md
    ![pic](/images/blog1/13.jpg)
    可以看到我们新建的页面到了 content 文件夹下
    ![pic](/images/blog1/14.jpg)
    可以对 first.md 中内容进行修改 根据myBlog\themes\hugo-tranquilpeak-theme\exampleSite\content\post 文件下的md文件修改 
    这里用的是Markdown语法 大家可以看看 [markdown 语法教程](https://www.jianshu.com/p/191d1e21f7ed/)  
    我们也可以在这里复制几篇到我们myBlog\content\post 文件夹下看看页面效果
    （post文件夹是我仿照主题例子content文件下目录新建的）

* 预览主题页面
     cmd命令行 生成docs文件夹：hugo --theme=主题名称 --baseUrl="git路径=myBlog\config.toml中的baseUrl（部署到git上页面要用到）" --buildDrafts 
     例如我们的项目：hugo --theme=hugo-tranquilpeak-theme --baseUrl="config.toml中的baseUrl" --buildDrafts
     根目录下 执行 hugo serve
     ![pic](/images/blog1/15.jpg)
     浏览器打开网址就可以看到博客啦！

<!-- ![pic](/images/image.jpg) -->