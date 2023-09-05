
### [解决dokuwiki中文文件乱码问题](https://blog.csdn.net/zhang_peisheng/article/details/131619350)

修改`.lib\plugins\config\settings`目录下`config.metadata.php`文件。

找到`$meta['_basic']   = array('fieldset');`，在下一句增加：

```
$meta['fnencode' ] = array('string');
```

重新启动网站后，配置页面的`基本设置`会出现一项新的配置：`非ASCII文件名的编码方法`选择`utf-8`，然后保存即可。

### [更换logo](https://cloud.tencent.com/developer/ask/sof/102546453)

打开网站，右上角进入`媒体管理器`，选择根目录下的wiki路径，上传`logo.png`

### [vector主题](https://www.lainme.com/doku.php/blog/2010/09/dokuwiki%E4%B8%BB%E9%A2%98_vector)

自定义LOGO：将图片命名为logo和favicon.ico，放入`.\lib\tpl\vector\user`目录下。

### [新窗口打开外部链接](https://zhuanlan.zhihu.com/p/600209878)

配置管理器 - 链接设置 - 外部链接的目标窗口：`_blank`

### [文内插入链接](https://www.dokuwiki.org/zh:wiki:syntax)

```
 [[http://www.地址.com|名称]]
```

## 插件

### [安装插件](https://www.dokuwiki.org/zh-tw:plugins)

- 下载扩展并将其解压缩到 `dokuwiki/lib/plugins/<base-plugin-name>`
- 打开网站，右上角进入`管理 - 扩展管理器`

### [markdowku](http://sunyongfeng.com/201704/administrator/dokuwiki/plugin)

可直接在 wiki 页上写 markdown 语法文本，不需要特殊处理。

### [indexmenu：添加侧边栏和索引](https://myds.cloud/dokuwiki/%E6%B7%BB%E5%8A%A0%E4%BE%A7%E8%BE%B9%E6%A0%8F%E5%92%8C%E7%B4%A2%E5%BC%95)

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
