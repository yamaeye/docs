
@[独行者](https://www.pdawiki.com/forum/space-uid-182843.html)：

## [MDX规范](https://www.pdawiki.com/forum/thread-35617-1-1.html?_dsign=66fe3c91)

词条由三部分组成：

- 词条关键字：作为词条索引
- 词典 HMTL：词条内容。去掉了 `<html>`、`<head> `和 `<body>` 标签的包裹，另外增加了一些 mdict 自有的标记和格式。
- 分隔符 `</>`：分割每个词条（后面不允许有任何空行）

###  css 和 js 文件

```html
Antarctica
<link href="styles_cb.css" rel="stylesheet"/>
<script src="scripts_cb.js"></script>
<div>南极洲</div>

</>
```

CSS建议删掉 `@charset "utf-8";`，因为欧路词典和 GoldenDict 本身就是以 UTF-8 打开的，无需再多此一举，增加了反而会导致欧路词典解析出错。

### 音频

```html
<a href="sound://sound_file.mp3">keyword</a>
```

### 图片

```html
<img src="file://abc.gif">
<img src="/abc.gif">
<img src="abc.gif">
```

### 跳转

```html
<a href="entry://ought to">
锚点：
<a href="entry://look#verb">
```

跳转到单词（只允许使用一次）：

```
@@@LINK=ought to
```

### 文件

引入资源文件时根目录为 `mdx` 所在目录。当资源文件数量极多时，建议将资源文件打包为 mdd。mdd 必须和 mdx 存放在同一目录下，有多个 mdd 文件时，文件名以 xx.mdd、xx.1.mdd，xx.n.mdd，词典软件都会读取。

推荐将图片和 css、js 和字体打包为 xx.mdd，将语音打包为 xx.1.mdd，这样不想要语音文件的用户只需拷贝 xx.mdd 而不丢失样式排版。裸露的资源文件优先级 > mdd 中的资源文件。

### [mdxbuilder 3.0 rc1](https://www.pdawiki.com/forum/thread-33114-1-1.html)

官方的制作工具。不要用 4.0，4.0 版本生成的 mdx 还未被解析出来，暂不被第三方软件支持。

- Source：即词典原始数据文本路径，扩展名随意。
- Target：目标词典文件路径，扩展名必须为 mdx。
- Sytle：留空，这个用不到。
- Data：资源数据路径，有就填，没有就不填。注意资源数据一定要存放到一个单独的文件夹 xx 中，不要直接全部分散在 mdx 目录下，而且这个 xx 文件夹并不会打包到 mdd 中，它会作为 mdd 资源数据的根目录。

![MdxBuilder](https://i.loli.net/2019/08/26/EC1btaqemhPUwS3.png)

- Original：一定要选 Mdict(Compact HTML)，这种格式就是我们上面提到的规范。
- Encoding：为避免乱码，必须选 UTF-8(Unicode)。
- Title：词典标题，可以被欧路词典读取到。
- Description：词典描述，支持 HTML 标签，不过支持十分有限，词典软件可以读取到。
- 未提到的其他选项不管。