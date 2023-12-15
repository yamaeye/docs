## 安装

```
npm i docsify-cli -g
```

## 初始化

```
docsify init ./docs
```

将创建以下文件：

- `index.html` 入口文件
- `README.md` 作为主页内容渲染
- `.nojekyll` 用于阻止 GitHub Pages 忽略掉下划线开头的文件

## 预览

```
docsify s
```

## 问题

### [一直Loading](https://zhuanlan.zhihu.com/p/663807103)

css和js都是从`cdn.jsdelivr.net`所导入的，但是国内访问jsdelivr的速度就很……

解决方法是将文件从本地引入，或改成其它域名引入。

在`index.html`中找到这几行代码：

```html
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4/lib/themes/vue.css">
  <script src="//cdn.jsdelivr.net/npm/docsify@4"></script>
```

然后把它们改成：

```html
 <link rel="stylesheet" href="//fastly.jsdelivr.net/npm/docsify@4/lib/themes/vue.css">
  <script src="//fastly.jsdelivr.net/npm/docsify@4"></script>
```

