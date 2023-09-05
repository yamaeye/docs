#### [remotely save 插件：坚果云双端同步](https://zhuanlan.zhihu.com/p/547381761)

1. 登陆坚果云网络账户，获取授权码并在 Remotely Save 插件中进行配置。
2. App 新建库，库名称和PC端保持一致，放在容易找到的路径下。
3. PC端的库中找到 `.obsidian/plugins/` 中的 `remotely_save` 文件夹，整体复制到 App 中“容易找到的路径”下的镜像位置（plugins 文件夹需要自行建立）。
4. 手机端不需要再配置 remotely_save 了，直接在 app 启用插件并使用即可。

#### [Spaced Repetition 插件：间隔重复](https://zhuanlan.zhihu.com/p/558326315)

默认只要在笔记中写入#flashcards，就能将笔记中包含的“问题|回答卡片”归纳进flashcards卡组。可以在左侧菜单栏的复习卡片选项中查看和复习卡组。

也可以自定义标签，这需要在设置中进行配置（卡片标签配置中增加对应标签）。允许使用分层标签，SR可以自动解析成对应的层次机构。如`#flashcards/sub1/sub2`。

在加入标签后，必须定义问题（卡片），否则不会在卡组信息中显示。每条笔记只能定义一个卡组，若有多个卡组标签，优先归为最先定义的卡组。


1. **单行卡片**：单行内完成问题(Question)和回答(Answer)定义，即简单的问答形式。定义方法：

```
Question::Answer
```
2. **单行翻转卡片**：单行内完成问题(Question)和回答(Answer)定义，同时问题和答案可以相互翻转（答案变成问题，问题变成答案）。定义方法：

```
Question:::Answer
```
3. **多行卡片**：多行内完成问题(Question)和回答(Answer)定义。适用于相对复杂的问题。定义方法：

```
Question
?
Answer
```
4. **多行翻转卡片**：多行内完成问题(Question)和回答(Answer)定义，同时问题和答案可以相互翻转。定义方法：

```
Question
??
Answer
```
5. **完形填空卡片**：可将文档中的高亮或者加粗自动解析为填空。定义方法：

```
Question==Answer==
```

#### [Advanced Tables 插件：自动格式化表格](https://www.readinghere.com/blog/obsidian-advanced-tables-plugin/)

1. 制表过程中自动美化编辑模式下的表格格式。
2. 输入表格只需要写一个「｜」，写入第一个表头后，可以通过 Tab 切换到下一格，enter 换行来完成整个表格的输入。
3. 或者点击左侧栏上的`Advanced Tables Toolbar`，右侧弹出操作选项，点击即可。
4. 添加、删除、移动行和列。
5. 设置列的对齐方式 （左对齐、居中、右对齐）。
6. 对指定的列进行排序。

#### [Media Extended 插件：音视频播放](https://zhuanlan.zhihu.com/p/362853550?ivk_sa=1024320u)

可以嵌入本机、YouTuBe 、B站的视频到 Obsidian内来播放，支持从指定时间处播放，指定播放区间来播放，针对播放速度控制、循环、自动播放、静音、隐藏控件等内容也提供了自定义控制的选项。

```
`![[视频.mp4#t=12,23]]` 
```
是指从视频的第12秒开始，第23秒结束，如果用 iframe 则可以将 Obsidian 库外的视频进行内嵌，同样支持 `#t=` 的语法。

或者每点一次视频播放窗口右上角的五角星，就会在笔记中插入一个时间链接。点击时间戳，可以跳到该时间下的视频继续观看。


#### [Commander 插件：自定义工具条](https://ios.sspai.com/post/75847)

每使用一个功能都要打开命令面板进行搜索还是比较繁琐，这个插件可以设置方便直接点击的图标。

所有图标的最下方会出现一个小加号+，点击即可添加命令。可以把命令添加至 UI 界面的各个区域，包括标题栏、状态栏、侧边栏、页头、文件菜单、右键菜单等。


1. 增加、删除想要 pin 的命令，并为命令设置显示的别名与图标。
2. 隐藏核心插件或社区插件自带的命令图标。
3. 支持修改显示顺序。
4. 支持设置移动端、桌面端各显示哪些命令。

#### [Note Refactor 插件：笔记重组与拆分](https://zhuanlan.zhihu.com/p/491766682)

把所有内容写在一篇笔记时，写到后面发现内容已经很庞大，如果想拆分为多篇笔记，手动将一段段内容剪切出去非常麻烦，这时可以通过 Note Refactor 一键将一篇笔记通过标题进行拆分。

#### [Remember cursor position 插件：记住上次打开文件时光标的位置](https://zhuanlan.zhihu.com/p/441013488)

在笔记之间切换、从链接到链接、返回时非常方便，无需滚动到上次所在的位置。

#### [Recent Files 插件：最近浏览](https://wiki.eryajf.net/pages/b20c99/#slated)

当库里的文件多了起来后，我们会经常陷入忘了上上个打开的文件是什么的困境。对于有浏览打开文件历史需求的人来说，Recent files 可在侧边栏显示最近打开的文件列表。

#### [Show Whitespace 插件：显示空格](https://zhuanlan.zhihu.com/p/487604071)

开启插件后，可以看到空格和换行。

#### [Tag Wrangler 插件：快速更改标签](https://zhuanlan.zhihu.com/p/354650871)

右键点击列表中的标签时会出现操作命令：删除、搜索、重命名等。如果需要对已在很多文档中使用的标签进行更改，重命名后全库内的所有同名标签都会被自动更改。

#### [Editing Toolbar：Markdown语法工具栏](https://zhuanlan.zhihu.com/p/580851046)

会在最上层显示类似Word一样的工具栏，简洁，快速完成MD指令。

#### [Shortcuts extender 插件：快捷输入](https://www.zhihu.com/question/497487995)

提供了6级标题的快捷键，Ctrl+1 = H1，Ctrl+2 = H2……以及一些其他特殊符号的快捷键。

#### [Find unlinked files 插件：查找未链接 / 未创建的文档](https://zhuanlan.zhihu.com/p/353449575)

遍历整个保管库并搜索没有反向链接的文件。执行指令后将创建一个文件，其中包含指向这些未链接文件的链接列表。现在您可以删除这些未使用的文件或将它们链接到某个位置。

#### [pandoc插件：输出word文档](https://zhuanlan.zhihu.com/p/500709585)

Pandoc 本身就是一个 app，Ob 只是借助 Pandoc 插件去调用 Pandoc. exe 进而将 markdown 文件转化为 docx 或者是 pptx。

1. 安装 [Pandoc](https://link.zhihu.com/?target=https%3A//www.pandoc.org/installing.html) 软件和插件
2. 设置obsidian-pandoc插件路径，精确到 `pandoc. exe`
3. 把图片做成可外链访问查看的形式