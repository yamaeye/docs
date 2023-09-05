## 图片

### 行内图片

图片默认以块级元素显示，如果想以内联元素显示：


```markdown
{% inlineImg [src] [height] %}
```

- **src**: 图片链接
- **height**：图片高度限制【可选】

```markdown
我漂亮吗

![](https://i.loli.net/2021/03/19/2P6ivUGsdaEXSFI.png)

我觉得很漂亮 {% inlineImg https://i.loli.net/2021/03/19/5M4jUB3ynq7ePgw.png 150px %}
```

### 相册图库

```
<div class="gallery-group-main">
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
</div>
```

- **name**：图库名
- **description**：图库描述
- **link**：连接到对应相册的地址
- **img-url**：图库封面地址

```
<div class="gallery-group-main">
{% galleryGroup '壁纸' '收藏的一些壁纸' '/Gallery/wallpaper' https://i.loli.net/2019/11/10/T7Mu8Aod3egmC4Q.png %}
{% galleryGroup '漫威' '关于漫威的图片' '/Gallery/marvel' https://i.loli.net/2019/12/25/8t97aVlp4hgyBGu.jpg %}
{% galleryGroup 'OH MY GIRL' '关于OH MY GIRL的图片' '/Gallery/ohmygirl' https://i.loli.net/2019/12/25/hOqbQ3BIwa6KWpo.jpg %}
</div>
```

#### 相册子页面

```markdown
{% gallery %}
markdown 图片格式
{% endgallery %}
```

```markdown
{% gallery %}
![](https://i.loli.net/2019/12/25/Fze9jchtnyJXMHN.jpg)
![](https://i.loli.net/2019/12/25/ryLVePaqkYm4TEK.jpg)
![](https://i.loli.net/2019/12/25/gEy5Zc1Ai6VuO4N.jpg)
![](https://i.loli.net/2019/12/25/d6QHbytlSYO4FBG.jpg)
![](https://i.loli.net/2019/12/25/6nepIJ1xTgufatZ.jpg)
![](https://i.loli.net/2019/12/25/E7Jvr4eIPwUNmzq.jpg)
![](https://i.loli.net/2019/12/25/mh19anwBSWIkGlH.jpg)
![](https://i.loli.net/2019/12/25/2tu9JC8ewpBFagv.jpg)
{% endgallery %}
```

## 样式

### 高亮文字

```markdown
{% label text color %}
```

- **text**：文字
- **color**：背景颜色，默认为 default（default/blue/pink/red/purple/orange/green）【可选】

```markdown
臣亮言：{% label 先帝 %}创业未半，而{% label 中道崩殂 blue %}。今天下三分，{% label 益州疲敝 pink %}，此诚{% label 危急存亡之秋 red %}也！然侍衞之臣，不懈于内；{% label 忠志之士 purple %}，忘身于外者，盖追先帝之殊遇，欲报之于陛下也。诚宜开张圣听，以光先帝遗德，恢弘志士之气；不宜妄自菲薄，引喻失义，以塞忠谏之路也。
宫中、府中，俱为一体；陟罚臧否，不宜异同。若有{% label 作奸 orange %}、{% label 犯科 green %}，及为忠善者，宜付有司，论其刑赏，以昭陛下平明之治；不宜偏私，使内外异法也。
```

### 友情链接

```markdown
{% flink %}
xxxxxx
{% endflink %}
```

```markdown
{% flink %}
- class_name: 友情链接

class_desc: 那些人，那些事

link_list:


- name: JerryClink: https://jerryc.me/avatar: https://jerryc.mehttps://yamaeye.github.io/docs/img/avatar.pngdescr: 今日事,今日毕


- name: Hexolink: https://hexo.io/zh-tw/avatar: https://d33wubrfki0l68.cloudfront.net/6657ba50e702d84afb32fe846bed54fba1a77add/827ae/logo.svgdescr: 快速、简单且强大的网誌框架

- class_name: 网站

class_desc: 值得推荐的网站

link_list:


- name: Youtubelink: https://www.youtube.com/avatar: https://i.loli.net/2020/05/14/9ZkGg8v3azHJfM1.pngdescr: 视频网站


- name: Weibolink: https://www.weibo.com/avatar: https://i.loli.net/2020/05/14/TLJBum386vcnI1P.pngdescr: 中国最大社交分享平台


- name: Twitterlink: https://twitter.com/avatar: https://i.loli.net/2020/05/14/5VyHPQqR6LWF39a.pngdescr: 社交分享平台
{% endflink %}
```

