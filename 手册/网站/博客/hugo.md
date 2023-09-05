## 生成站点

比如希望生成到 /path/to/site 路径：

```
hugo new site /path/to/site
```

## 创建文章

创建页面到`文件夹/文件名.md`：

```
hugo new 文件夹/文件名.md
```

## 调试+部署

```
hugo server
hugo
```

---

## [支持内联html块](https://zhuanlan.zhihu.com/p/363943183)

以前，Hugo使用`Blackfriday`渲染Markdown文件。从`Hugo 0.60`版本开始，默认的Markdown渲染器已更改为`goldmark`。在goldmark中，默认设置是不呈现原始HTML标签。

要解决此问题，有两个选择。

1. 设置`blackfriday`为默认的Markdown引擎。打开`config.toml`并添加以下设置：

```
[markup]

defaultMarkdownHandler = "blackfriday"
```

2. 使用`goldmark`和设置`unsafe`选项：

```
[markup]

defaultMarkdownHandler = "goldmark"

[markup.goldmark]


[markup.goldmark.renderer]unsafe = true
```

## [在netlify平台上使用Hugo主题样式](https://www.andbible.com/post/hugo-hosting-and-deployment-hosting-on-netlify/)

Netlify平台上Hugo不支持`git clone`方法安装主题样式. 如果使用了git clone, Netlify会要求您递归删除主题目录theme中的.git子目录, 因此阻止了主题未来版本的兼容性.

更佳的方法是通过`git submodule`来安装theme.

```
cd themes
git submodule add https://github.com/<THEMECREATOR>/<THEMENAME>
```
