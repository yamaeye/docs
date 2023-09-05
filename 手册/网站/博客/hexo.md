>#### 来源<!-- {docsify-ignore} -->

>[hexo官方文档](https://hexo.io/zh-cn/docs/setup)   
>[hexo史上最全搭建教程](https://blog.csdn.net/sinat_37781304/article/details/82729029)  


### Hexo搭建步骤


1. 安装Git

2. 安装Node.js

3. 安装Hexo

4. GitHub创建个人仓库

5. 生成SSH添加到GitHub

6. 将hexo部署到GitHub

7. 设置个人域名

8. 发布文章


## 安装hexo

1. 先创建一个文件夹，然后cd到这个文件夹下

（或者在这个文件夹下直接右键git bash打开）

2. 输入命令

```
npm install -g hexo-cli
```

3. 用`hexo -v`查看一下版本


## 初始化hexo


```
hexo init <folder>
```
`folder`是自定义的文件夹。

如果没有设置`folder`，Hexo默认在目前的文件夹建立网站。

```
cd <folder>
npm install
```


新建完成后，指定文件夹目录下有：

`node_modules`: 依赖包

`public`：存放生成的页面

`scaffolds`：生成文章的一些模板

`source`：用来存放你的文章

`themes`：主题

`_config.yml`: **博客的配置文件**


## 新建一篇文章

```
hexo new [layout] <title>
```
如果没有设置layout，默认使用 `_config.yml` 中的 `default_layout` 参数代替。

如果标题包含空格，请使用引号括起来。

```
hexo new "post title with whitespace"
```
Hexo默认会创建一个以标题为名字的目录，并在目录中放置一个 `index.md` 文件。

可以使用参数`-p`自定义新文章的路径：
```
hexo new page --path about/me "About me"
```
以上命令会创建一个 `source/about/me.md` 文件，title 为 `"About me"`


## scaffolds/模板

新建文章时，Hexo 会根据 `scaffolds` 文件夹内相对应的文件来建立文件：

```
hexo new photo "My Gallery"
```
在执行这行指令时，Hexo 会尝试在 `scaffolds` 文件夹中寻找 `photo.md`，并根据其内容建立文章。


分类具有顺序性和层次性，而标签没有顺序，是同级的。

如下指定方法，会使分类`Life`成为`Diary`的子分类：

```
categories:

- Diary

- Life

tags: 
- PS3

- Games

```
如果你需要为文章添加多个分类，可以尝试以下方法：


```
categories:

- [Diary, PlayStation]

- [Diary, Games]

- [Life]

```
这篇文章同时包括三个分类： `PlayStation` 和 `Games` 分别是父分类 `Diary` 的子分类，同时 `Life` 是一个没有子分类的分类。


## 支持的格式

Hexo 支持以任何格式书写文章，只要安装了相应的渲染插件。

只需要将文章的扩展名从 `md` 改成 `ejs`，Hexo 就会使用 `hexo-renderer-ejs` 渲染这个文件，其他格式同理。


## 发表草稿

Hexo 有三种默认布局：`post`、`page` 和 `draft`。将被保存到不同的路径：

post：`source/_posts`

draft：`source/_drafts`

page：`source`

自定义的其他布局和 `post` 相同，都将储存到 `source/_posts` 文件夹。

```
hexo publish [layout] <filename>
```

## 打开hexo服务

```
hexo g //generate生成静态文章

hexo server //启动服务器

```

默认访问网址为：`https://localhost:4000/`

使用`ctrl+c`可以把服务关掉。

如果发现对站点的更改无论如何也不生效，可以清除一下之前生成的东西：
 
```
hexo clean
```

## [排查故障](https://github.com/hexojs/hexo/issues/1837)

To find the error in which file：

```
hexo generate --debug
```

## 将hexo部署到GitHub


1. 需要先安装deploy-git ，才能用命令部署到GitHub。


```
npm install hexo-deployer-git --save
```

2. 打开站点配置文件`_config.yml`，翻到最后，修改为`YourgithubName`(你的GitHub账户)


```
deploy:

type: git

repo: https://github.com/YourgithubName/YourgithubName.github.io.git

branch: master

```

3. 部署时可能需要输入username和password


```
hexo g

hexo d //deploy部署网站

```

---

## [部署到Vercel](https://www.bilibili.com/read/cv11239428)

使用npm安装Vercel控制台客户端:

```
npm install -g vercel
hexo g
cd public
vercel
```

第一次会提示你登录。输入你注册Vercel账号的邮箱地址，打开邮件点击验证（VERIFY）按钮。

提示登录成功后，再执行：

```
vercel --prod
```

## [部署到cloudflare page](https://blog.kukmoon.com/6cc87dff/)

把“框架预设”设置为 `None`，在“构建命令”文本框中输入 `exit 0`，这表示只是把仓库的内容克隆到 Cloudflare Pages，但是不进行任何操作。

## [Busuanzi网站统计失效问题](https://blog.csdn.net/lijing742180/article/details/87928437)

主题中默认集成了第三方统计服务 Busuanzi 来统计网站数据，但是实际并没有生效。

问题原因是由于 `busuanzi(不蒜子)` 的域名更新，导致了使用 Hexo Next 主题时统计数据失效。

不蒜子的域名由原来的 `dn-lbstatics.qbox.me` 更换为了 `busuanzi.ibruce.info`。


以 Hexo Next 主题为例：
1. 进入 `\themes\next\layout_third-party\analytics` 目录

2. 打开 `busuanzi-counter.swig`

3. 将 `src="https://dn-lbstatics.qbox.me/busuanzi/2.3/busuanzi.pure.mini.js"` 修改为 `src="https://busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"`

4. 使用 hexo g 、hexo d 命令重启服务器即可生效。


---

## [隐藏部分文章](https://github.com/Jamling/hexo-generator-index2/blob/master/README_zh.md)

想搞一些花里胡哨的东西，例如某些福利、妹子图、日记，但是又不想放在首页，影响气质，怎么办呢？人真是复杂的动物啊。

hexo默认是会把所有文章按照时间顺序排列，分页展示。百度上查到一个黑科技，但有一个bug：文章是隐藏了，但是分页计数仍然计算。

假设首页十篇文章都设置隐藏，那首页就是空白的一页，而不会显示第二页的文章。这怎么能忍，果断放弃。

后来又在Hexo插件库找到一个产生首页的插件，自带过滤功能：[`hexo-generator-index2`](https://github.com/Jamling/hexo-generator-index2/blob/master/README_zh.md)


输入以下命令:

```
npm install hexo-generator-index2 --save

npm uninstall hexo-generator-index --save

```

`hexo-generator-index2`可以完全替代官方的`hexo-generator-index`，所以安装之后，先卸载官方的插件，不然会引起一些冲突。

打开hexo博客根目录下的`_config.yml`，配置以下内容：

```YAML
# index2 generator是否包含官方的hexo-generator-index，默认true（包含）
index2_include_index: true # defult is true

# 配置index2 generator，可以是数组或对象
index2_generator:

per_page: 10

order_by: -date # 按发布时间排序

include:


- category Web # 只包含Web分类下的文章

exclude:


- tag Hexo # 不包含标签为Hexo的文章
```

>#### 来源<!-- {docsify-ignore} -->
>[hexo首页优雅的隐藏部分文章](https://blog.csdn.net/qq_15602635/article/details/83479980)