### 时间线

```markdown
{% timeline title,color %}
<!-- timeline title -->
xxxxx
<!-- endtimeline -->
<!-- timeline title -->
xxxxx
<!-- endtimeline -->
{% endtimeline %}
```

- **title**：标题/时间线
- **color**：颜色（default(留空) / blue / pink / red / purple / orange / green）

```markdown
{% timeline 2022,green %}
<!-- timeline 01-02 -->
这是测试页面
<!-- endtimeline -->
{% endtimeline %}
```

## 标签

### 标签页

```markdown
{% tabs Unique name, [index] %}
<!-- tab [Tab caption] [@icon] -->
Any content (support inline tags too).
<!-- endtab -->
{% endtabs %}
```

- **Unique name**: Unique name of tabs block tag without comma.
Will be used in #id's as prefix for each tab with their index numbers.

If there are whitespaces in name, for generate #id all whitespaces will replaced by dashes.

Only for current url of post/page must be unique!

- **[index]**: Index number of active tab.
如果没有指定，预设默认选择第一个。
If index is -1, no tab will be selected. It's will be something like spoiler.

Optional parameter.

- **[Tab caption]**: Caption of current tab.
If not caption specified, unique name with tab index suffix will be used as caption of tab.

If not caption specified, but specified icon, caption will empty.

Optional parameter.

- **[@icon]**: FontAwesome icon name (full-name, look like 'fas fa-font')
Can be specified with or without space; e.g. 'Tab caption @icon' similar to 'Tab caption@icon'.

Optional parameter.


预设选择tab3：

```markdown
{% tabs test, 3 %}
<!-- tab 第一个Tab -->
**tab名为第一个Tab**
<!-- endtab -->

<!-- tab @fab fa-apple-pay -->
**只有图标 没有Tab名字**
<!-- endtab -->

<!-- tab 炸弹@fas fa-bomb -->
**名字+icon**
<!-- endtab -->
{% endtabs %}
```

### 按钮

```markdown
{% btn [url],[text],[icon],[color] [style] [layout] [position] [size] %}
```

- **url**: 链接
- **text**: 按钮文字
- **icon**: 图标[可选] 
- **style**: 按钮样式，默认实心（outline/留空）[可选] 
- **color**: （default/blue/pink/red/purple/orange/green）[可选] 


- **默认style**：按钮背景顔色


- **outline**：按钮字体和边框顔色
- **layout**: 按钮布局，默认为line（block/留空）[可选] 
- **position**: 按钮位置，前提是设置了layout为block，默认为左边（center/right/留空）[可选] 
- **size**: 按钮大小（larger/留空）[可选] 

```markdown
This is my website, click the button {% btn 'https://butterfly.js.org/',Butterfly %}
This is my website, click the button {% btn 'https://butterfly.js.org/',Butterfly,far fa-hand-point-right, blue %}
This is my website, click the button {% btn 'https://butterfly.js.org/',Butterfly,block center outline red %}
This is my website, click the button {% btn 'https://butterfly.js.org/',Butterfly,far fa-hand-point-right,outline %}
This is my website, click the button {% btn 'https://butterfly.js.org/',Butterfly,far fa-hand-point-right,orange larger %}
```

### 隐藏内容

不建议有标题，因为Toc会把隐藏内容标题也显示出来，而且当滚动屏幕时，如果隐藏内容没有显示出来，会导致Toc的滚动出现异常。

#### 隐藏文字按钮

inline 在文本里添加按钮隐藏内容，只限文字：

```markdown
{% hideInline content,display,bg,color %}
```

- **content**：文本内容。不能包含英文逗号，可用`&sbquo;`
- **display**: 按钮显示的文字(可选)
- **bg**: 按钮的背景颜色(可选)
- **color**: 按钮文字的颜色(可选)

```markdown
哪个英文字母最酷？ {% hideInline 因为西装裤(C装酷),查看答案,#FF7242,#fff %}

门里站着一个人? {% hideInline 闪 %}
```

#### 隐藏内容按钮

独立的block隐藏内容，可以隐藏很多内容，包括图片，代码块等：

```markdown
{% hideBlock display,bg,color %}
content
{% endhideBlock %}
```

