---
title: hexo入门
categories: blog工具
tags: 杂项
abbrlink: 13304
date: 2021-12-29 20:35:25
---



<p align="right">hexo使用记录</p> 

<!-- more -->

## hexo常用命令

```sh
 hexo n "博客名称"  => hexo new "博客名称"   #这两个都是创建新文章，前者是简写模式
$ hexo p  => hexo publish
$ hexo g  => hexo generate  #生成
$ hexo s  => hexo server  #启动服务预览
$ hexo d  => hexo deploy  #部署

$ hexo server   #Hexo 会监视文件变动并自动更新，无须重启服务器。
$ hexo server -s   #静态模式
$ hexo server -p 5000   #更改端口
$ hexo server -i 192.168.1.1   #自定义IP
$ hexo clean   #清除缓存，网页正常情况下可以忽略此条命令
```



###  hexo删除文章

目前未找到删除文章的指令，可以到目录/source/_posts下删除相应的文章，然后重新生成部署即可

```sh
#到目录/source/_posts下删除相应的文章
hexo g
hexo d
```



### hexo生成文章

```sh
hexo new [layout] <title>
```

您可以在命令中指定文章的布局（layout），默认为 `post`，可以通过修改 `_config.yml` 中的 `default_layout` 参数来指定默认布局。



Hexo 有三种默认布局：`post`、`page` 和 `draft`。在创建这三种不同类型的文件时，它们将会被保存到不同的路径；而您自定义的其他布局和 `post` 相同，都将储存到 `source/_posts` 文件夹。



```html
<center>要居中的文字</center>
```



### html标题

```html
<h1 align = "center">hexo入门</h1>
```



### hexo部署

1. 本地预览和同时发布到远程的浏览结果不一致

这是由缓存造成的,需要先hexo clean,再hexo g -d部署到远程

### hexo创建页面

1. 创建一般的文章：hexo new "文章名称"
2. 创建"关于我"等页面：hexo new page "about"这里的about要和在主题的_config.yml文件中的menu中进行匹配
    如：menu:
    Home: /
    Archives: /archives
    About: /about
    那创建关于我的页面：hexo new page "about" 在编辑创建出来的md文件，然后部署就能看到

