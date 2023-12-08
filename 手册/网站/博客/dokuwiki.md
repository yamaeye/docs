
### [解决dokuwiki中文文件乱码问题](https://blog.csdn.net/zhang_peisheng/article/details/131619350)

修改`.lib\plugins\config\settings`目录下`config.metadata.php`文件。

找到`$meta['_basic']   = array('fieldset');`，在下一句增加：

```
$meta['fnencode' ] = array('string');
```

重新启动网站后，配置页面的`基本设置`会出现一项新的配置：`非ASCII文件名的编码方法`选择`utf-8`，然后保存即可。

### [更换logo](https://cloud.tencent.com/developer/ask/sof/102546453)

打开网站，右上角进入`媒体管理器`，选择根目录下的wiki路径，上传`logo.png`

### [新窗口打开外部链接](https://zhuanlan.zhihu.com/p/600209878)

配置管理器 - 链接设置 - 外部链接的目标窗口：`_blank`

### [文内插入链接](https://www.dokuwiki.org/zh:wiki:syntax)

外部链接：

```
 [[http://www.地址.com|名称]]
```

内部链接：

```
 [[目录:页面名#章节名|名称]] 
```

## [主题](http://ciangbrides.myds.me/dw/dokuwiki/template)

### [vector主题](https://www.lainme.com/doku.php/blog/2010/09/dokuwiki%E4%B8%BB%E9%A2%98_vector)

自定义LOGO：将图片命名为logo和favicon.ico，放入`.\lib\tpl\vector\user`目录下。

[DEMO](https://wiki.geany.org/newsletter/start)

### [Argon](https://github.com/IceWreck/Argon-Dokuwiki-Template)

![DEMO](https://github.com/IceWreck/Argon-Dokuwiki-Template/raw/master/screenshots/1.png)

### [material](https://github.com/LeonStaufer/material-dokuwiki)

![DEMO](https://camo.githubusercontent.com/b6d1f7b1ca77ead8318dc6d44ad367f68fadaca0208633ea69fe5700b58e02cc/68747470733a2f2f692e696d6775722e636f6d2f315169626d4b672e6a7067)

### [writr](https://github.com/selfthinker/dokuwiki_template_writr)

![DEMO](https://www.dokuwiki.org/_media/template:writr_sample.png)

### [sprintdoc](https://github.com/cosmocode/dokuwiki-template-sprintdoc)

![DEMO](https://www.dokuwiki.org/_media/template:sprintdoc-annotated.png?cache=)
### [bootstrap3](https://github.com/giterlizzi/dokuwiki-template-bootstrap3)

![DEMO](https://www.dokuwiki.org/lib/exe/fetch.php?tok=38e4f8&media=http%3A%2F%2Flotar.altervista.org%2Fdokuwiki%2F_media%2Fwiki%2Ftemplate%2Fbootstrap3-template.png)



## 插件

### [安装插件](https://www.dokuwiki.org/zh-tw:plugins)

- 下载扩展并将其解压缩到 `dokuwiki/lib/plugins/<base-plugin-name>`
- 打开网站，右上角进入`管理 - 扩展管理器`

### [markdowku](http://sunyongfeng.com/201704/administrator/dokuwiki/plugin)

可直接在 wiki 页上写 markdown 语法文本，不需要特殊处理。

### [indexmenu](https://myds.cloud/dokuwiki/%E6%B7%BB%E5%8A%A0%E4%BE%A7%E8%BE%B9%E6%A0%8F%E5%92%8C%E7%B4%A2%E5%BC%95)

添加侧边栏和索引

创建`sidebar`页面，在侧边栏显示3级目录， 并隐藏`sidebar` 和 `start` 页面，宽度可在`模板设置样式`里调整：

```
{{indexmenu>..#3|navbar nocookie skipfile+/(^|:)(start|sidebar)$/}}
```

### [move](https://www.gualaohan.com/post/564)

移动页到其它名称空间，移动页面的同时移动对应的媒体，修改链接到它的页面链接。想要修改wiki词条，就直接在页面右边的工具栏选`页面重命名`。

### [prosemirror](https://myds.cloud/start)

比较轻便美观的可视化编辑器

### [imgpaste](https://myds.cloud/start)

在编辑器直接粘贴就可以插入剪贴板中的图片

### [upgrade](https://myds.cloud/start)

直接在管理界面进行升级新版本

### [tag](https://www.ichiayi.com/wiki/tech/dokuwiki_plugin)

只要在 wiki 頁面輸入以下語法，就可以创建 tag（每個 tag 間以空格隔開）：

```
{{tag>tag1 tag2 tag3}}
```

### [cloud](https://www.lainme.com/doku.php/blog/2010/08/dokuwiki%E6%8F%92%E4%BB%B6%E4%B8%8E%E4%B8%BB%E9%A2%98%E6%8E%A8%E8%8D%90)

标签云：

```
~~TAGCLOUD[showCount]:50~~
```

### [插件集](https://zhuanlan.zhihu.com/p/600209878)

- [EditTable](https://github.com/cosmocode/edittable)：提供一个可视化的表格编辑和插入界面
- mathjax：对维基页面中的TeX数学表达式进行解析
- mathpublish：数学公式渲染
- zotero：从zotero引用文献
- refnotes：文献管理与引用，很灵活很强大，配置上有些复杂
- styler：这个插件为你的文本提供额外的格式化：扩展引文、附言、诗句等。
- Note：信息提示栏。可以在页面中插入醒目的提示文字，有几种默认图标和样式
- box：在方框中突出显示你的维基中特别重要的部分
- [SyntaxHighlighter4](https://github.com/crazy-max/dokuwiki-plugin-syntaxhighlighter4)：语法高亮
- codemirror：CodeMirror编辑器，用于 DokuWiki 的语法高亮
- Blockquote：可内嵌的区块语法，blockquote、QUOTE、quote、q语法
- [discussion](https://github.com/dokufreaks/plugin-discussion)： 添加评论区域
- backlinks：反向链接，列出所有链接到给定页面的页面，使用第一个标题作为链接标题。
- Select：创建下拉菜单，将用户导航至所选链接
- DocNavigation ： 显示上一篇文章、下一篇文章、目录页
- pagenav ： 显示上一页下一页等
- randompage：（随机页面）只有一个动作并无按钮，需要自定义
- rss：在DokuWiki中显示RSS源
- sync：同步dokuwiki
- [gitbacked](https://github.com/woolfg/dokuwiki-plugin-gitbacked)：Store/Sync pages and media files in a git repository
- html5video2：使用video.js用html5和flash-fallback播放mp4视频
- [mdpage](https://github.com/mizunashi-mana/dokuwiki-plugin-mdpage)：Markdown Page
- [ckgedit](https://github.com/turnermm/ckgedit)：比较实用的编辑器
- [translation](https://github.com/splitbrain/dokuwiki-plugin-translation)：显示页面的可用翻译列表。