- **content**: 文本内容
- **display**: 按钮显示的文字。不能包含英文逗号，可用`&sbquo;`(可选)
- **bg**: 按钮的背景颜色(可选)
- **color**: 按钮文字的颜色(可选)

```markdown
查看答案
{% hideBlock 查看答案 %}
怎么可能有答案
{% endhideBlock %}
```

#### Toggle收缩框

如果需要展示的内容太多，可以把它隐藏在收缩框里，需要时再把它展开。

```markdown
{% hideToggle display,bg,color %}
content
{% endhideToggle %}
```

```markdown
{% hideToggle Butterfly安装方法 %}
在你的博客根目录里

git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/Butterfly

如果想要升级，在主题目录下

git pull

{% endhideToggle %}
```

### [提示块](https://butterfly.js.org/posts/4aa8abbe/#Note-Bootstrap-Callout)

#### 默认标识配色方案

```markdown
{% note [class] [no-icon] [style] %}
Any content (support inline tags too.io).
{% endnote %}
```

1. **class**：标识（ default / primary / success / info / warning / danger ），不同的标识有不同的配色【可选】
2. **no-icon**：不显示 icon【可选】
3. **style**：可覆盖配置中的 style（simple/modern/flat/disabled）【可选】

```markdown
{% note simple %}
默认 提示块标籤
{% endnote %}

{% note default modern %}
default 提示块标籤
{% endnote %}

{% note info no-icon %}
info 提示块标籤
{% endnote %}
```

#### 自定义标识配色

```markdown
{% note [color] [icon] [style] %}
Any content (support inline tags too.io).
{% endnote %}
```

1. color：顔色（default / blue / pink / red / purple / orange / green）【可选】
2. icon：只支持`fontawesome`图标, 也可以配置`no-icon`【可选】
3. style：可覆盖配置中的 style（simple/modern/flat/disabled）【可选】

```markdown
{% note 'fab fa-cc-visa' flat %}
你是刷 Visa 还是 UnionPay
{% endnote %}

{% note green 'fab fa-internet-explorer' disabled %}
前端最讨厌的浏览器
{% endnote %}

{% note blue no-icon %}
2021年快到了....
{% endnote %}
```

## [主题配置](https://butterfly.js.org/posts/4aa8abbe)

**本地预览404页面**：https://localhost:4000/404.html

**置顶**：`sticky`属性的数值越大，置顶的优先级越大。

**侧边栏排序**：`sort_order`属性的数值越小，排序越靠前，默认为 0。

### [自定义侧边栏](https://butterfly.js.org/posts/ea33ab97/)

在`source/_data`文件夹中，创建`widget.yml`文件：

```YAML
top:

- class_name:


id_name:


name:


icon:


html:

bottom:

- class_name:


id_name:


name:


icon:


order:


html:
```

生成的代码为：
```HTML
<div class="class_name" id="id_name" style="order">
<div class="item-headline">
<i class="icon"></i>
<span>name</span>
</div>
<div class="item-content">
html


</div>
</div>
```

#### 参数说明

- **top**: 所有页面都显示
- **bottom**: 除了文章页外都显示
- **class_name**: 父类 class 名 （可选）
- **id_name**: 父类 id 名（可选）
- **name**: 标题
- **icon**: 图标
- **order**: 排序 （可选）
- **html**: 代码

如果需要调整UI，请自行添加css到inject。

#### 访客地图案例

HTML代码为：

```HTML
<script type="text/javascript" id="clstr_globe" src="//clustrmaps.com/globe.js?d=5V2tOKp8qAdRM-i8eu7ETTO9ugt5uKbbG-U7Yj8uMl8"></script>
```

创建`widget.yml`：

```YAML
bottom:


- class_name: user-mapid_name: user-mapname: 访客地图icon: fas fa-heartbeatorder:html: '<script type="text/javascript" id="clstr_globe" src="//clustrmaps.com/globe.js?d=5V2tOKp8qAdRM-i8eu7ETTO9ugt5uKbbG-U7Yj8uMl8"></script>'
```

### [添加额外的js/css/meta等](https://butterfly.js.org/posts/ceeb73f/)

支持添加到head(`</body>`标签之前)和bottom(`</html>`标签之前)，须以标准的html格式添加内容：

```HTML
inject:

head:

	- <link rel="stylesheet" href="/self.css">

bottom:

	- <script src="xxxx"></script>
```