3. 创建友情链接：在主题的配置中：
    links_title: 友情链接
    links:
    CSDN: [http://blog.csdn.net/u012900536](https://link.jianshu.com?t=http://blog.csdn.net/u012900536)

   ```yaml
   menu:
     home: / || fa fa-home
     about: /about/ || fa fa-user
     tags: /tags/ || fa fa-tags
     categories: /categories/ || fa fa-th
     archives: /archives/ || fa fa-archive
     books: /books/ || fa fa-book
     schedule: /schedule/ || fa fa-calendar
     sitemap: /sitemap.xml || fa fa-sitemap
     commonweal: /404/ || fa fa-heartbeat
   ```

   如上，在里面添加了books

   菜单配置包括三个部分，第一是菜单项（名称和链接），第二是菜单项的显示文本，第三是菜单项对应的图标。 NexT 使用的是 [Font Awesome](http://fontawesome.io/) 提供的图标， Font Awesome 提供了 600+ 的图标，可以满足绝大的多数的场景，同时无须担心在 Retina 屏幕下 图标模糊的问题。

   

   若你的站点运行在子目录中，请将链接前缀的 `/` 去掉

   > [开始使用 - NexT 使用文档](https://theme-next.iissnan.com/getting-started.html)
   >
   > https://fontawesome.com/

## hexo代码块高亮

首先需要动的地方有：

```yaml
主题的_config.yml文件
站点的_config.yml文件
代码块的语言标注
```

### 站点配置文件

在站点的配置文件中，搜索hightlight:

```yaml
highlight:
  enable: true
  line_number: true
  auto_detect: true
  tab_replace:
```

文字自动检测默认不启动，所以改成true使其起作用。

### 主题配置文件

再到主题的配置文件：

找到：

highlight_theme: normal，注释显示有五种显示主题可用，分别是：

```yaml
normal
night
night eighties
night blue
night bright
```

选择的是night bright



还可以选择mac风格

`_config.yml` 配置一下 codeblock.copy_button.style: mac

> [hexo next 代码块高亮](https://benpaodewoniu.github.io/2019/10/06/hexo7/)
>
> [Hexo+NexT美化🍕Mac Panel风格代码块配置](https://miaosakurai.com/2020/04/20/Hexo-NexT%E7%BE%8E%E5%8C%96%F0%9F%8D%95Mac-Panel%E9%A3%8E%E6%A0%BC%E4%BB%A3%E7%A0%81%E5%9D%97%E9%85%8D%E7%BD%AE/)

## 配置markdown渲染器

主要是为了数学公式，

Next 主题可以使用 mathjax 和 katex 两种渲染 latex 的方式。

- katex 渲染速度更快，但仅支持 latex 的子集。
- mathjax 渲染速度稍慢，但对 latex 的支持较好。



Next 主题的配置文件 _config.yml 中：

```yaml
# Math Formulas Render Support
math:
  # Default (true) will load mathjax / katex script on demand.
  # That is it only render those page which has `mathjax: true` in Front-matter.
  # If you set it to false, it will load mathjax / katex srcipt EVERY PAGE.
  per_page: true

  # hexo-renderer-pandoc (or hexo-renderer-kramed) required for full MathJax support.
  mathjax:
    enable: true
    # See: https://mhchem.github.io/MathJax-mhchem/
    mhchem: false

  # hexo-renderer-markdown-it-plus (or hexo-renderer-markdown-it with markdown-it-katex plugin) required for full Katex support.
  katex:
    enable: false
    # See: https://github.com/KaTeX/KaTeX/tree/master/contrib/copy-tex
    copy_tex: false
```

mathjax 和 katex 是互斥的两个选项，enable 不能同时 true或 false。

如果设置 `mathjax : true` ，就需要更换渲染引擎， `hexo-renderer-pandoc` 或 `hexo-renderer-kramed`（这个不推荐）

hexo-renderer-marked：hexo默认的渲染器不支持复杂的数学公式
hexo-renderer-kramed：支持复杂的数学公式，mathjax的渲染方式
hexo-renderer-markdown-it：取代第一个的渲染器，渲染更快，更符合CommonMark规则。
hexo-renderer-markdown-it-katex：跟上一个差不多，但是不用设置就支持katex
hexo-renderer-markdown-it-plus：好用，可以自己决定是否要渲染katex公式。此外能渲染的东西多，但是已经不维护了。
@upupming/hexo-renderer-markdown-it-plus ：上一个的升级版。好用。支持的功能多



虽然next不推荐katlex这里选用的是katex

步骤：

1. 更换渲染器

   1. 卸载原来的
      如果你没换过hexo的渲染器，那你就这样卸载：

      ```sh
      npm uni hexo-renderer-marked --save
      ```

      如果你换过了，那你就想想你用的是什么渲染器，然后卸载

      ```npm
      npm uni 你的渲染器 --save
      ```

   2. 下载新的渲染器

   	```sh
   npm i @upupming/hexo-renderer-markdown-it-plus --save

2. 修改 _config.yml文件

   1. 介绍文件
      先一下完整代码，把这段代码完整的放到你博客的 _config.yml里边。下边详细解释一下每行代表什么。

      ```yaml
      # Markdown config
      markdown_it_plus:
        render:
          html: true						
          xhtmlOut: false
          breaks: true
          linkify: true
          typographer: true
          quotes: '“”‘’'
        plugins:
        anchors:	
          level: 2
          collisionSuffix: 'v'
          permalink: true
          permalinkClass: header-anchor
          permalinkSide: 'left'
          permalinkSymbol: ¶
      ```
      
      > render
      > html：
      > true 支持HTML内嵌
      > xhtmlOut：
      > true 解析器markdown为完全符合XHTML的代码。例如：一个换行符将是<br />，否则会转换为<br>
      > breaks：
      > true 每当.md文件的换行符都会解析器都会生成<br>标签。
      > 其实讲真的这个设置true还是false，我页面上没看出区别。
      > linkify：
      > true 返回文本链接作为与段落内联的适当链接。例如，如果你写的一段文本看起来像一个链接，它将被呈现为<a src="http://example.com">http://example.com</a>，否则会解析为文本，比如<span>http://example.com</span>
      > typographer：替换常见的排版元素。
      > quotes：在 typographer为true的时候才好使，用于替换英文单双引号。
      > 如果quotes：'“”‘’' 那么"hello" 'hello'会变成“hello” ‘hello’
      > 如果quotes：'«»“”'那么"hello" 'hello'会变成«hello» “hello”
      > 我用着不好使
      
      plugins
      
      添加插件，这就是我为什么选了这个渲染器，这个默认支持的比较多，不用自己下载。
      markdown-it-emoji支持emoji，:cat:→🐱
      markdown-it-sub 支持H~2~O→H2O
      markdown-it-sup 支持X^2^→X2
      markdown-it-deflist 支持自定义列表
      markdown-it-abbr支持<abbr>标签
      markdown-it-footnote支持引入参考文献。emmm就是上标数字，最后附上文献那种
      markdown-it-ins支持++Inserted++ →Inserted， ~~Del~~ →Del
      markdown-it-mark支持==marked==→inserted
      markdown-it-katex支持katex公式
      markdown-it-toc-and-anchor支持@[toc]生成目录
      anchors: 这个按照我上边的默认值写就行
      
      ```yaml
          # Minimum level for ID creation. (Ex. h2 to h6)
          level: 2
          # A suffix that is prepended to the number given if the ID is repeated.
          collisionSuffix: ''           
          # If `true`, creates an anchor tag with a permalink besides the heading.
          permalink: false              
          # Class used for the permalink anchor tag.
          permalinkClass: header-anchor
          # Set to 'right' to add permalink after heading
          permalinkSide: 'left'
          # The symbol used to make the permalink
          permalinkSymbol: ¶
          # Transform anchor to (1) lower case; (2) upper case
          case: 0
          # Replace space with a character
          separator: '-'
      ```
      
   2. 修改文件
   
      添加插件你可以
   
      ```yaml
        plugins:
          - markdown-it-sub
          - markdown-it-sup
          - ...
      ```
   
      也可以
   
      ```yaml
        plugins:
       	- plugin:
       		 name: markdown-it-sub
       		 enable: false	#false就是不开启这个插件
       	- plugin:
       		 name: markdown-it-sup
       		 enable: false	#false就是不开启这个插件
          - ...
      
      ```
   
      ```yaml
        plugins:
          - markdown-it-sub
          - markdown-it-sup
          - markdown-it-footnote
          - markdown-it-ins
          - markdown-it-mark
          - markdown-it-katex
          - markdown-it-toc-and-anchor
      ```
   
   3. 增加插件
      如果你想用其他的插件，你可以自己下载
      `npm install markdown-it-... --save`
   
      

支持katex公式
1. 修改_config.yml的 plugins，增加katex插件

  plugins:
   - markdown-it-katex

2. 给你主题的中引入一个css，一般路径主题/source/css，找到对应的文件，加上https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.9.0/katex.min.css

3. 这个地方是在next的_config.yml里面填写的

   ```yaml
     katex:
     copy_tex_js:
     copy_tex_css: https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.9.0/katex.min.css
   ```

最后一定要记得`hexo clean` 之后再`hexo g` `hexo s`

> [hexo markdown渲染器 @upupming/hexo-renderer-markdown-it-plus](https://blog.csdn.net/qq_36667170/article/details/105846999)
>
> [Hexo Next主题渲染 Latex 公式的配置方法](https://roro4ever.github.io/2019/12/01/hexo-Next%E4%B8%BB%E9%A2%98%E6%B8%B2%E6%9F%93-latex-%E5%85%AC%E5%BC%8F%E7%9A%84%E9%85%8D%E7%BD%AE%E6%96%B9%E6%B3%95/hexo-next%E4%B8%BB%E9%A2%98%E6%B8%B2%E6%9F%93-latex-%E5%85%AC%E5%BC%8F%E7%9A%84%E9%85%8D%E7%BD%AE%E6%96%B9%E6%B3%95/)
>
> [让 Hexo Next (v8.0.0) 支持 LaTeX 数学公式](https://dog.wtf/tech/making-hexo-next-theme-latex-math-equation-supported/)

## hexo博客站点sitemap

> [hexo博客站点sitemap的使用](https://eericzeng.github.io/2019/07/14/hexo%E5%8D%9A%E5%AE%A2%E7%AB%99%E7%82%B9sitemap%E7%9A%84%E4%BD%BF%E7%94%A8/)
>
> [Hexo博客站点地图配置（Google）](https://mizeri.github.io/2021/04/18/hexo-sitemap-google/)
>
> ## [Baidu/Google站点地图](Baidu/Google站点地图)

## hexo的next主题美化设置

> [Hexo的Next主题美化设置](https://blog.mrzorg.top/Hexo/2020-02-12-hero-next-theme-settings/)
>
> [Hexo next主题博客搭建及美化](https://segmentfault.com/a/1190000021486019)
>
> [在 Hexo 中添加豆瓣个人主页](https://blog.csdn.net/qq_38157825/article/details/112783187)
>
> [Hexo 加入豆瓣读书页面](https://tding.top/archives/c7ba3a41.html)

## hexo同步管理以及迁移

### 将hexo部署环境上传到GitHub方法

- github上切换到hexo分支，`git clone`仓库到本地。
- 此时本地会多出一个`username.github.io`文件夹，命令行`cd`进去，删除除`.git`文件夹（如果你看不到这个文件夹，说明是隐藏了。windows下需要右击文件夹内空白处，点选'显示/隐藏 异常文件'，Mac下我就不知道了）外的其他文件夹。
- 命令行`git add -A`把工作区的变化（包括已删除的文件）提交到暂存区（ps:`git add .`提交的变化不包括已删除的文件）。
- 命令行`git commint -m "some description"`提交。
- 命令行`git push origin hexo`推送到远程hexo分支。此时刷下github，如果正常操作，hexo分支应该已经被清空了。
- 复制本地`username.github.io`文件夹中的`.git`文件夹到hexo项目根目录下。此时，hexo项目已经变成了和远程hexo分支关联的本地仓库了。而`username.github.io`文件夹的使命到此为止，你可以把它删掉，因为我们只是把它作为一个“中转站”的角色。以后每次发布新文章或修改网站样式文件时，`git add . ; git commit -m "some description" ; git push origin hexo`即可把环境文件推送到hexo分支。然后再`hexo g -d`发布网站并推送静态文件到master分支。

至此，hexo的环境文件已经全部托管在github的hexo分支了

### 在新的电脑部署原hexo博客

首先是git有ssh key密钥之类的 ，这一部分略去，后续有时间专门介绍

```shell
git clone git@github.com:Josephucas/Josephucas.github.io.git
#有些库下载不了，得用国内源，我后面就直接cpm了
npm config set registry https://registry.npm.taobao.org
npm install -g cnpm --registry=https://registry.npm.taobao.org

cnpm install hexo-cli -g
#在根目录下cnpm install
#然后直接hexo g hexo s 试一下

```



### 关于next自定义主题的有些问题

一般我们在下载主题的时候都是在themes文件夹下直接git clone某仓库的，这样的话，仓库的文件夹下会直接留下.git文件这个文件在这里的时候，会导致你在博客根目录的时候，会发现这里还有一个.git文件，就会直接作为第三方的仓库，这样的坏处是，我们往往会对next主题进行一些魔改的地方就不能被同步的

所以我这边就直接把.git和gitignore删掉

并且，如果在github上还是以第三方仓库的形式，需要先git删除掉自己当初上传的themes

如在根目录下

```shell
git rm -r --cached D:\github\Josephucas.github.io\themes\hexo-theme-next
```

这样取消对next之前的追踪记录

然后再重新上传，就ok了

```shell
git add -A ；git commit -m "some description" ; git push origin hexo
```

​	但是这样还是会有一个问题，我们的next主题的_config.yml里面往往会有一些私人信息，比如一些插件的账号和密码，这些往往是我们不想让别人知道的，我第一次的时候就直接泄露了gitalk的密码，

​	后面我搜索了很多关于git删除记录的方法，其他的都很麻烦，用bfg还算是比较方便的

```sh
java -jar bfg-VERSION .jar YOUR-REPOSITORY/ .git --delete-files "config.py"
```

​	但是最后还是直接到github里面的gitalk里面把原来的密钥删掉，生成新的密钥，是最方便的，然后到博客根目录的gitignore里面直接把 config文件加入忽略上传，并且删掉原来的config文件，我自己通过第三方（网盘或者U盘或者微信）同步config文件

```shell
git rm -r --cached "D:\github\Josephucas.github.io\themes\hexo-theme-next\_config.yml"
git commit -m "some discription";git push origin hexo
```



> [hexo博客同步管理及迁移](https://www.jianshu.com/p/fceaf373d797)
>
> [十分鐘超詳細替 Hexo Next 開啟 Gitalk 留言版](https://hsiangfeng.github.io/hexo/20191206/2397475810/)
>
> [在GitHub上公开秘密：泄露凭证和API密钥后该怎么办](https://blog.csdn.net/dfsgwe1231/article/details/105993314)

