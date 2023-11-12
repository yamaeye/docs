>#### 来源
>[**菜鸟教程**](https://www.runoob.com/css/css-tutorial.html)  
>[**W3school**](https://www.w3school.com.cn/css/index.asp)


## margin：外边距

margin 没有背景颜色，是完全透明的。

为元素的每一侧指定外边距的属性（允许负值）：

```css
p {

margin-top: 100px;

margin-bottom: 100px;

margin-right: 150px;

margin-left: 80px;
}
```

margin 可以单独改变元素的上，下，左，右边距，也可以一次改变所有的属性：

```css
p {

margin: 25px 50px 75px 100px;
}
```

顺时针简写设置四个值：上外边距是 25px，右外边距是 50px，下外边距是 75px，左外边距是 100px


（缩略左右）设置三个值：

```css
p {

margin: 25px 50px 75px;
}
```

上外边距是 25px，右和左外边距是 50px，下外边距是 75px

（先上下，后左右）成对设置两个值：

```css
p {

margin: 25px 50px;
}
```

上和下外边距是 25px，右和左外边距是 50px

值|说明
-|-
`auto` | 浏览器来计算外边距
`length` | 以 px、pt、cm 等单位指定外边距
`%` | 指定以包含元素宽度的百分比计的外边距
`inherit` | 指定应从父元素继承外边距

## padding：内边距

![margin & padding](https://www.runoob.com/wp-content/uploads/2013/08/VlwVi.png)

为元素的每一侧指定内边距的属性（不允许负值）：

```css
div {
padding-top: 50px;

padding-right: 30px;

padding-bottom: 50px;

padding-left: 80px;
}
```

内边距被清除时，所释放的区域将会受到元素背景颜色的填充。

```css
div {
padding: 25px;
}
```

## position属性

除非首先设置了 position 属性，否则top、bottom、left和right属性将不起作用。

### static（静态）

```css
div {
position: static;
}
```

默认情况下的定位方式。

静态定位的元素不受 top、bottom、left 和 right 属性的影响。

元素不会以任何特殊方式定位；它始终根据页面的正常流进行定位。

### relative

```css
div {

position: relative;

left: 30px;
}
```

设置相对定位的元素的 top、right、bottom 和 left 属性将导致其偏离其正常位置进行调整。

不会对其余内容进行调整来适应元素留下的任何空间。

### fixed

```css
div {

position: fixed;

bottom: 0;

right: 0;

width: 300px;
}
```

即使滚动页面，它也始终位于同一位置。 

固定定位的元素不会在页面中通常应放置的位置上留出空隙。

### absolute

相对于最近的定位祖先元素进行定位（而不是相对于视口定位，如 fixed）。

然而，如果绝对定位的元素没有祖先，它将使用文档主体（body），并随页面滚动一起移动。

### sticky

根据用户的滚动位置进行定位。

粘性元素根据滚动位置在相对（relative）和固定（fixed）之间切换。

起先它会被相对定位，直到在视口中遇到给定的偏移位置为止 - 然后将其“粘贴”在适当的位置（比如 position:fixed）。

## Overflow属性

可以控制内容溢出元素框时在对应的元素区间内添加滚动条。只工作于指定高度的块元素上。


visible|内容不会被修剪（默认值）|会呈现在元素框之外
-|-|-
hidden|内容会被修剪|其余内容是不可见的
scroll|内容会被修剪|但是浏览器会显示滚动条以便查看其余的内容
auto|如果内容被修剪|则浏览器会显示滚动条以便查看其余的内容
inherit||从父元素继承 overflow 属性的值

### [滚动条样式](https://blog.csdn.net/qq_53931766/article/details/124667259)

#### 滚动条宽高及背景
```
.main::-webkit-scrollbar { 
	width: 6px;
	height:4px;
	background: #007acc;
} 
```
#### 滑块样式
```
.main::-webkit-scrollbar-thumb { 
	border-radius: 3px; 
	height: 100px;

/* 滚动条滑块长度 */
	-webkit-box-shadow: inset005pxrgba(0,0,0,0.2);
	background:rgba(0,0,0,0.2);
}
```
#### 滚动条轨道（凹槽）样式
```
.main::-webkit-scrollbar-track { 
	-webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3);

/* 较少使用 */
	border-radius: 3px; 
	background:rgba(0,0,0,0.1);
} 
```

## 重叠元素

在对元素进行定位时，它们可以与其他元素重叠。

`z-index` 属性指定元素的堆栈顺序（哪个元素应放置在其他元素的前面或后面）。

具有较高堆叠顺序的元素始终位于具有较低堆叠顺序的元素之前。

如果两个定位的元素重叠而未指定 `z-index`，则位于 HTML 代码中最后的元素将显示在顶部。

元素可以设置正或负的堆叠顺序：

```css
img {

position: absolute;

left: 0px;

top: 0px;

z-index: -1;
}
```

---

## [代码块自动换行](https://www.jarods.org/2001.html)

`<pre>` 标签的一个常见应用就是用来显示源码。如果一句代码很长，会造成代码超出边界。

用 `overflow:hidden` 会将原来的代码隐藏掉，导致显示不全。

而如果用 `overflow:auto` ，则经常出现两个滚动条（右部和底部）。

```
pre {
white-space: pre-wrap;
word-wrap: break-word;
}
```

### [white-space](https://blog.csdn.net/glorydx/article/details/112671300)

用来控制文本字符串类的空白和换行

| 属性     | 说明                                                                 |
| -------- | -------------------------------------------------------------------- |
| normal   | 忽略多余的空白，只保留一个空白（默认）                               |
| pre      | 保留空白(行为方式类似于html中的pre标签)                              |
| nowrap   | 只保留一个空白，文本不会换行，会在在同一行上继续，直到遇到br标签为止 |
| pre-wrap | 保留空白符序列，正常地进行换行                                       |
| pre-line | 合并空白符序列，保留换行符                                           |
| inherit  | 从父元素继承white-space属性的值                                      |

### word-wrap

| 属性 | 说明 |
| ---- | ---- |
|normal|只在允许的断字点换行（浏览器保持默认处理）|
|break-word|在长单词或 URL 地址内部进行换行|

## 故障

### 样式丢失

@[张三钉](https://www.zhihu.com/people/zhang-san-ding)：

有些模板喜欢用CDN加速css结果国内墙了海外的CDN，没办法加载结果就丢失样式了。

### [用户代理样式表](https://blog.csdn.net/qq_45890970/article/details/123319868)

只要一刷新页面就会向下“掉”，打开网页开发人员工具查看盒子模型，才发现多了一个叫做用户代理样式表的东西，添加一个`margin:8px`。

用户代理样式表是浏览器（例如，Chrome，Firefox，Edge 等）提供的“默认样式表”，用于以满足“一般显示期望”的方式显示页面。

有些同学存在用户代理样式表的问题是因为没加`<!DOCTYPE html>`，然而代码本身就有`<!DOCTYPE html>`，所以最终使用`!important`解决了这个问题！！！

```
body{
   margin: 0 !important;
 }
```

