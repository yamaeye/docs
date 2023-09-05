>#### 来源
>[**菜鸟教程**](https://www.runoob.com/html/html-tutorial.html)  
>[**W3school**](https://www.w3school.com.cn/h.asp)

## 图像

```html
<img src="https://www.url.jpg" alt="替换文本" width="300" height="500">
```

## 音频

```html
<audio src="https://www.url.mp3">您的浏览器不支持该音频格式（提示文本）。</audio>
```

## 视频

```html
<video src="https://www.url.mp4" width="320" height="240">您的浏览器不支持该视频格式（提示文本）。</video>
```

## 链接

```html
<a href="https://www.url.com/">链接文本（图片或其他元素也可以）</a>
```

### ID属性

```html
<a id="tips">提示部分</a>
<a href="#tips">链接到"提示部分"</a>
```

## align属性

规定元素中内容的水平对齐方式。

`left`：左对齐

`right`：右对齐

`center`：居中

`justify`：两边对齐


居中对齐：

```html
<div align="center">

This is some text!
</div>
```

## 速查表

| 标签 | 功能 |
| :--- | :---: |
| `<br />` | 折行 |
| `<hr />` | 水平线 | 
| `<wbr>` | 单词换行时机 |
| `</b>` | 粗体 |
| `</del>` | 删除线 |
| `</ins>` | 下划线 |
| `</sup>` | 上标 |
| `</sub>` | 下标 |
| `</blockquote>` | 块引用 |
| `</q>` | 短引用 |

## 结构框架

```html
<!-- 声明为 HTML5 文档，有助于浏览器正确显示网页。 -->
<!DOCTYPE html>
<html>
<!-- 头部元素 -->
<head>
<!-- 为避免出现中文乱码，需要将字符声明为 UTF-8 或 GBK -->
<meta charset="utf-8">
<title>页面标题</title>
</head><!-- 页面内容 -->
<body>
<h6>6级标题</h6>
<p>段落</p>
</body>
</html>
```