	css笔记

[toc]



### 1.CSS简介

CSS是用来修饰网页样式的语法，又叫做重叠样式表，它可以美化我们的页面元素
	



---



### 2.样式表的建立

#### 1.内联样式表

在一个标签内部的样式表

```html
<p style="color: #D1D3D6;">hello</p>
```



#### 2.内部样式表

在一个页面内的样式表

```html
<style type="text/css">
    p{
        color:red;
    }
</style>
```



#### 3.外部样式表

```html
<link rel="stylesheet" type="text/css" href="../015练习/001.css"/>
```

使用link元素导入外部样式表时，需要写在head标签之间

参数介绍

| 参数                      | 描述                                          |
| ------------------------- | --------------------------------------------- |
| rel="stylesheet"          | 用于定义文档关联，表示关联样式表              |
| type="text/css"           | 定义文档的类型                                |
| href="../015练习/001.css" | 为css文件的路径，可以是绝对路径或者是相对路径 |

​			

#### 4.导入样式

使用 @import 可以在原样式规则中导入其他样式表，可以在外部样式、style标签中使用。
导入样式要放在样式规则前面定义

```css
@import url(../css/002.css);
```

​	

---



### 3.选择器

	3.CSS常用选择符
		1.元素选择符
			1.示例
				div{
					color:blue;
				}
			2.用法
				使用标签名作为选择器(p,div,span,body,img...)
			
		2.ID选择符
			1.示例		
				#navigate {
					color:red;
				}
				<div id="navigate" >
			2.用法
				使用#+id来说明内部样式
				id表示身份，不能重复，只能选择单个元素
				
		3.类（别）选择符
			1.示例
				.nav {
					color：red;
				}
				<a href="#" class="nav">关于主页</a>
			2.用法	
				使用.+class来说明内部样式
				
		4.通用选择符
			1.示例
				*{
					color：bule;
				}
			2.用法
				对所有通用
			
		5.属性选择器
			1.说明
				根据属性来为元素设置样式也是常用的场景。
	
			2.示例
				[attribute]		[target]		选择带有 target 属性所有元素
				[attribute=value]  [target=_blank]	  -选择 title 属性包含单词 "flower" 的所有元素
				[attribute~=value] -[title~=flower]	   -选择 title 属性包含单词 "flower" 的所有元素
				[attribute|=value] -[lang|=en]		 选择 lang 属性值以 "en" 开头的所有元素。
				[attribute*=value] -a[src*="abc"]	  -选择其 src 属性中包含 "abc" 子串的每个 元素
				[attribute^=value] -a[src^="https"]	   -选择其 src 属性值以 "https" 开头的每个 元素
				[attribute$=value] -a[src$=".pdf"]	   选择其 src 属性以 ".pdf" 结尾的所有 元素
		
		6.伪类选择器
			1.说明
				为元素的不同状态或不确定存在的元素设置样式规则。
	
			2.示例
				状态	 	示例	 			说明
				:link	 		a:link			 选择所有未被访问的链接
				:visited	 	 -a:visited			-选择所有已被访问的链接
				:hover	    	-a:hover		  -鼠标移动到元素上时
				:active		 	 a:active		   点击正在发生时
				:focus			-input::focus		 选择获得焦点的 input 元素
				:root			:root			-选择文档的根元素即html
				:empty			-p:empty		  -选择没有子元素的每个元素（包括文本节点）
				:first-child   	   -p:first-child		-选择属于父元素的第一个子元素的每个元素
				:last-child	   	   p:last-child		   选择属于其父元素最后一个子元素每个元素
				:first-of-type		-p:first-of-type	  -选择属于其父元素的首个元素的每个元素
				:last-of-type		p:last-of-type		 选择属于其父元素的最后元素的每个元素
				:only-of-type		p:only-of-type		 选择属于其父元素唯一的元素的每个元素
				:only-child	   	   p:only-child		   选择属于其父元素的唯一子元素的每个元素
				:nth-child(n)		p:nth-child(2)		 选择属于其父元素的第二个子元素的每个元素
				:nth-child(odd)	 	 p:nth-child(odd)	   选择属于其父元素的奇数元素
				:nth-child(even) 	 -p:nth-child(even)		-选择属于其父元素的偶数元素
				:nth-of-type(n)	 	 p:nth-of-type(2)	   选择属于其父元素第二个元素的每个元素
				:nth-last-child(n)	  -p:nth-last-child(2)	  -同上，从最后一个子元素开始计数。
				:nth-last-of-type(n)   -p:nth-last-of-type(2)	-同上，但是从最后一个子元素开始计数。
				:not(selector)		-:not(p)		  -选择非元素的每个元素
	
		5.群组选择器
			1.示例
			
			2.用法


​	





-------------------------------------------------------------------------------



### 4.元素权重	

	4.CSS样式表的优先级
	<style type="text/css">
		#p1{
			color: blue;
		}
		.pp{
			color: orange;
		}
		*{
			color: green;
		}
		p{
			color: red;
		}
	</style>
	<p class="pp" id="p1" style="color: slateblue;">猜猜我什么颜色</p>
	
	1.优先级
		1.行内样式 > ID选择器 > 类选择器 > 标签选择器 > 通用选择器
		2.内部样式表和外部样式表的优先级和书写的顺序有关，靠后的优先级别高
	
	2.权重值
		1.通用选择器*
			权重值 0
		2.标签选择器 div, p...
			权重值 1
		3.类（别）选择器 .act, .nav...
			权重值 10
		4.ID选择器 #btn, #box...
			权重值 100
		5.行内样式
			权重值 1000
		6.继承
			没有权重，比通配符还低
	
	3.示例
		#box p .tt	权重：100+1+10 = 111
		#box .tt  	权重：100+10 = 110
		选择器选择的范围越小越精确，优先级越高
		有时在规则冲突时，为了让某个规则强制有效可以使用 !important





-------------------------------------------------------------------------------


3.span标签
	1.用法
		span，一个容器标签，不具备任何特殊功能，仅当作容器来使用。
		用于包裹一段文字，便于给文本添加样式

	2.示例
		<span style="background-color: gray;color: white;font-size: 24px;">白岩松</span>
		1.background-color: gray	容器背景颜色
		2.color: white				字体颜色
		3.font-size: 24px			字体大小





-------------------------------------------------------------------------------
4.div标签
	1.用法
		一个通用容器标签，不具备任何特殊功能，仅当作容器来使用。
		可以包裹任何内容，也可以容器直接互相包裹
		

	2.示例
		<div style="color: #555; margin: auto;">标签</div>
		1.margin:auto		容器居中对齐  
		2.width = 500px;	设置容器宽度
	
	3.特点
		一个空div，默认宽度为100%，高度为0
	
	4.line-height: 80px;
		设置行高
		字体默认16px
		行高默认21px





-------------------------------------------------------------------------------


### 5.文本类属性

#### 1.字体设置

使用 `font-family` 设置多个字体，由前到后的顺序使用，中文字体比较大不建议使用

```css
article{  
    font-family: "华文中宋", 'Courier New', Courier, monospace;
}
```



#### 2.字重定义

使用 `font-weight` 对字体的粗细进行调整。

```css
article{
    font-weight: bold;
}
```

属性列表

| 属性名称 |               |
| -------- | ------------- |
| normal   | 正常，对应400 |
| bold     | 粗体，对应700 |
| bolder   | 更粗          |
| lighter  | 跟明亮        |
| 100~900  | 字重数字取值  |



#### 3.字体大小

使用 `font-size` 设置字体大小

```css
article{
    font-size: 60px;
}
```

##### 字体大小的单位

| 单位  | 含义                             |
| ----- | -------------------------------- |
| 100%  | 百分数是子元素相对于父元素的大小 |
| 1em   | em单位等同于百分数单位           |
| 100px | 像素大小                         |

##### 控制字符

也可以使用控制字符

```css
article{
    font-size: small;
}
```

| 控制字符 |
| -------- |
| xx-small |
| x-small  |
| small    |
| meidum   |
| large    |
| x-large  |
| xx-large |



#### 4.文字颜色

##### 字符串颜色

使用定义好的字符颜色，比如 red，blue等等

```css
article{
     color: red;
}
```

##### 十六进制颜色

```css
color: #dddddd;
```

\#dddddd 可以简写成 \#ddd

##### RGB颜色

```css
color: rgb(100, 100, 100);
```

##### 透明颜色

透明色从 `0~1` 间，表示透明到不透明

```css
color: rgba(100, 100, 100, 0.5);
```



#### 5.行高定义

使用 `line-height` 定义行高

```css
 article {
     line-height: 1.5em;
}
```

单位列表

| 单位  | 描述                  |
| ----- | --------------------- |
| 20px  | 20px行高              |
| 1.5em | 1.5倍行高（建议使用） |



#### 6.字体倾斜

使用 `font-style` 控制字体的样式

```css
article {
    font-style: italic;
}
```

| 属性   | 描述               |
| ------ | ------------------ |
| normal | 正常，用于去除倾斜 |
| italic | 倾斜               |



#### 7.字体组合定义

可以使用 `font` 一次将字符样式定义，但要注意必须存在以下几点：

- 必须有字体规则
- 必须有字符大小规则

```css
article{
    font: bold initial 60px/1.5em 'Courier New', Courier, monospace;
}
```



#### 8.大小写转换

使用 `font-variant` 可以设置小型大写，字母全变为大写，但是字体大小不会变大

```css
article {
     font-variant: small-caps;
}
```

使用 `text-transform` 可以设置字母的大小写

```css
article {         
    text-transform: uppercase;
}
```

属性列表

| 属性       | 描述                          |
| ---------- | ----------------------------- |
| uppercase  | 全大写                        |
| lowercase  | 全小写                        |
| capitalize | 首字母大写 (句号，逗号，空格) |



#### 9.文本线条

使用 `text-decoration` 控制文本线条

```css
a{
	text-decoration: none;
}
```

属性列表

| 属性        | 描述   |
| ----------- | ------ |
| none        | 无线条 |
| underline   | 下划线 |
| ine-through | 删除线 |
| overline    | 上划线 |

​	

#### 10.文本阴影

使用 `text-shadow` 设置文本阴影

```css
article {
    font-size: 24px;
    text-shadow: rgba(100, 100, 100, 0.8) 5px 5px 5px;
}
```

参数顺序为：颜色，水平偏移，垂直偏移，模糊度



#### 11.空白处理

使用 `white-space` 控制文本空白显示。

```css
h1{
    white-space: pre;
}
```

属性列表

| 选项     | 说明                                    |
| -------- | --------------------------------------- |
| pre      | 保留文本中的所有空白，类似使用 pre 标签 |
| nowrap   | 禁止文本换行                            |
| pre-wrap | 保留空白，保留换行符                    |
| pre-line | 空白合并，保留换行符                    |



#### 12.文本溢出

##### 换行处理

使文本溢出后换行处理

```css
article {
    border: solid 1px rebeccapurple;
    overflow-wrap: break-word;
    width: 100px;
}
```

##### 溢出省略

溢出添加  `...` ，需要将overflow 设置在 text-overflow 前面。

```css
 article {
     border: solid 1px rebeccapurple;
     width: 100px;
     white-space: nowrap;
     overflow: hidden;
     text-overflow: ellipsis;
}
```



#### 13.文本缩进

使用 `text-indent` 控制文本缩进

```css
p {
    text-indent: 2em;
}
```

单位可用 px ，但 em 更好用

​	

#### 14.文本对齐

##### 水平对齐

使用 `text-align` 控制文本水平对齐

```css
article {
    border: solid 1px rebeccapurple;
    text-align: center;
}
```

属性列表

| 属性   | 描述           |
| ------ | -------------- |
| left   | 左对齐（默认） |
| right  | 右对齐         |
| center | 居中对齐       |



##### 垂直对齐

使用 `vertical-align` 控制文本垂直对齐

```css
article {
    border: solid 1px rebeccapurple;
    vertical-align: middle;
}
```

属性列表

| 属性   | 描述     |
| ------ | -------- |
| top    | 顶部对齐 |
| middle | 居中对齐 |
| bottom | 底部对齐 |



#### 15.排版模式

##### 单词间距

用空格，逗号，句号隔开的算一个单词，使用 `word-spacing` 控制单词间距

```css
p{
    word-spacing: 20px;
}
```



##### 字符间距

使用 `letter-spacing` 控制每个字符之间的间隔

```css
p{
    letter-spacing: 20px;
}
```



##### 排版方向

使用 `writing-mode` 控制排版方向

```css
p{
    writing-mode: vertical-rl;
}
```

属性列表

| 属性          | 描述                                     |
| ------------- | ---------------------------------------- |
| horizontal-tb | 水平方向自上而下的书写方式               |
| vertical-rl   | 垂直方向自右而左的书写方式               |
| vertical-lr   | 垂直方向内内容从上到下，水平方向从左到右 |





-------------------------------------------------------------------------------



### 6.盒子模型

![](http://houdunren.gitee.io/note/assets/img/image-20190817163854641.0f6c1947.png)



#### 1.元素边框

使用 `border` 设置边框的宽度，样式，颜色，只有颜色可以省略，默认黑色

```css
border: 2px, solid, #ddd;
```



##### 边框样式

| 属性   | 描述           |
| ------ | -------------- |
| none   | 无边框         |
| solid  | 实线           |
| dashed | 虚线           |
| dotted | 点线           |
| double | 3D 凹槽边框    |
| double | 双线           |
| groove | 3D 凹槽边框    |
| ridge  | 3D 垄状边框    |
| inset  | 3D inset 边框  |
| outset | 3D outset 边框 |



##### 单独定义

可以单独定义每个边框的样式

```css
div {
     border-top: ridge 10px #aaaaaa;
}
```



##### 行元素边框

行元素也是可以设置边框的

```css
p {
	border-bottom: solid 2px red;
}
```



##### 边框圆角

使用  `border-radius`  规则设置圆角，可以使用`px | %` 等单位。也支持四个边分别设置。

```css
h2 {
	border-radius: 10px;
	border: solid 2px red;
}
```

支持单独控制

| 选项                       | 说明 |
| -------------------------- | ---- |
| border-top-left-radius     | 上左 |
| border-top-right-radius    | 上右 |
| border-bottom-left-radius  | 下载 |
| border-bottom-right-radius | 下右 |



#### 2.外边距

使用 `margin` 设置边框大小

边距顺序依次为：上、右、下、左

![](http://houdunren.gitee.io/note/assets/img/image-20190817185522220.41d1113e.png)

```css
p{
  	margin-top: 20px;
    margin-bottom: 20px;
    margin-left: 20px;
    margin-right: 20px; 
}
p{
    margin: 10px 15px 10px 15px 上，右，下，左一个都不可省略
    margin: 10px 15px 10px		表示上，右下，左
    margin: 10px 15px			表示上右，下左
    margin: 10px 				表示上下左右
}
```



##### 负值设置

设置负值就会向反方向作用

```css
p{
    margin: -10px -15px;
}
```



##### 边距合并

相邻元素的外边距会进行合并，取值为最大值



#### 3.内边距

使用 `padding` 设置内边距

```css
p{
  	padding: 10px 10px 20px 20px;
}
```



#### box-sizing

使用 `box-sizing` 使元素的尺寸包括内边距和边框的大小

```css
p{
  	padding: 10px 10px 20px 20px;
    box-sizing: border-box;
}
```



#### 4.轮廓线

轮廓线是边框外的线，不占用空间，使用 `outline` 设置，不影响页面布局

```css
 div {
     border: solid 2px #aaaaaa;
     box-sizing: border-box;
     outline: solid 3px #675756;
}
```

设置属性操作和样式等，和边框一样



##### 表单轮廓线

表单默认具有轮廓线，但有时并不好看，使用以下样式规则去除

```css
input:focus {
	outline: none;
}
```



#### 5.display

##### 控制显示隐藏

使用 `display` 控制元素的显示机制。

属性列表

| 属性         | 描述                        |
| ------------ | --------------------------- |
| none         | 隐藏元素                    |
| block        | 显示为块元素                |
| inline       | 显示为行元素，不能设置宽/高 |
| inline-block | 行级块元素，允许设置宽/高f  |



##### 行转块元素

行元素属于文本元素，不会独占一行，而块元素可以独占一行

```css
a {
  border: solid 1px #ddd;
  display: block;
  margin-bottom: 5px;
}
...

<a href="">houdunren.com</a>
<a href="">houdunren.com</a>
<a href="">houdunren.com</a>
```



##### 块转为行元素

```css
ul>li {
  display: inline;
  padding: 5px 10px;
  border: solid 1px #ddd;
}

ul>li:hover {
  background: green;
  color: white;
  cursor: pointer;
}
...

<ul>
<li>hdcms.com</li>
<li>houdunren.com</li>
<li>后盾人</li>
</ul>
```



##### 行级块使用

```css
a {
  display: inline-block;
  width: 30%;
  height: 50px;
  border: solid 1px #ddd;
  text-align: center;
  line-height: 3em;
}
...

<a href="">MYSQL</a>
<a href="">LINUX</a>
<a href="">PHP</a>
```



##### 隐藏元素visibility

前面说了可以用 `display: none` 隐藏元素，但是隐藏元素之后，元素的位置就空出来了，后面的元素会补上，有时候不是我们想要的。我们可以使用 `visibility: hidden` 是元素隐藏，而不会空出位置。也可以使用 `opacity: 0` 把元素的透明度设置为0

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        article {
            border: solid 2px #dddddd;
            width: 400px;
            padding: 20px;
            height: 400px;
        }

        div {

            background-color: aqua;
            width: 100px;
            height: 100px;
            margin-bottom: 10px;
        }

        div:nth-child(1) {
            visibility: hidden;
        }
    </style>
</head>

<body>
    <article>
        <div></div>
        <div></div>
    </article>
</body>

</html>
```



#### 6.内容溢出

可以使用 `overflow` 控制溢出的处理 

| 选项   | 说明                                                 |
| ------ | ---------------------------------------------------- |
| hidden | 溢出内容隐藏                                         |
| scroll | 显示滚动条（有些浏览器会一直显示，有些在滚动时显示） |
| auto   | 根据内容自动处理滚动条                               |

 

##### 溢出隐藏

```css
div {
  width: 400px;
  height: 100px;
  border: solid 2px #ddd;
  padding: 20px;
  overflow: hidden;
}
```



**溢出产生滚动条**

```css
div {
  width: 400px;
  height: 100px;
  border: solid 2px #ddd;
  padding: 20px;
  overflow: scroll;
}
```



#### 7.尺寸控制

可以使用多种方式为元素设置宽、高尺寸。

| 选项           | 说明             |
| -------------- | ---------------- |
| width          | 宽度             |
| height         | 高度             |
| min-width      | 最小宽度         |
| min-height     | 最小高度         |
| max-width      | 最大宽度         |
| max-height     | 最大高度         |
| fill-available | 撑满可用的空间   |
| fit-content    | 根据内容适应尺寸 |



##### min&max

正文中不希望图片太大造成溢出窗口，也不希望太小影响美观，使用以下代码可以做到约束。

max表示最大的尺寸，min为最小的尺寸，图片会自动被缩放到这个范围内

```css
<style>
	div {
    width: 600px;
    border: solid 2px #ddd;
    padding: 20px;
  }
  div img {
    min-width: 50%;
    max-width: 90%;
  }
</style>
```



##### fill-available

使元素撑满可用的空间，在`chrome` 浏览器中使用前缀 `-webkit` 书写样式

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        * {
            padding: 0;
            margin: 0;
        }

        body {
            width: 100vw;
            height: 100vh;
            background: #2c3e50;
        }

        main {
            background: #9b59b6;
            height: 100px;
            padding: 20px;
            box-sizing: border-box;
        }

        span {
            background: #e67e22;
            display: inline-block;
            width: -webkit-fill-available;
            height: -webkit-fill-available;
        }
    </style>
</head>

<body>
    <main>
        <span>
            houdunren.com
        </span>
    </main>
</body> 
```



##### fit-content

下面是根据内容自动适应宽度，让元素居中显示的效果。

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        * {
            padding: 0;
            margin: 0;
        }

        body {
            width: 100vw;
            height: 100vh;
            background: #2c3e50;
        }

        h2 {
            text-align: center;
            background: #f1c40f;
            width: fit-content;
            margin: auto;
        }
    </style>
</head>

<body>
    <h2>houdunren.com</h2>
</body>
```



##### min-content & max-content

使用`min-content` 将容器尺寸按最小元素宽度设置使用

使用`max-content`容器尺寸按子元素最大宽度设置

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        * {
            padding: 0;
            margin: 0;
        }

        body {
            width: 100vw;
            height: 100vh;
            background: #2c3e50;
        }

        main {
            width: min-content;
            margin: auto;
        }

        div {
            margin-bottom: 20px;
            background: #f1c40f;
            word-break: break-all;
            padding: 10px;
        }

        div:nth-child(1) {
            width: 100px;
        }
    </style>
</head>

<body>
    <main>
        <div>houdunren.com</div>
        <div>hdcms.com</div>
    </main>
</body>
```





---



### 7.背景与渐变

	1.背景颜色
	
		1. 背景颜色可以使用 rga | rgba | 十六进制 等颜色格式
		2. background-color: blueviolet;
	
	2.背景图片
		1. 可以使用 png| gif |jpeg 等图片做为背景使用
		2. background-image: url(../img/css_background.webp);
	
	3.背景裁切
		1.说明
			使用 background-clip 可以控制背景的填充位置
		
		2.属性列表
			border-box		包括边框
			padding-box		-不含边框，包括内边距
			content-box		-内容区域
	
	4.背景重复
		1.说明
			使用 background-repeat 设置背景重复的规则
		
		2.属性列表
			1. repeat		水平、垂直重复
			2. repeat-x		 水平重复
			3. repeat-y		 垂直重复
			4. no-repeat	 -不重复
			5. space	   -背景图片对称均匀分布
	
	5.背景滚动
		1.说明
			使用 background-attachment 设置在页面滚动时的图片处理方式
			
		2.属性列表
			1. scroll	-背景滚动
			2. fixed	背景固定		
	
	6.背景位置
		1.说明
			使用 background-position 用于设置背景图片的水平、垂直定位
		
		2.属性列表
			left		左对齐
			right		-右对齐
			center	     居中对齐
			top		   -顶端对齐
			bottom		 底部对齐
			5px 5px		 水平、垂直设置
			50% 50%		 水平、垂直设置
	
	7.背景尺寸
		1.说明
			使用 background-size 调整背景尺寸
	
		2.属性列表
			cover		背景完全覆盖，可能会有背景溢出
			contain		 图片不溢出的放在容器中，可能会漏出部分区域
			100px auto	  调整宽高
			100px 100px	  -调整宽高
	
	8.多个背景
		1.后定义的背景置于底层
			background-image: url(xj-small.png), url(bg.png);
	
		2.多属性定义
			background-image: url(xj-small.png), url(bg.png);
			background-repeat: no-repeat;
			background-position: top left, right bottom;
	
		3.可以一次定义多个背景图片
			background: url(xj-small.png) left 50% no-repeat,
	            url(bg.png) right 100% no-repeat red;
	
	9.组合设置
		1. 可以使用一条指令设置背景
		2. background: red url(xj-small.png) no-repeat right 50% fixed;


	10.盒子阴影
		1.说明
			可以使用 box-shadow 对盒子元素设置阴影，参数为 水平偏移,垂直偏移,模糊度,颜色 构成
		
		2.示例
			box-shadow: 10px 10px 10px rgba(100, 100, 100, .5);
	
	11.颜色渐变
		1.线性渐变
			向下渐变	background: linear-gradient(green,blue);
			渐变角度	background: linear-gradient(30deg, red, green);
			向右渐变	background: linear-gradient(to right, red, green)
			向左渐变	background: linear-gradient(to left, red, green);
			左上渐变	background: linear-gradient(to top left, red, green);
			右下渐变	background: linear-gradient(to right bottom, red, green);
			多个颜色	background: linear-gradient(red, rgb(0, 0, 200), green, rgba(122, 211, 100, 0));
		
		2.径向渐变
			设置渐变		background: radial-gradient(red, blue, green);
			设置渐变宽度与高度	 background: radial-gradient(100px 200px, red, blue, green);
			左下渐变		background: radial-gradient(at bottom left, red, blue);
			右下渐变		background: radial-gradient(at bottom right, red, blue);
			左侧向中心渐变	   background: radial-gradient(at center left, red, blue);
			底部向中心渐变	   background: radial-gradient(at 50% 100%, red, blue);
	
	12.标识位
		1.说明
			颜色未指定标识时，颜色会平均分布。
	
		2. background: linear-gradient(45deg,red 50%, blue 50%);
	
	13中间点
		设置渐变中心点的位置
		background: linear-gradient(45deg, red, 50%, blue);
	
	14.进度条绘制
		background: repeating-linear-gradient(90deg,red ,25px,yellow 25px,25px,blue 50px);
7.背景图片的使用
	1.html ,body{
		height: 100%;
		margin: 0;
	}
		body默认宽为100%，高为一个单位
		html和body同时设置height：100%才能使body高为100%
		margin:0;表示略去下拉条，消除边距
		

	2.background-image: url(../img/1001294.jpg);
		插入背景图片，默认无限平铺
		background-repeat: no-repeat;表示不重复
	
	3.图片位置
		background-position: right bottom;
		第一个参数：水平位置
		第二个参数：垂直位置
		
	4.background：
		可以完成关于背景的所有内容



6.常见图片类型
	1.jpg
		采用有损压缩算法
		体积较小
		不支持透明
		不支持动画
		

	2.gif
		支持动画
		只有全透明和不透明两种模式
		只有256种颜色
	
	3.png
		采用无损压缩算法0
		体积也相对较小
		支持背景透明
		不支持动画
	
	4.svg
		不会失真
		只能保存颜色和形状相对简单的图片



---



### 8.数据样式

15.数据样式
	1.定制表格
		1.说明
			除了使用 table 标签绘制表格外，也可以使用 display 样式绘制。		

		2.属性
			table			对应 table
			table-caption		对应 caption
			table-row		  对表 tr
			table-row-group		 对应 tbody
			table-header-group	  -对应 thead
			table-footer-group	  -对应 tfoot
	
	2.列表
		1.列表符号
			1.说明
				使用 list-style-type 来设置列表样式，规则是继承的，所以在ul 标签上设置即可。
	
			2.属性列表
				none				无标记。
				disc				默认。标记是实心圆。
				circle				 标记是空心圆。
				square				 标记是实心方块。
				decimal				 -标记是数字。
				decimal-leading-zero		0开头的数字标记。(01, 02, 03, 等。)
				lower-roman			   -小写罗马数字(i, ii, iii, iv, v, 等。)
				upper-roman			   -大写罗马数字(I, II, III, IV, V, 等。)
				lower-alpha			   -小写英文字母The marker is lower-alpha (a, b, c, d, e, 等。)
				upper-alpha			   -大写英文字母The marker is upper-alpha (A, B, C, D, E, 等。)
				lower-greek			   -小写希腊字母(alpha, beta, gamma, 等。)
				lower-latin			   -小写拉丁字母(a, b, c, d, e, 等。)
				upper-latin			   -大写拉丁字母(A, B, C, D, E, 等。)
				hebrew			     传统的希伯来编号方式
				armenian			  传统的亚美尼亚编号方式
				georgian			  传统的乔治亚编号方式(an, ban, gan, 等。)
				cjk-ideographic			 -简单的表意数字
				hiragana			  标记是：a, i, u, e, o, ka, ki, 等。（日文片假名）
				katakana			  标记是：A, I, U, E, O, KA, KI, 等。（日文片假名）
				hiragana-iroha			 标记是：i, ro, ha, ni, ho, he, to, 等。（日文片假名）
				katakana-iroha			 标记是：I, RO, HA, NI, HO, HE, TO, 等。（日文片假名）





---



### 9.浮动

8.元素浮动
	浮动元素会脱离网页文档，与其他元素发生重叠，但不会与文字内容发生重叠
	1.示例
		float: right ;
		right:向右浮动
		left:向左浮动
	

	2.父元素
		.outer{
			height: 200px;
		}
		<div class="outer">
			<div id="a"></div>
			<div id="b"></div>
			<div id="c"></div>
		</div>
		父元素可以清除浮动元素对于后面元素的影响
		
		1.overflow: auto;
			对于超出边界的元素，父元素做出自动的调整
			
		2.clear:left/right/both
			清除浮动元素对当前元素的影响
	
	3.浮动注意事项
		1.浮动元素在排列时，只参考前一个元素位置即可
			一行排不下时，下一行的元素会以前一个元素作为参考排列
		2.浮动元素重叠问题
			1.浮动元素不会覆盖文字内容
			2.浮动元素不会覆盖图片内容，图片可以看作一个特殊文字
			3.浮动元素不会覆盖表单元素（复选框等）



---



### 10.定位布局

17.定位布局
	1.定位类型
		1.说明
			使用 position 属性设置定位类型
		

属性列表

| 参数     | 作用                 |
| -------- | -------------------- |
| static   | 默认形为，参考文档流 |
| relative | 相对定位             |
| absolute | 绝对定位             |
| fixed    | 固定定位             |
| sticky   | 粘性定位             |




	2.位置偏移
		1.说明
			可以为部分类型的定位元素设置上、下、左、右 的位置偏移。


		2.属性列表
			top			距离顶边
			bottom		 -距离下边
			left		-距离左部
			right		 距离右边
	
	2.相对定位
		相对定位是相对于元素原来的位置控制，当元素发生位置偏移时，原位置留白。
	
	3.绝对定位
		1. 绝对定位不受文档流影响，就像漂浮在页面中的精灵，绝对定位元素拥有行内块特性
		2. 原来的位置丢失，以页面为基准调整
		3. 如果父元素有定位(任意定位)，则以父元素为基准
		4. 如果元素没有设置尺寸，可以通过定位的偏移值设置元素的尺寸
		5. 如果设置了定位而没有设置位置偏移量, 则位置没有发生改变
	
	4.居中定位
		通过将 left 设置为50% ,并向左偏移子元素宽度一半可以实现水平居中，垂直居中使用方式类似
		
	5.滚动行为
		固定定位元素会随滚动条发生滚动。
	
	6.纵向重叠
		1.说明
			如果元素重叠在一起，可以使用 z-index 控制元素的上下层级，数值越大越在上面。
			父级子元素设置 z-index 没有意义，子元素永远在父元素上面的
	
		2.示例
			z-index = -1; (正数和负数都可以)
	
	7.粘性定位
		1.说明
			吸住元素的特性
	
		2.示例
			article section h2{
				background: burlywood;
				color: white;
				position: sticky;
				top: 10px;
	   	 	}
	
		3.注意事项
			1.同级定位
				会产生叠加效果
	
			2.非同级定位
				会把上一个元素顶走
	
	8.固定定位
		1.说明
			使用 position: fixed; 设置固定定位
			不受父元素的影响, 以页面为标准, 做位置偏移
			不受其他元素影响, 固定在页面的某个位置





---



### 11.弹性布局

Flex 是 Flexible Box 的缩写，意为"弹性布局"，可以轻松的控制元素排列、对齐和顺序的控制。

现在的终端类型非常多，使用弹性盒模型可以让元素在不同尺寸终端控制尺寸。



#### 声明定义

容器盒子里面包含着容器元素，使用 `display:flex` 或 `display:inline-flex` 声明为弹性盒子

flex 为块级的弹性盒子，inline-flex 为行级的弹性盒子

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <style>
        * {
            padding: 0;
            margin: 0;
        }

        body {
            padding-left: 100px;
            padding-top: 100px;
        }

        footer {
            border: solid 2px blueviolet;
            width: 400px;
            display: flex;
        }

        footer div {
            width: 100px;
            height: 100px;
            background-color: bisque;
            margin: 10px;
            font-size: 25px;
        }
    </style>

</head>

<body>
    <footer>
        <div>睡懒觉</div>
        <div>程序员</div>
        <div>小知识</div>
    </footer>
</body>

</html>
```



#### flex-direction

用于控制盒子元素排列的方向

| 值             | 描述                           |
| :------------- | :----------------------------- |
| row            | 从左到右水平排列元素（默认值） |
| row-reverse    | 从右向左排列元素               |
| column         | 从上到下垂直排列元素           |
| column-reverse | 从下到上垂直排列元素           |



```css
footer {
    border: solid 2px blueviolet;
    width: 400px;
    display: flex;
    flex-direction: row-reverse;
}
```



#### flex-wrap

flex-wrap 属性规定flex容器是单行或者多行，同时横轴的方向决定了新行堆叠的方向。

装不下的时候选择的处理方式

| 选项         | 说明                                             |
| :----------- | :----------------------------------------------- |
| nowrap       | 元素不拆行或不拆列（默认值）                     |
| wrap         | 容器元素在必要的时候拆行或拆列。                 |
| wrap-reverse | 容器元素在必要的时候拆行或拆列，但是以相反的顺序 |



```css
footer {
    border: solid 2px blueviolet;
    width: 400px;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
}
```



#### flex-flow

`flex-flow` 是 `flex-direction` 与 `flex-wrap` 的组合简写模式。

下面是从右向左排列，换行向上拆分行。

![](data:image/png;base64,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)

```text
flex-flow: row-reverse wrap-reverse;
```



#### 轴说明

##### 水平排列

下面是使用 `flex-flow: row wrap` 的主轴与交叉轴说明。

![image-20190825175808514](http://houdunren.gitee.io/note/assets/img/image-20190825175808514.241ce400.png)

下面是使用 `flex-flow: row-reverse wrap-reverse` 的主轴与交叉轴说明。

![image-20190825180523789](http://houdunren.gitee.io/note/assets/img/image-20190825180523789.c688ac2e.png)

##### 垂直排列

下面是使用 `flex-flow: column wrap` 的主轴与交叉轴说明。

![image-20190825181547815](http://houdunren.gitee.io/note/assets/img/image-20190825181547815.ddd72467.png)

##### justify-content

用于控制元素在主轴上的排列方式，再次强调是主轴的排列方式。

| 选项          | 说明                                                         |
| :------------ | :----------------------------------------------------------- |
| flex-start    | 元素紧靠主轴起点                                             |
| flex-end      | 元素紧靠主轴终点                                             |
| center        | 元素从弹性容器中心开始                                       |
| space-between | 第一个元素靠起点，最后一个元素靠终点，余下元素平均分配空间   |
| space-around  | 每个元素两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍 |
| space-evenly  | 元素间距离平均分配                                           |

水平排列元素，并使用 `justify-content: flex-end` 对齐到主轴终点

![image-20190825185352912](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlEAAACFCAYAAAB7TK3OAAABRmlDQ1BJQ0MgUHJvZmlsZQAAKJFjYGASSSwoyGFhYGDIzSspCnJ3UoiIjFJgf8zAwSDJwMfAxSCTmFxc4BgQ4ANUwgCjUcG3awyMIPqyLsisVrZM4er5jJxT0jeu+3mzzx9TPQrgSkktTgbSf4A4PbmgqISBgTEFyFYuLykAsTuAbJEioKOA7DkgdjqEvQHEToKwj4DVhAQ5A9k3gGyB5IxEoBmML4BsnSQk8XQkNtReEOD1cVcI9QkJcgz3dHEl4F6SQUlqRQmIds4vqCzKTM8oUXAEhlKqgmdesp6OgpGBoSUDAyjMIao/3wCHJaMYB0KsQIyBwWIGUPAhQiwe6IftcgwM/H0IMTWgfwW8GBgO7itILEqEO4DxG0txmrERhM29nYGBddr//5/DGRjYNRkY/l7////39v///y5jYGC+xcBw4BsAvTZgQZTtpjMAAA4ISURBVHgB7d1JiBzVHwfwl7/jgtvBFTFEI2gMGuO+L6CIF4+CiAsqghG9JOQgisaIKBIhiAdRQRTReHCNBxkP4ilxJwaCmShiiCKuuKKCcf6+ki6jmar01HRNv1f9KYjTqa1/7/MrnG+qqqvnTP41BRMBAgQIECBAgMC0BP43rbWtTIAAAQIECBAgUAgIUQ4EAgQIECBAgEADASGqAZpNCBAgQIAAAQJClGOAAAECBAgQINBAQIhqgGYTAgQIECBAgMDYVATj4+NTzTaPAAECBAgQIDBSApdccknleJ2JqqSxgAABAgQIECBQLSBEVdtYQoAAAQIECBCoFBCiKmksIECAAAECBAhUCwhR1TaWECBAgAABAgQqBaa8sXyqteturJpqffMIECBAgAABAjkJTPeDdc5E5dRdtRIgQIAAAQLJCAhRybRCIQQIECBAgEBOAkJUTt1SKwECBAgQIJCMgBCVTCsUQoAAAQIECOQkIETl1C21EiBAgAABAskICFHJtEIhBAgQIECAQE4CQlRO3VIrAQIECBAgkIyAEJVMKxRCgAABAgQI5CQgROXULbUSIECAAAECyQgIUcm0QiEECBAgQIBATgJCVE7dUisBAgQIECCQjIAQlUwrFEKAAAECBAjkJCBE5dQttRIgQIAAAQLJCAhRybRCIQQIECBAgEBOAkJUTt1SKwECBAgQIJCMgBCVTCsUQoAAAQIECOQkIETl1C21EiBAgAABAskICFHJtEIhBAgQIECAQE4CQlRO3VIrAQIECBAgkIzAWDKVKITALAusWDgxy+/o7QYhsPLDBYPYTbkPx0FJkdULx0FW7Wqt2EEfB9Mt1Jmo6YpZnwABAgQIECDwl4AQ5TAgQIAAAQIECDQQEKIaoNmEAAECBAgQICBEOQYIECBAgAABAg0E3FjeAM0m3RUY9k2K3ZVtNrJh3fTtOGjWr7a2chy0JZvXfod1HNQpORNVp2MZAQIECBAgQKBCQIiqgDGbAAECBAgQIFAnIETV6VhGgAABAgQIEKgQEKIqYMwmQIAAAQIECNQJCFF1OpYRIECAAAECBCoEhKgKGLMJECBAgAABAnUCQlSdjmUECBAgQIAAgQoBIaoCxmwCBAgQIECAQJ2AEFWnYxkBAgQIECBAoEJAiKqAMZsAAQIECBAgUCcgRNXpWEaAAAECBAgQqBAQoipgzCZAgAABAgQI1AkIUXU6lhEgQIAAAQIEKgSEqAoYswkQIECAAAECdQJCVJ2OZQQIECBAgACBCgEhqgLGbAIECBAgQIBAnYAQVadjGQECBAgQIECgQkCIqoAxmwABAgQIECBQJzBWt9AyAgTyFPjiiy/Cxx9/HPbcc89w+umn5zkIVTcS2LRpU9i8eXPR/99++y0cdthh4cgjjwznn39+2GuvvRrt00Z5CUxOTob169cXx8DWrVtD/PshhxwS5s6dGy644IKw33775TWghKsVohJujtIINBHYsGFDWLFiRdi+fXvxS/O5555rshvbZCbw008/hQceeCC89957U1b+6KOPhptuuilcdNFFUy43sxsCW7ZsCatWrQrxH1JTTY899li4/PLLwxVXXBHmzJkz1SrmTUNAiJoGllUJpCzw559/hldeeSXE/0maRkvgxx9/DNdff32IZ57itMcee4T58+eHvffeO2zbti188803xbLVq1cXvzgvvPDC0QIakdHGs07Lli0rRxvPPB5xxBHFGenPPvssfPfdd8U/rp555pkQ/39x1VVXlet60UxAiGrmZisCyQjEMxBr164NL774YvlLNJniFDIrAvEsUy9AnXrqqeHWW2/916W7devWhfvvv7/4Bfrggw+GE044IRx00EGzUps3mR2B33//Pdxxxx3lm8UzTfGM09jYP7/m33zzzXDfffcVx8Gzzz5bXOKdN29euY0X0xdwY/n0zWxBICmB1157LaxZs6b8JRp/Qcb7YEyjIfDJJ5+EN954oxjswQcfXFzK/e+9T2effXa44YYbinXiZd633nprNHBGaJTvvvtucaYpDvniiy8OV1555b8CVJx/5plnFpd04+s4ffDBB3+/8N/GAkJUYzobEkhLYJ999glLliwJ9957b9h3333TKk41rQls3Lix3PeNN95YeZ9LvKG4N8X7ZkzdEoghqjddffXVvZc7/TznnHPKeRMTE+VrL5oJ/HOer9n2tiJAYMgCCxYsCLfddls466yzKn+BDrlEb9+iwKefflru/bjjjitf//fFjmen4r0xpm4JxMt28dN3Bx54YDjggAP6Glz89K5pZgJC1Mz8bE1g6ALHH3/80GtQwPAE4g3DcYo3k9d9dD0+8qI3HX300b2XfnZE4Oabb+5rJDteynUc9EVWu5IQVctjIQECBNIWiI816Gd6+umny9WOPfbY8rUXoyPwzjvvhIceeqgYcLz8f+65547O4FsaqRDVEqzdEiBAIBWB8fHx8ibiQw89NJxyyimplKaOFgVeffXVEO+V+uGHH8Lnn38e4id54xQD1F133eXeyQHYC1EDQLQLAgQIpCrwwgsvhMcff7ws7/bbbw+77bZb+XcvuisQP3Sw4+W73khvueWWsHDhwt5f/ZyBgBA1AzybEiBAIFWBX3/9tXg21I6f2lq6dGk46qijUi1ZXQMWiJ/IPPzww8PPP/8c4r1z8dsM4hSfGRYv7cXjwVPLZ4YuRM3Mz9YECBBITuCjjz4Kd955Z3n5Jt50Hr8KaPHixcnVqqD2BOJzoeKf3hQ/lXn33XcX36n3+uuvh2OOOSZceumlvcV+NhDwnKgGaDYhQIBAqgLxyfXxDEPv/pd4E3m8nCdApdqx2asrPvoghqje5dz41HLTzASciZqZn60JECCQhED8LrT4lR7r168v67n22mvDZZddVv7di24KfP311+Hll18uBnfGGWeERYsWVQ50//33DzFYb9q0KXz//ffhjz/+2OnJ5pUbW7CTgBC1E4kZBAgQyEtgcnKy+N603td4xE9f3XPPPcFzgPLqY9Nq44NUX3rppWLzL7/8sjZExZV233338q2EqJKi0QuX8xqx2YgAAQLpCDz//PPlIwziFws//PDDAlQ67Wm9kviQ1d4XSsdP5MVgVDXFZZs3by4Wx8t7Oz7Jvmob86sFhKhqG0sIECCQvMBXX30VnnrqqaLOeAP5qlWr+v7aj+QHp8C+BU466aRi3V9++SU88sgjlds98cQT5ZeVn3zyyZXrWdCfgMt5/TlZiwABAkkKrF27Nmzfvr2obf78+eH999/fZZ3xrIUHbu6SKasVrrvuurBu3boQQ1R8yOa3334brrnmmjBv3rwQ75fbunVr8QGD3iXfGLjjctPMBISomfnZmgABAkMV2LJlS/n+ExMTIf7Z1RTvlRKidqWU1/J4w/jKlSvD8uXLi8LffvvtEP9MNcVP58VHYPT7RcVT7cO8vwVcznMkEOiwQO+jzB0e4sgPbdu2bdM2iGchTN0TiJ+6i5fyTjvttMrBnXfeeeHJJ58MJ554YuU6FvQv4ExU/1bWJJCNwOrVq7OpVaEzE1izZs3MdmDrTgnEJ5THB6vGy3rx+/Lik8rjP6biZb25c+f+65N5nRr4kAYjRA0J3tsSIECAAIG2BOJjLuITyeMfU3sCLue1Z2vPBAgQIECAQIcFhKgON9fQCBAgQIAAgfYEhKj2bO2ZAAECBAgQ6LCAENXh5hoaAQIECBAg0J6AENWerT0TIECAAAECHRYQojrcXEMjQIAAAQIE2hMQotqztWcCBAgQIECgwwJCVIeba2gECBAgQIBAewJCVHu29kyAAAECBAh0WECI6nBzDY0AAQIECBBoT0CIas/WngkQIECAAIEOCwhRHW6uoREgQIAAAQLtCQhR7dnaMwECBAgQINBhASGqw801NAIECBAgQKA9ASGqPVt7JkCAAAECBDosIER1uLmGRoAAAQIECLQnIES1Z2vPBAgQIECAQIcFhKgON9fQCBAgQIAAgfYExtrbtT0TyE9gxcKJ/IpW8cAFHAcDJ81yh46DLNs2q0U7EzWr3N6MAAECBAgQ6IqAENWVThoHAQIECBAgMKsCQtSscnszAgQIECBAoCsCQlRXOmkcBAgQIECAwKwKuLF8Vrm9WUoCKz9ckFI5ahmSgONgSPCJva3jILGGZFKOM1GZNEqZBAgQIECAQFoCQlRa/VANAQIECBAgkImAEJVJo5RJgAABAgQIpCUgRKXVD9UQIECAAAECmQgIUZk0SpkECBAgQIBAWgJCVFr9UA0BAgQIECCQiYAQlUmjlEmAAAECBAikJSBEpdUP1RAgQIAAAQKZCAhRmTRKmQQIECBAgEBaAkJUWv1QDQECBAgQIJCJgBCVSaOUSYAAAQIECKQlIESl1Q/VECBAgAABApkICFGZNEqZBAgQIECAQFoCQlRa/VANAQIECBAgkImAEJVJo5RJgAABAgQIpCUgRKXVD9UQIECAAAECmQgIUZk0SpkECBAgQIBAWgJCVFr9UA0BAgQIECCQiYAQlUmjlEmAAAECBAikJTDWbznj4+P9rmo9AgQIECBAgEDnBZyJ6nyLDZAAAQIECBBoQ0CIakPVPgkQIECAAIHOCwhRnW+xARIgQIAAAQJtCAhRbajaJwECBAgQINB5gTmTf02dH6UBEiBAgAABAgQGLOBM1IBB7Y4AAQIECBAYDQEhajT6bJQECBAgQIDAgAWEqAGD2h0BAgQIECAwGgJC1Gj02SgJECBAgACBAQsIUQMGtTsCBAgQIEBgNASEqNHos1ESIECAAAECAxb4P7kbAgPtAhcCAAAAAElFTkSuQmCC)

















---



### 12.属性的简写

#### 1.background

```css
background: gray url(xxx/xx.png) no-repeat;
```

​	分别是：背景颜色，背景图片，平铺方式
​		

#### 2.border

```css
border: 1px solid #D3f402;
```

分别是：边框宽度，边框样式，边框颜色
只有颜色可以省略，默认黑色



#### 3.font

```css
font: italic bold 20px/35px arial,scans-serif,"微软雅黑";
```

分别是：斜体字，加粗，字号大小/行高 默认字体，备用字体，备用字体



#### 4.margin

```css
margin: 10px 15px 10px 15px 上，右，下，左一个都不可省略
margin: 10px 15px 10px		表示上，右下，左
margin: 10px 15px			表示上右，下左
margin: 10px 				表示上下左右
```



#### 5.padding

```css
padding：10px 15px 10px 15px	上，右，下，左一个都不可省略（同上）
```





-------------------------------------------------------------------------------



### 13.常用颜色

| 英文          | 中文       |
| ------------- | ---------- |
| rebeccapurple | 雷贝卡紫色 |
| royalblue     | 宝蓝色     |
| rosybrown     | 玫瑰棕色   |
| blueviolet    | 蓝紫色     |
| cadetblue     | 军蓝色     |
| wheat         | 小麦色     |

​	



-------------------------------------------------------------------------------



### 14.居中定位

##### 使用 margin-left 和 margin-top 控制

```css
main {
    position: absolute;
    left: 50%;
    top: 50%;
    margin-left: -250px;
    margin-top: -250px;
    width: 500px;
    height: 500px;
    border: solid 5px silver;
}
```



##### 使用移动居中

使用移动进行操作，不会因为尺寸的改变发生变化

```css
main {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);
    width: 500px;
    height: 500px;
    border: solid 5px silver;
}
```



##### 使用外边距居中

可以设置外边距为 auto 使父元素内的子元素居中对齐

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        article {
            border: solid 2px #dddddd;
            width: 800px;
        }

        div {
            border: solid 3px #aaaaaa;
            width: 400px;
            margin: 0 auto;
        }
    </style>
</head>

<body>
    <article>
        <div>hello</div>
    </article>
</body>

</html>
```





---



### 15.变形透视动画

### 坐标系统

要使用元素变形操作需要掌握坐标轴，然后通过改变不同坐标来控制元素的变形。

![image-20190901174833435](http://houdunren.gitee.io/note/assets/img/image-20190901174833435.9b3582ae.png)

- X轴是水平轴
- Y轴是垂直轴
- Z轴是纵深轴

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#变形操作)变形操作

使用 `transform` 规则控制元素的变形操作，包括控制移动、旋转、倾斜、3D转换等，下面会详细介绍每一个知识点。

下面是CSS提供的变形动作。

| 选项                          | 说明                                  |
| ----------------------------- | ------------------------------------- |
| none                          | 定义不进行转换。                      |
| translate(*x*,*y*)            | 定义 2D 转换。                        |
| translate3d(*x*,*y*,*z*)      | 定义 3D 转换。                        |
| translateX(*x*)               | 定义转换，只是用 X 轴的值。           |
| translateY(*y*)               | 定义转换，只是用 Y 轴的值。           |
| translateZ(*z*)               | 定义 3D 转换，只是用 Z 轴的值。       |
| scale(*x*,*y*)                | 定义 2D 缩放转换。                    |
| scale3d(*x*,*y*,*z*)          | 定义 3D 缩放转换。                    |
| scaleX(*x*)                   | 通过设置 X 轴的值来定义缩放转换。     |
| scaleY(*y*)                   | 通过设置 Y 轴的值来定义缩放转换。     |
| scaleZ(*z*)                   | 通过设置 Z 轴的值来定义 3D 缩放转换。 |
| rotate(*angle*)               | 定义 2D 旋转，在参数中规定角度。      |
| rotate3d(*x*,*y*,*z*,*angle*) | 定义 3D 旋转。                        |
| rotateX(*angle*)              | 定义沿着 X 轴的 3D 旋转。             |
| rotateY(*angle*)              | 定义沿着 Y 轴的 3D 旋转。             |
| rotateZ(*angle*)              | 定义沿着 Z 轴的 3D 旋转。             |
| skew(*x-angle*,*y-angle*)     | 定义沿着 X 和 Y 轴的 2D 倾斜转换。    |
| skewX(*angle*)                | 定义沿着 X 轴的 2D 倾斜转换。         |
| skewY(*angle*)                | 定义沿着 Y 轴的 2D 倾斜转换。         |
| perspective(*n*)              | 为 3D 转换元素定义透视视图。          |

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#变形叠加)变形叠加

重复设置变形操作时只在原形态上操作。

#### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#默认处理)默认处理

下面设置了两次移动，并不会移动 550px 而是只移动50px。

```css
<style>
    div {
        transform: translateX(500px);
        width: 100px;
        height: 100px;
        background: #9b59b6;
    }

    div:nth-child(1) {
        transform: translateX(50px);
    }
</style>

<div></div>
```

#### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#伪类叠加)伪类叠加

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7734353.de347599.gif)

```text
<style>
    div {
        transition: 2s;
        transform: translateX(200px) translateX(50px);
        width: 100px;
        height: 100px;
        background: #9b59b6;
    }

    div:hover {
        transition: 2s;
        transform: translateX(100px);
    }
</style>

<div></div>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#行级元素)行级元素

行级元素不产生变形效果，将其转为 `inline-block` 或 `block` 以及弹性元素时都可以产生变化效果。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7734657.cce0a000.gif)

```text
<style>
    span {
        display: inline-block;
        transition: 2s;
        transform: translateX(100px) translateX(50px);
        width: 100px;
        height: 100px;
        background: #9b59b6;
    }

    span:hover {
        transition: 2s;
        transform: translateX(100px);
    }
</style>

<span>hdcms</span>
```

## [#](http://houdunren.gitee.io/note/css/12 变形动画.html#伪类状态)伪类状态

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#hover):hover

鼠标移动上后发生改变。

![image-20190902133840698](data:image/png;base64,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)

```text
article div:nth-child(2):hover {
	transform: rotate(180deg);
}
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#target):target

以下操作变化时间为零秒，通过掌握后面的过渡动画可以控制变化时间。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7404551.0296ff4c.gif)

```text
<style>
    article {
        width: 300px;
        height: 300px;
        display: grid;
        gap: 10px;
        grid-template-columns: repeat(2, 1fr);
        grid-template-rows: repeat(2, 1fr);
        position: relative;
        border: solid 5px silver;
        color: white;
    }

    article div a {
        color: white;
        text-decoration: none;
    }

    article div,
    article div aside {
        background: blueviolet;
        background-clip: content-box;
        padding: 5px;
        border: solid 2px blueviolet;
        box-sizing: border-box;
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
    }

    article div aside {
        position: absolute;
        display: none;
        width: 100px;
        height: 100px;
    }

    aside:target {
        display: block;
        transform: translateY(150px);
        box-shadow: 0 0 10px #ddd;
    }
</style>

<article>
    <div>
        <a href="#hdcms">hdcms</a>
        <aside id="hdcms">
            内容管理系统
        </aside>
    </div>
    <div>
        <a href="#houdunren">houdunren</a>
        <aside id="houdunren">
            在线社区
        </aside>
    </div>
</article>
```

## [#](http://houdunren.gitee.io/note/css/12 变形动画.html#移动元素)移动元素

- 沿X轴移动时正值向右移动、负值向左移动
- 沿Y轴移动时正值向下移动、负值向上移动
- 如果使用百分数将控制元素的原尺寸计算百分比然后移动
- 可同时设置多个值，解析器会从左向右依次执行
- 变形是在原基础上更改，即第二次设置值时不是在第一次值上变化

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#translatex)translateX

正值向右移动、负值向左移动。

![image-20190901223332605](data:image/png;base64,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)

```text
<style>
    article {
        width: 300px;
        height: 300px;
        position: relative;
        border: solid 5px silver;
    }

    article div {
        width: 100px;
        height: 100px;
        background: blueviolet;
        box-sizing: border-box;
        position: absolute;
        left: 50%;
        margin-left: -50px;
        top: 50%;
        margin-top: -50px;
    }

    article div:nth-child(1) {
        background: #e9dddd;
    }

    article div:nth-child(2) {
        transform: translateX(100px);
    }
</style>
...

<article>
    <div></div>
    <div></div>
</article>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#translatey)translateY

正值向下移动、负值向上移动。

![image-20190901223350501](data:image/png;base64,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)

```text
article div:nth-child(2) {
	transform: translateY(100px);
}
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#translate)translate

使用 `translate` 可以控制按X、Y同时移动操作，第一个值控制X移动，第二个值控制Y移动。

![image-20190901223632200](data:image/png;base64,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)

```text
article div:nth-child(2) {
	transform: translate(100px, -100px);
}
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#百分比移动)百分比移动

元素宽度为100px设置50%时将移动50px，即百分比是指元素的尺寸的百分比。

![image-20190902145927971](data:image/png;base64,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)

```text
article div:nth-child(2) {
	transform: translateX(50%);
}
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#元素居中)元素居中

居中可以使用多种方式，如弹性布局、定位操作，下面来看使用移动操作居中。

![image-20190904112916419](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAaEAAAGgCAYAAAAD9NhnAAABRmlDQ1BJQ0MgUHJvZmlsZQAAKJFjYGASSSwoyGFhYGDIzSspCnJ3UoiIjFJgf8zAycDCwM3AwaCcmFxc4BgQ4ANUwgCjUcG3awyMIPqyLsis/yVB5StatqrLp7H1/9ZzkcFUjwK4UlKLk4H0HyBOTy4oKmFgYEwBspXLSwpA7A4gW6QI6Cggew6InQ5hbwCxkyDsI2A1IUHOQPYNIFsgOSMRaAbjCyBbJwlJPB2JDbUXBHh93BVCfUKCHMM9XVwJuJdkUJJaUQKinfMLKosy0zNKFByBoZSq4JmXrKejYGRgaMnAAApziOrPN8BhySjGgRArEGNgsJgBFHyIEIsH+mG7HAMDfx9CTA3oXwEvBoaD+woSixLhDmD8xlKcZmwEYXNvZ2Bgnfb//+dwBgZ2TQaGv9f///+9/f//v8sYGJhvMTAc+AYAJ69f4g3/CDEAABJBSURBVHgB7dphip1FEIZRI7OX4EpmWZJl3ZUEVxMHIVIwISVzrTcFdfLHJu1093fqx8Ogn769/fnNHwIECBAg8AsEfv8Fd7qSAAECBAj8I/Dy3eHxeHxf+icBAgQIEPjfBV5fX9+d6TehdyT+ggABAgRSAiKUknYPAQIECLwTEKF3JP6CAAECBFICIpSSdg8BAgQIvBP4939MeLfz9hc/+o9IP/r3/B0BAgQIEKgC//V/dvObUFWzJkCAAIGogAhFuV1GgAABAlVAhKqGNQECBAhEBUQoyu0yAgQIEKgCIlQ1rAkQIEAgKiBCUW6XESBAgEAVEKGqYU2AAAECUQERinK7jAABAgSqgAhVDWsCBAgQiAqIUJTbZQQIECBQBUSoalgTIECAQFRAhKLcLiNAgACBKiBCVcOaAAECBKICIhTldhkBAgQIVAERqhrWBAgQIBAVEKEot8sIECBAoAqIUNWwJkCAAIGogAhFuV1GgAABAlVAhKqGNQECBAhEBUQoyu0yAgQIEKgCIlQ1rAkQIEAgKiBCUW6XESBAgEAVEKGqYU2AAAECUQERinK7jAABAgSqgAhVDWsCBAgQiAqIUJTbZQQIECBQBUSoalgTIECAQFRAhKLcLiNAgACBKiBCVcOaAAECBKICIhTldhkBAgQIVAERqhrWBAgQIBAVEKEot8sIECBAoAqIUNWwJkCAAIGogAhFuV1GgAABAlVAhKqGNQECBAhEBUQoyu0yAgQIEKgCIlQ1rAkQIEAgKiBCUW6XESBAgEAVEKGqYU2AAAECUQERinK7jAABAgSqgAhVDWsCBAgQiAqIUJTbZQQIECBQBUSoalgTIECAQFRAhKLcLiNAgACBKiBCVcOaAAECBKICIhTldhkBAgQIVAERqhrWBAgQIBAVEKEot8sIECBAoAqIUNWwJkCAAIGogAhFuV1GgAABAlVAhKqGNQECBAhEBUQoyu0yAgQIEKgCIlQ1rAkQIEAgKiBCUW6XESBAgEAVEKGqYU2AAAECUQERinK7jAABAgSqgAhVDWsCBAgQiAqIUJTbZQQIECBQBUSoalgTIECAQFRAhKLcLiNAgACBKiBCVcOaAAECBKICIhTldhkBAgQIVAERqhrWBAgQIBAVEKEot8sIECBAoAqIUNWwJkCAAIGogAhFuV1GgAABAlVAhKqGNQECBAhEBUQoyu0yAgQIEKgCIlQ1rAkQIEAgKiBCUW6XESBAgEAVEKGqYU2AAAECUQERinK7jAABAgSqgAhVDWsCBAgQiAqIUJTbZQQIECBQBUSoalgTIECAQFRAhKLcLiNAgACBKiBCVcOaAAECBKICIhTldhkBAgQIVAERqhrWBAgQIBAVEKEot8sIECBAoAqIUNWwJkCAAIGogAhFuV1GgAABAlVAhKqGNQECBAhEBUQoyu0yAgQIEKgCIlQ1rAkQIEAgKiBCUW6XESBAgEAVEKGqYU2AAAECUQERinK7jAABAgSqgAhVDWsCBAgQiAqIUJTbZQQIECBQBUSoalgTIECAQFRAhKLcLiNAgACBKiBCVcOaAAECBKICIhTldhkBAgQIVAERqhrWBAgQIBAVEKEot8sIECBAoAqIUNWwJkCAAIGogAhFuV1GgAABAlVAhKqGNQECBAhEBUQoyu0yAgQIEKgCIlQ1rAkQIEAgKiBCUW6XESBAgEAVEKGqYU2AAAECUQERinK7jAABAgSqgAhVDWsCBAgQiAqIUJTbZQQIECBQBUSoalgTIECAQFRAhKLcLiNAgACBKiBCVcOaAAECBKICIhTldhkBAgQIVAERqhrWBAgQIBAVEKEot8sIECBAoAqIUNWwJkCAAIGogAhFuV1GgAABAlVAhKqGNQECBAhEBUQoyu0yAgQIEKgCIlQ1rAkQIEAgKiBCUW6XESBAgEAVEKGqYU2AAAECUQERinK7jAABAgSqgAhVDWsCBAgQiAqIUJTbZQQIECBQBUSoalgTIECAQFRAhKLcLiNAgACBKiBCVcOaAAECBKICIhTldhkBAgQIVAERqhrWBAgQIBAVEKEot8sIECBAoAqIUNWwJkCAAIGogAhFuV1GgAABAlVAhKqGNQECBAhEBUQoyu0yAgQIEKgCIlQ1rAkQIEAgKiBCUW6XESBAgEAVEKGqYU2AAAECUQERinK7jAABAgSqgAhVDWsCBAgQiAqIUJTbZQQIECBQBUSoalgTIECAQFRAhKLcLiNAgACBKiBCVcOaAAECBKICIhTldhkBAgQIVAERqhrWBAgQIBAVEKEot8sIECBAoAqIUNWwJkCAAIGogAhFuV1GgAABAlVAhKqGNQECBAhEBUQoyu0yAgQIEKgCIlQ1rAkQIEAgKvASvc1lBN4E/vzjLw6LBL58/bzoNZ5yTcBvQtcm7nsJECCwSECEFg3DUwgQIHBNQISuTdz3EiBAYJGACC0ahqcQIEDgmoAIXZu47yVAgMAiARFaNAxPIUCAwDUBEbo2cd9LgACBRQIitGgYnkKAAIFrAiJ0beK+lwABAosERGjRMDyFAAEC1wRE6NrEfS8BAgQWCYjQomF4CgECBK4JiNC1ifteAgQILBIQoUXD8BQCBAhcExChaxP3vQQIEFgkIEKLhuEpBAgQuCYgQtcm7nsJECCwSECEFg3DUwgQIHBNQISuTdz3EiBAYJGACC0ahqcQIEDgmoAIXZu47yVAgMAiARFaNAxPIUCAwDUBEbo2cd9LgACBRQIitGgYnkKAAIFrAiJ0beK+lwABAosERGjRMDyFAAEC1wRE6NrEfS8BAgQWCYjQomF4CgECBK4JiNC1ifteAgQILBIQoUXD8BQCBAhcExChaxP3vQQIEFgkIEKLhuEpBAgQuCYgQtcm7nsJECCwSECEFg3DUwgQIHBNQISuTdz3EiBAYJGACC0ahqcQIEDgmoAIXZu47yVAgMAiARFaNAxPIUCAwDUBEbo2cd9LgACBRQIitGgYnkKAAIFrAiJ0beK+lwABAosERGjRMDyFAAEC1wRE6NrEfS8BAgQWCYjQomF4CgECBK4JiNC1ifteAgQILBIQoUXD8BQCBAhcExChaxP3vQQIEFgkIEKLhuEpBAgQuCYgQtcm7nsJECCwSECEFg3DUwgQIHBNQISuTdz3EiBAYJGACC0ahqcQIEDgmoAIXZu47yVAgMAiARFaNAxPIUCAwDUBEbo2cd9LgACBRQIitGgYnkKAAIFrAiJ0beK+lwABAosERGjRMDyFAAEC1wRE6NrEfS8BAgQWCYjQomF4CgECBK4JiNC1ifteAgQILBIQoUXD8BQCBAhcExChaxP3vQQIEFgkIEKLhuEpBAgQuCYgQtcm7nsJECCwSECEFg3DUwgQIHBNQISuTdz3EiBAYJGACC0ahqcQIEDgmoAIXZu47yVAgMAiARFaNAxPIUCAwDUBEbo2cd9LgACBRQIitGgYnkKAAIFrAiJ0beK+lwABAosERGjRMDyFAAEC1wRE6NrEfS8BAgQWCYjQomF4CgECBK4JiNC1ifteAgQILBIQoUXD8BQCBAhcExChaxP3vQQIEFgkIEKLhuEpBAgQuCYgQtcm7nsJECCwSECEFg3DUwgQIHBNQISuTdz3EiBAYJGACC0ahqcQIEDgmoAIXZu47yVAgMAiARFaNAxPIUCAwDUBEbo2cd9LgACBRQIitGgYnkKAAIFrAiJ0beK+lwABAosERGjRMDyFAAEC1wRE6NrEfS8BAgQWCYjQomF4CgECBK4JiNC1ifteAgQILBIQoUXD8BQCBAhcExChaxP3vQQIEFgkIEKLhuEpBAgQuCYgQtcm7nsJECCwSECEFg3DUwgQIHBNQISuTdz3EiBAYJHAy6K3eMoRgS9fPx/5Up9JgEAn4DehTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAmI0BitgwkQIECgExChTsg+AQIECIwJiNAYrYMJECBAoBMQoU7IPgECBAiMCYjQGK2DCRAgQKATEKFOyD4BAgQIjAm8/Ozkx+Pxs217BAgQIEDgKQG/CT3F54cJECBA4BkBEXpGz88SIECAwFMCIvQUnx8mQIAAgWcEROgZPT9LgAABAk8JfPr29uepE/wwAQIECBD4oIDfhD4I58cIECBA4HkBEXre0AkECBAg8EEBEfognB8jQIAAgecF/gaE1xfrbjML7gAAAABJRU5ErkJggg==)

```text
<style>
    body {
        height: 100vh;
    }

    main {
        width: 400px;
        height: 400px;
        border: solid 5px silver;
        position: relative;
    }

    main div {
        width: 100px;
        height: 100px;
        background: blueviolet;
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
    }
</style>

<main>
    <div></div>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#translatez)translateZ

控制Z轴移动，正数向外、负数向里移动。因为Z轴是透视轴没有像X/Y一样的固定尺寸，所以不能使用百分数。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7827784.63fc4fc8.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        list-style: none;
    }

    body {
        width: 100vw;
        height: 100vh;
        background: #34495e;
    }

    main {
        position: absolute;
        left: 50%;
        top: 50%;
        width: 200px;
        height: 200px;
        transform-style: preserve-3d;
        transition: 2s;
        transform: perspective(900px) rotateY(60deg);
    }

    body:hover main {
        transform: perspective(600px) rotateY(60deg) scaleZ(5);
    }

    div {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: #f1c40f;
    }

    div.b {
        background: #8e44ad;
        transform: translateZ(-100px);
    }
</style>

<main>
    <div class="f"></div>
    <div class="b"></div>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#translate3d)translate3d

用于同时控制X/Y/Z轴的移动，三个值必须输入如果某个轴不需要移动时设置为零。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7824321.6a82c902.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        list-style: none;
    }

    body {
        width: 100vw;
        height: 100vh;
        background: #34495e;
    }

    main {
        position: absolute;
        left: 50%;
        top: 50%;
        width: 200px;
        height: 200px;
        background: #f1c40f;
        perspective: 600px;
        transform: perspective(600px) rotateY(35deg);
        transition: 2s;
    }

    body:hover main {
        transform: perspective(600px) rotateY(35deg) translate3d(50%, 50%, 200px);
    }
</style>

<main>
	<div></div>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#渐变表单)渐变表单

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7851179.821af195.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    body {
        width: 100vw;
        height: 100vh;
        background: #34495e;
    }

    main {
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        width: 300px;
        height: 300px;
        border: solid 5px silver;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .field {
        position: relative;
        overflow: hidden;
        margin-bottom: 20px;
    }

    .field::before {
        content: '';
        position: absolute;
        left: 0;
        height: 2px;
        bottom: 0;
        width: 100%;
        background: linear-gradient(to right, white, #1abc9c, #f1c40f, #e74c3c, white);
        transform: translateX(-100%);
        transition: 2s;
    }

    .field:hover::before {
        transform: translateX(100%);
    }

    .field input {
        border: none;
        outline: none;
        background: #ecf0f1;
        padding: 10px;
    }
</style>

<main>
    <div class="field">
        <input type="text" placeholder="请输入后盾人帐号">
    </div>
    <div class="field">
        <input type="text" placeholder="请输入密码">
    </div>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#页面切换)页面切换

下面是使用移动效果制作的页面切换效果。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7584912.730ab731.gif)

```text
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css">
<style>
    * {
        padding: 0;
        margin: 0;
    }

    a {
        text-decoration: none;
    }

    body {
        display: flex;
        width: 100vw;
        height: 100vh;
        flex-direction: column;
    }

    main {
        position: relative;
        background: #f3f3f3;
        flex: 1;
        overflow: hidden;
    }

    nav {
        display: flex;
        justify-content: space-around;
        align-items: center;
        height: 8vh;
        text-align: center;
        background: #34495e;
    }

    nav a {
        flex: 1;
        font-size: 1.3em;
        text-transform: uppercase;
        font-weight: bold;
        opacity: .8;
        color: white;
    }

    nav a:nth-child(2) {
        border-right: solid 1px #aaa;
        border-left: solid 1px #aaa;
    }

    main>div {
        position: absolute;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        transition: all 1s;
        z-index: 1;
        background: #f3f3f3;
        opacity: 0;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        transform: translate(0, -100%);
        color: white;
        font-size: 2em;
    }

    main>div:target {
        opacity: 1;
        transform: translate(0%, 0%);
    }

    main>div:nth-of-type(1):target {
        background: #3498db;
    }

    main>div:nth-of-type(2):target {
        background: #9b59b6;
    }

    main>div:nth-of-type(3):target {
        background: #16a085;
    }

    div i[class^="fa"] {
        font-size: 100px;
        color: white;
    }
</style>

<body>
    <main>
        <div id="home">
            <i class="fa fa-home" aria-hidden="true"></i>
            houdunren.com
        </div>
        <div id="video">
            <i class="fa fa-vimeo" aria-hidden="true"></i>
        </div>
        <div id="live">
            <i class="fa fa-viadeo" aria-hidden="true"></i>
        </div>
    </main>
    <nav>
        <a href="#home">home</a>
        <a href="#video">video</a>
        <a href="#live">live</a>
    </nav>
</body>
```

## [#](http://houdunren.gitee.io/note/css/12 变形动画.html#缩放元素)缩放元素

比如数值为2时表示为原尺寸的两倍。

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#scalex)scaleX

下面是沿X轴缩放一半。

![image-20190902151123183](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAY8AAAGSCAYAAAAb0k2iAAABRmlDQ1BJQ0MgUHJvZmlsZQAAKJFjYGASSSwoyGFhYGDIzSspCnJ3UoiIjFJgf8zAycDEwMOgyaCcmFxc4BgQ4ANUwgCjUcG3awyMIPqyLsgscyG/7BVLP8ytjPr/X1730SJM9SiAKyW1OBlI/wHi9OSCohIGBsYUIFu5vKQAxO4AskWKgI4CsueA2OkQ9gYQOwnCPgJWExLkDGTfALIFkjMSgWYwvgCydZKQxNOR2FB7QYDXx10h1CckyDHc08WVgHtJBiWpFSUg2jm/oLIoMz2jRMERGEqpCp55yXo6CkYGhpYMDKAwh6j+fAMcloxiHAixAjEGBosZQMGHCLF4oB+2yzEw8PchxNSA/hXwYmA4uK8gsSgR7gDGbyzFacZGEDb3dgYG1mn//38OZ2Bg12Rg+Hv9///f2////7uMgYH5FgPDgW8AEPRhmJCm9HoAABE3SURBVHgB7dqxbSTmFQRgSrgmpAYucR+XqQ034dDdKFPGPpyoAbsMSXCquQcsSGBnsN+F7z9yh98cMCCkH/7468+bPwQIECBA4AGBHx/4u/4qAQIECBD4v4Dx8A+BAAECBB4WMB4Pk/kCAgQIEDAe/g0QIECAwMMCxuNhMl9AgAABAsbDvwECBAgQeFjAeDxM5gsIECBA4EsieH9/T2c3AgQIEHgxgW/fvsWf2G8ekcWRAAECBC4B43HpeCNAgACBKGA8IosjAQIECFwCxuPS8UaAAAECUcB4RBZHAgQIELgE4v9t9b0v+N5/df/e33cnQIAAgQ2BR/8vW795bPQqJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ8B4bPQkJQECBKoEjEdVHcIQIEBgQ+DLRkwpnynwv99/f9rH//avt7f//udpH/+0D/75H29vv/z7aR//9tPXr8/7cJ88IeA3j4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAgYj4mahCRAgECXgPHo6kMaAgQITAh8mUgp5FMFfvr69Wmf/89fn/bRPpgAgUPAbx4HjicCBAgQyALGI7u4EiBAgMAhYDwOHE8ECBAgkAWMR3ZxJUCAAIFDwHgcOJ4IECBAIAsYj+ziSoAAAQKHgPE4cDwRIECAQBYwHtnFlQABAgQOAeNx4HgiQIAAgSxgPLKLKwECBAgcAsbjwPFEgAABAlnAeGQXVwIECBA4BIzHgeOJAAECBLKA8cgurgQIECBwCBiPA8cTAQIECGQB45FdXAkQIEDgEDAeB44nAgQIEMgCxiO7uBIgQIDAIWA8DhxPBAgQIJAFjEd2cSVAgACBQ8B4HDieCBAgQCALGI/s4kqAAAECh4DxOHA8ESBAgEAWMB7ZxZUAAQIEDgHjceB4IkCAAIEsYDyyiysBAgQIHALG48DxRIAAAQJZwHhkF1cCBAgQOASMx4HjiQABAgSygPHILq4ECBAgcAgYjwPHEwECBAhkAeORXVwJECBA4BAwHgeOJwIECBDIAsYju7gSIECAwCFgPA4cTwQIECCQBYxHdnElQIAAgUPAeBw4nggQIEAgCxiP7OJKgAABAoeA8ThwPBEgQIBAFjAe2cWVAAECBA4B43HgeCJAgACBLGA8sosrAQIECBwCxuPA8USAAAECWcB4ZBdXAgQIEDgEjMeB44kAAQIEsoDxyC6uBAgQIHAIGI8DxxMBAgQIZAHjkV1cCRAgQOAQMB4HjicCBAgQyALGI7u4EiBAgMAhYDwOHE8ECBAgkAWMR3ZxJUCAAIFDwHgcOJ4IECBAIAsYj+ziSoAAAQKHgPE4cDwRIECAQBYwHtnFlQABAgQOAeNx4HgiQIAAgSxgPLKLKwECBAgcAsbjwPFEgAABAlnAeGQXVwIECBA4BIzHgeOJAAECBLKA8cgurgQIECBwCBiPA8cTAQIECGQB45FdXAkQIEDgEDAeB44nAgQIEMgCxiO7uBIgQIDAIWA8DhxPBAgQIJAFjEd2cSVAgACBQ8B4HDieCBAgQCALGI/s4kqAAAECh4DxOHA8ESBAgEAWMB7ZxZUAAQIEDgHjceB4IkCAAIEsYDyyiysBAgQIHALG48DxRIAAAQJZwHhkF1cCBAgQOASMx4HjiQABAgSygPHILq4ECBAgcAgYjwPHEwECBAhkAeORXVwJECBA4BAwHgeOJwIECBDIAsYju7gSIECAwCFgPA4cTwQIECCQBYxHdnElQIAAgUPAeBw4nggQIEAgCxiP7OJKgAABAoeA8ThwPBEgQIBAFjAe2cWVAAECBA4B43HgeCJAgACBLGA8sosrAQIECBwCxuPA8USAAAECWcB4ZBdXAgQIEDgEjMeB44kAAQIEsoDxyC6uBAgQIHAIGI8DxxMBAgQIZAHjkV1cCRAgQOAQMB4HjicCBAgQyALGI7u4EiBAgMAhYDwOHE8ECBAgkAWMR3ZxJUCAAIFDwHgcOJ4IECBAIAsYj+ziSoAAAQKHgPE4cDwRIECAQBYwHtnFlQABAgQOAeNx4HgiQIAAgSxgPLKLKwECBAgcAsbjwPFEgAABAlnAeGQXVwIECBA4BIzHgeOJAAECBLKA8cgurgQIECBwCBiPA8cTAQIECGQB45FdXAkQIEDgEDAeB44nAgQIEMgCxiO7uBIgQIDAIWA8DhxPBAgQIJAFjEd2cSVAgACBQ8B4HDieCBAgQCALGI/s4kqAAAECh4DxOHA8ESBAgEAWMB7ZxZUAAQIEDgHjceB4IkCAAIEsYDyyiysBAgQIHALG48DxRIAAAQJZwHhkF1cCBAgQOAS+HG9/e3p/f//bzYEAAQIEXk/Abx6v17mfmAABAh8WMB4fJvQNCBAg8HoCxuP1OvcTEyBA4MMCxuPDhL4BAQIEXk/AeLxe535iAgQIfFjghz/++vPh7+IbECBAgMBLCfjN46Xq9sMSIEDgcwSMx+c4+i4ECBB4KQHj8VJ1+2EJECDwOQLG43McfRcCBAi8lIDxeKm6/bAECBD4HAHj8TmOvgsBAgReSuBPI34byRTzbq4AAAAASUVORK5CYII=)

```text
article div:nth-child(2) {
	transform: scaleX(.5);
}
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#scaley)scaleY

下面是沿Y轴缩放一半。

![image-20190902151103536](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAY8AAAGPCAYAAACkmlznAAABRmlDQ1BJQ0MgUHJvZmlsZQAAKJFjYGASSSwoyGFhYGDIzSspCnJ3UoiIjFJgf8zAycDEwMOgyaCcmFxc4BgQ4ANUwgCjUcG3awyMIPqyLsgscyG/7BVLP8ytjPr/X1730SJM9SiAKyW1OBlI/wHi9OSCohIGBsYUIFu5vKQAxO4AskWKgI4CsueA2OkQ9gYQOwnCPgJWExLkDGTfALIFkjMSgWYwvgCydZKQxNOR2FB7QYDXx10h1CckyDHc08WVgHtJBiWpFSUg2jm/oLIoMz2jRMERGEqpCp55yXo6CkYGhpYMDKAwh6j+fAMcloxiHAixAjEGBosZQMGHCLF4oB+2yzEw8PchxNSA/hXwYmA4uK8gsSgR7gDGbyzFacZGEDb3dgYG1mn//38OZ2Bg12Rg+Hv9///f2////7uMgYH5FgPDgW8AEPRhmJCm9HoAABEhSURBVHgB7dqxkWZnFQRQRE0SIoF1yGM9pUESmGSDhzd54CgBCENSYc9O1Rj3/d3NWXO0+l7f06rqWkk//fbHrz/5RYAAAQIEviDw5y/8Xr+VAAECBAj8T8B4+AeBAAECBL4sYDy+TOZvIECAAAHj4Z8BAgQIEPiygPH4Mpm/gQABAgTePiJ4f3//6Md+RoAAAQL/ZwLfv3//8GJ/8viQxQ8JECBA4DMB4/GZjr9GgAABAh8KGI8PWfyQAAECBD4TMB6f6fhrBAgQIPChgPH4kMUPCRAgQOAzgQ//b6sf/Q0/+q/uP/r9fk6AAAECHQJf/b9s/cmjo1cpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycpCRAgECVgPKLqEIYAAQIdAsajoycp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)

```text
article div:nth-child(2) {
	transform: scaleY(.5);
}
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#scale)scale

使用 `scale` 可同时设置 `X/Y` 轴的缩放，如果只设置一个值时表示两轴缩放相同。

使用数值定义缩放，如 .5 表示缩小一半，2 表示放大两倍。

![image-20190902151035273](data:image/png;base64,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)

```text
article div:nth-child(2) {
	transform: scale(.5, 2);
}
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#scalez)scaleZ

沿Z轴缩放元素，需要有3D透视才可以查看到效果。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7905140.2e8820f0.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    body {
        width: 100vw;
        height: 100vh;
    }

    main {
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        width: 400px;
        height: 400px;
        border: solid 5px silver;
        transform-style: preserve-3d;
        transform: perspective(900px) rotateY(45deg);
        transition: 3s;
    }

    div {
        position: absolute;
        left: 50%;
        top: 50%;
        margin-left: -100px;
        margin-top: -100px;
        width: 200px;
        height: 200px;
    }

    div:nth-child(1) {
        background: #2ecc71;
    }

    div:nth-child(2) {
        background: #e67e22;
        transition: 1s;
        transform: translateZ(-300px);
    }

    body:hover main {

        transform: perspective(900px) rotateY(45deg) scaleZ(3);
    }
</style>

<main>
    <div></div>
    <div></div>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#scale3d)scale3d

沿X/Y/Z三个轴绽放元素。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7828065.e355537e.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        list-style: none;
    }

    body {
        width: 100vw;
        height: 100vh;
        background: #34495e;
    }

    main {
        position: absolute;
        left: 50%;
        top: 50%;
        width: 200px;
        height: 200px;
        transform-style: preserve-3d;
        transition: 2s;
        transform: perspective(900px) rotateY(60deg)
    }

    body:hover main {
        transform: perspective(600px) rotateY(60deg) scale3d(2, 2, 4);
    }

    div {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: #f1c40f;
    }

    div.b {
        background: #8e44ad;
        transform: translateZ(-100px);
    }
</style>

<main>
    <div class="f"></div>
    <div class="b"></div>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#菜单缩放)菜单缩放

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7638319.e0db60be.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
    }

    body {
        background: #34495e;
    }

    main {
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
    }

    ul {
        list-style: none;
        display: flex;
        justify-content: space-evenly;
        width: 200px;
    }

    ul li {
        position: relative;
    }

    ul li strong {
        background: #e67e22;
        color: #2c3e50;
        padding: 2px 20px;
        cursor: pointer;
        text-transform: uppercase;
    }

    ul li strong+div {
        border: solid 2px #e67e22;
        display: flex;
        flex-direction: column;
        padding: 10px 20px;
        position: absolute;
        transform-origin: left top;
        transform: scale(0);
        z-index: -1;
        transition: .6s;
        background: #e67e22;
    }

    ul li strong+div a {
        display: inline-block;
        padding: 5px;
        font-size: 1em;
        color: #2c3e50;
        text-decoration: none;
        text-transform: uppercase;
    }

    ul li:hover strong+div {
        transform: scale(1);
    }
</style>

<main>
    <ul>
        <li>
            <strong>VIDEO</strong>
            <div>
                <a href="">PHP</a>
                <a href="">hdcms</a>
                <a href="">laravel</a>
            </div>
        </li>
        <li>
            <strong>LIVE</strong>
            <div>
                <a href="">houdunren</a>
                <a href="">angular</a>
                <a href="">css3</a>
            </div>
        </li>
    </ul>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#相册放大)相册放大

下面是使用缩放开发相册放大效果的示例。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7641188.78385d23.gif)

```text
<style>
    body {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        background: #ddd;
    }

    main {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    main div {
        height: 200px;
        width: 200px;
        background: white;
        border: solid 1px #ddd;
        transition: all .5s;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 1.5em;
        text-transform: uppercase;
        color: blueviolet;
        overflow: hidden;
        border: solid 3px #555;
        box-sizing: border-box;
    }

    main div img {
        height: 100%;
    }

    main:hover div {
        transform: scale(.8) translateY(-30px);
        cursor: pointer;
        filter: blur(15px);
    }

    main div:hover {
        transform: scale(1.6);
        color: white;
        filter: none;
        z-index: 2;
    }

    main div:hover::after {
        content: '';
        position: absolute;
        background: #000;
        width: 100%;
        height: 100%;
        z-index: -1;
        box-shadow: 0 0 5px rgba(0, 0, 0, .3);
    }
</style>

<main>
    <div>
        <img src="1.jpg" alt="">
    </div>
    <div> <img src="2.jpg" alt=""></div>
    <div> <img src="3.jpg" alt=""></div>
</main>
```

## [#](http://houdunren.gitee.io/note/css/12 变形动画.html#旋转操作)旋转操作

使用CSS可以控制元素按照不同坐标轴进行旋转。

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#rotatex)rotateX

控制元素按照X轴进行旋转操作。

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#基本使用)基本使用

按水平轴发生旋转，如果旋转90deg 将不可见。

![image-20190902130125983](data:image/png;base64,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jQICsMap6IkAgSICArAIsyIECNQoIABrnIqeCBAoIiAAizArQoBAjQICsMap6IkAgSICArAIsyIECNQoIABrnIqeCBAoIiAAizArQoBAjQICsMap6IkAgSICArAIsyIECNQoIABrnIqeCBAoIiAAizArQoBAjQICsMap6IkAgSICArAIsyIECNQoIABrnIqeCBAoIiAAizArQoBAjQICsMap6IkAgSICArAIsyIECNQoIABrnIqeCBAoIiAAizArQoBAjQICsMap6IkAgSICArAI8+QqMv+UwbTm0rnp5IXTj9n4QO+3Zvm5s9JZrz055e/bthknTUvnvH5OmrdssO2UtPC0GU2tmSc/x4VaH/38B2bNnZZWXzInnbJm1vOf7IwpJ9D+mznlKLq74GVnz0xX/euZ6c6btqXbP7VldKG/+TenpvMvm5euOX99OnQwpXze7/3j6enkRWPB99Sj+9NNv7sx7dxyoHncohUz0pW3npFOmtcPrOFDKd196470qrcvSP/x11vStz+7rQnFd9+4Ip39C3NGa23buK+3fyDNmD2QPvmLDzb733fbGenlrxwLpvuHdqZXvnFuevTePemmd25M+Xju6S8v+OHodfI3H79vTdp4z7Ppc+/qn7P0rJnp2gvHn5P7e89nV6bTLjhp9LH79xxKt33k8XTfv+9s9l197+q09aF96YZf3TB6ztmvm9N73Ip0+ye3pDs/t210v2+6KXBi/tntptWkX1Xb3drAwEAanDXQBNvsBdOb//hzKOTAzHdo7//qGaNr//W/Wt6E34//e3f68lWb0v2372zCL58wbfpAc97bP3VqE34P3rkrffrXNqQvvX9TmrN4MOXwHNle9/uLm/Db/tj+JpS+deO2tOYNc5trtPU58tjj+frun4bfo9/b09S/42+fTMPDKf3GJ5anfGc6uvVbHv3RN1NLwB3g1Jp362rf9KfL0uDMgZSDaOTO5/b1W5oAPO/N89LFv7Uwfffm7WnZOTPTwQPD6QtXPNJc6wd3PJOuPH1VWv4zY3da562dl/buOpS++AePNuc8/oO96eYPPpbyXeHI9orenVbe/qkXopsf2Nt8f6h33Uvet6T5/qX8lUN7Re/Ob8fjB9KN73i4udT6rz+THrn32fSuz6xIr3/v4nTH3z35Ukp4bEcEDvunsCMrsowXJbDiwtnN477z5e3j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)

```text
article div:nth-child(2) {
    transform: rotateX(180deg);
}
```

下面是旋转89deg后，只会看到一条线。

![image-20190902130411118](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAdsAAAHhCAYAAAAmmxT/AAABRmlDQ1BJQ0MgUHJvZmlsZQAAKJFjYGASSSwoyGFhYGDIzSspCnJ3UoiIjFJgf8zAycDEwMOgyaCcmFxc4BgQ4ANUwgCjUcG3awyMIPqyLsgscyG/7BVLP8ytjPr/X1730SJM9SiAKyW1OBlI/wHi9OSCohIGBsYUIFu5vKQAxO4AskWKgI4CsueA2OkQ9gYQOwnCPgJWExLkDGTfALIFkjMSgWYwvgCydZKQxNOR2FB7QYDXx10h1CckyDHc08WVgHtJBiWpFSUg2jm/oLIoMz2jRMERGEqpCp55yXo6CkYGhpYMDKAwh6j+fAMcloxiHAixAjEGBosZQMGHCLF4oB+2yzEw8PchxNSA/hXwYmA4uK8gsSgR7gDGbyzFacZGEDb3dgYG1mn//38OZ2Bg12Rg+Hv9///f2////7uMgYH5FgPDgW8AEPRhmJCm9HoAABdDSURBVHgB7dzBrV3FEoZRQDcJR+BQPCUM0iALwmB6I0FEQBgGMbOu1W61+uwq1b+YPZ+9d3etQvrkAe/nr//985N/CBAgQIAAgZcJ/PKyL/swAQIECBAg8L+A2PoXgQABAgQIvFhAbF8M7PMECBAgQEBs/TtAgAABAgReLCC2Lwb2eQIECBAgILb+HSBAgAABAi8WENsXA/s8AQIECBB4+x7B+/v79/7YnxEgQIAAAQI/EPjy5cuHJ/zN9gOJPyBAgAABAncFxPaup68RIECAAIEPAmL7gcQfECBAgACBuwJie9fT1wgQIECAwAcBsf1A4g8IECBAgMBdAbG96+lrBAgQIEDgg4DYfiDxBwQIECBA4K7Ad/872x8d8b3/huhH7/idAAECBAhMEDj5/6LwN9sJmzcDAQIECLQWENvW63E5AgQIEJggILYTtmgGAgQIEGgtILat1+NyBAgQIDBBQGwnbNEMBAgQINBaQGxbr8flCBAgQGCCgNhO2KIZCBAgQKC1gNi2Xo/LESBAgMAEAbGdsEUzECBAgEBrAbFtvR6XI0CAAIEJAmI7YYtmIECAAIHWAmLbej0uR4AAAQITBMR2whbNQIAAAQKtBcS29XpcjgABAgQmCIjthC2agQABAgRaC4ht6/W4HAECBAhMEBDbCVs0AwECBAi0FhDb1utxOQIECBCYICC2E7ZoBgIECBBoLSC2rdfjcgQIECAwQUBsJ2zRDAQIECDQWkBsW6/H5QgQIEBggoDYTtiiGQgQIECgtYDYtl6PyxEgQIDABAGxnbBFMxAgQIBAawGxbb0elyNAgACBCQJiO2GLZiBAgACB1gJi23o9LkeAAAECEwTEdsIWzUCAAAECrQXEtvV6XI4AAQIEJgiI7YQtmoEAAQIEWguIbev1uBwBAgQITBAQ2wlbNAMBAgQItBYQ29brcTkCBAgQmCAgthO2aAYCBAgQaC0gtq3X43IECBAgMEFAbCds0QwECBAg0FpAbFuvx+UIECBAYIKA2E7YohkIECBAoLWA2LZej8sRIECAwAQBsZ2wRTMQIECAQGsBsW29HpcjQIAAgQkCYjthi2YgQIAAgdYCYtt6PS5HgAABAhMExHbCFs1AgAABAq0FxLb1elyOAAECBCYIiO2ELZqBAAECBFoLiG3r9bgcAQIECEwQENsJWzQDAQIECLQWENvW63E5AgQIEJggILYTtmgGAgQIEGgtILat1+NyBAgQIDBBQGwnbNEMBAgQINBaQGxbr8flCBAgQGCCgNhO2KIZCBAgQKC1gNi2Xo/LESBAgMAEAbGdsEUzECBAgEBrAbFtvR6XI0CAAIEJAmI7YYtmIECAAIHWAmLbej0uR4AAAQITBMR2whbNQIAAAQKtBcS29XpcjgABAgQmCIjthC2agQABAgRaC4ht6/W4HAECBAhMEBDbCVs0AwECBAi0FhDb1utxOQIECBCYICC2E7ZoBgIECBBoLSC2rdfjcgQIECAwQUBsJ2zRDAQIECDQWkBsW6/H5QgQIEBggoDYTtiiGQgQIECgtYDYtl6PyxEgQIDABAGxnbBFMxAgQIBAawGxbb0elyNAgACBCQJiO2GLZiBAgACB1gJi23o9LkeAAAECEwTEdsIWzUCAAAECrQXEtvV6XI4AAQIEJgiI7YQtmoEAAQIEWguIbev1uBwBAgQITBAQ2wlbNAMBAgQItBYQ29brcTkCBAgQmCAgthO2aAYCBAgQaC0gtq3X43IECBAgMEFAbCds0QwECBAg0FpAbFuvx+UIECBAYIKA2E7YohkIECBAoLWA2LZej8sRIECAwAQBsZ2wRTMQIECAQGsBsW29HpcjQIAAgQkCYjthi2YgQIAAgdYCYtt6PS5HgAABAhMExHbCFs1AgAABAq0FxLb1elyOAAECBCYIiO2ELZqBAAECBFoLiG3r9bgcAQIECEwQENsJWzQDAQIECLQWENvW63E5AgQIEJggILYTtmgGAgQIEGgtILat1+NyBAgQIDBBQGwnbNEMBAgQINBaQGxbr8flCBAgQGCCgNhO2KIZCBAgQKC1gNi2Xo/LESBAgMAEAbGdsEUzECBAgEBrAbFtvR6XI0CAAIEJAmI7YYtmIECAAIHWAmLbej0uR4AAAQITBMR2whbNQIAAAQKtBcS29XpcjgABAgQmCIjthC2agQABAgRaC4ht6/W4HAECBAhMEBDbCVs0AwECBAi0FhDb1utxOQIECBCYICC2E7ZoBgIECBBoLSC2rdfjcgQIECAwQUBsJ2zRDAQIECDQWkBsW6/H5QgQIEBggoDYTtiiGQgQIECgtYDYtl6PyxEgQIDABAGxnbBFMxAgQIBAawGxbb0elyNAgACBCQJiO2GLZiBAgACB1gJi23o9LkeAAAECEwTEdsIWzUCAAAECrQXEtvV6XI4AAQIEJgiI7YQtmoEAAQIEWguIbev1uBwBAgQITBAQ2wlbNAMBAgQItBYQ29brcTkCBAgQmCAgthO2aAYCBAgQaC0gtq3X43IECBAgMEFAbCds0QwECBAg0FpAbFuvx+UIECBAYIKA2E7YohkIECBAoLWA2LZej8sRIECAwAQBsZ2wRTMQIECAQGsBsW29HpcjQIAAgQkCYjthi2YgQIAAgdYCYtt6PS5HgAABAhMExHbCFs1AgAABAq0FxLb1elyOAAECBCYIiO2ELZqBAAECBFoLiG3r9bgcAQIECEwQENsJWzQDAQIECLQWENvW63E5AgQIEJggILYTtmgGAgQIEGgtILat1+NyBAgQIDBBQGwnbNEMBAgQINBa4K317VwuSuCfv/+Omtewzwh8+vz5mYOcQmAh4G+2Cxw/ESBAgACBGwJie0PRNwgQIECAwEJAbBc4fiJAgAABAjcExPaGom8QIECAAIGFgNgucPxEgAABAgRuCIjtDUXfIECAAAECCwGxXeD4iQABAgQI3BAQ2xuKvkGAAAECBBYCYrvA8RMBAgQIELghILY3FH2DAAECBAgsBMR2geMnAgQIECBwQ0Bsbyj6BgECBAgQWAiI7QLHTwQIECBA4IaA2N5Q9A0CBAgQILAQENsFjp8IECBAgMANAbG9oegbBAgQIEBgISC2Cxw/ESBAgACBGwJie0PRNwgQIECAwEJAbBc4fiJAgAABAjcExPaGom8QIECAAIGFgNgucPxEgAABAgRuCIjtDUXfIECAAAECCwGxXeD4iQABAgQI3BAQ2xuKvkGAAAECBBYCYrvA8RMBAgQIELghILY3FH2DAAECBAgsBMR2geMnAgQIECBwQ0Bsbyj6BgECBAgQWAiI7QLHTwQIECBA4IaA2N5Q9A0CBAgQILAQENsFjp8IECBAgMANAbG9oegbBAgQIEBgISC2Cxw/ESBAgACBGwJie0PRNwgQIECAwEJAbBc4fiJAgAABAjcExPaGom8QIECAAIGFgNgucPxEgAABAgRuCIjtDUXfIECAAAECCwGxXeD4iQABAgQI3BAQ2xuKvkGAAAECBBYCYrvA8RMBAgQIELghILY3FH2DAAECBAgsBMR2geMnAgQIECBwQ0Bsbyj6BgECBAgQWAiI7QLHTwQIECBA4IaA2N5Q9A0CBAgQILAQENsFjp8IECBAgMANAbG9oegbBAgQIEBgISC2Cxw/ESBAgACBGwJie0PRNwgQIECAwEJAbBc4fiJAgAABAjcExPaGom8QIECAAIGFgNgucPxEgAABAgRuCIjtDUXfIECAAAECCwGxXeD4iQABAgQI3BAQ2xuKvkGAAAECBBYCYrvA8RMBAgQIELghILY3FH2DAAECBAgsBMR2geMnAgQIECBwQ0Bsbyj6BgECBAgQWAiI7QLHTwQIECBA4IaA2N5Q9A0CBAgQILAQENsFjp8IECBAgMANAbG9oegbBAgQIEBgISC2Cxw/ESBAgACBGwJie0PRNwgQIECAwEJAbBc4fiJAgAABAjcExPaGom8QIECAAIGFgNgucPxEgAABAgRuCIjtDUXfIECAAAECCwGxXeD4iQABAgQI3BAQ2xuKvkGAAAECBBYCYrvA8RMBAgQIELgh8HbjI75B4IbAH7/e+IpvEPhW4Pe/vv3f/heBCgF/s61QdyYBAgQIRAn4m23UunsP+9ufve/ndgQIEDgV8DfbUznvESBAgACBTQGx3YTyGAECBAgQOBUQ21M57xEgQIAAgU0Bsd2E8hgBAgQIEDgVENtTOe8RIECAAIFNAbHdhPIYAQIECBA4FRDbUznvESBAgACBTQGx3YTyGAECBAgQOBUQ21M57xEgQIAAgU0Bsd2E8hgBAgQIEDgVENtTOe8RIECAAIFNAbHdhPIYAQIECBA4FRDbUznvESBAgACBTQGx3YTyGAECBAgQOBUQ21M57xEgQIAAgU0Bsd2E8hgBAgQIEDgVENtTOe8RIECAAIFNAbHdhPIYAQIECBA4FRDbUznvESBAgACBTQGx3YTyGAECBAgQOBUQ21M57xEgQIAAgU0Bsd2E8hgBAgQIEDgVENtTOe8RIECAAIFNAbHdhPIYAQIECBA4FRDbUznvESBAgACBTQGx3YTyGAECBAgQOBUQ21M57xEgQIAAgU0Bsd2E8hgBAgQIEDgVENtTOe8RIECAAIFNAbHdhPIYAQIECBA4FRDbUznvESBAgACBTQGx3YTyGAECBAgQOBUQ21M57xEgQIAAgU0Bsd2E8hgBAgQIEDgVENtTOe8RIECAAIFNAbHdhPIYAQIECBA4FRDbUznvESBAgACBTQGx3YTyGAECBAgQOBUQ21M57xEgQIAAgU0Bsd2E8hgBAgQIEDgVENtTOe8RIECAAIFNAbHdhPIYAQIECBA4FRDbUznvESBAgACBTQGx3YTyGAECBAgQOBUQ21M57xEgQIAAgU0Bsd2E8hgBAgQIEDgVENtTOe8RIECAAIFNAbHdhPIYAQIECBA4FRDbUznvESBAgACBTQGx3YTyGAECBAgQOBUQ21M57xEgQIAAgU0Bsd2E8hgBAgQIEDgVENtTOe8RIECAAIFNAbHdhPIYAQIECBA4FRDbUznvESBAgACBTQGx3YTyGAECBAgQOBUQ21M57xEgQIAAgU0Bsd2E8hgBAgQIEDgVENtTOe8RIECAAIFNAbHdhPIYAQIECBA4FRDbUznvESBAgACBTQGx3YTyGAECBAgQOBUQ21M57xEgQIAAgU0Bsd2E8hgBAgQIEDgVENtTOe8RIECAAIFNAbHdhPIYAQIECBA4FRDbUznvESBAgACBTQGx3YTyGAECBAgQOBUQ21M57xEgQIAAgU0Bsd2E8hgBAgQIEDgVENtTOe8RIECAAIFNAbHdhPIYAQIECBA4FRDbUznvESBAgACBTYG3zec8RuDlAp8+f375GQ4gQIBAhYC/2VaoO5MAAQIEogTENmrdhiVAgACBCgGxrVB3JgECBAhECYht1LoNS4AAAQIVAmJboe5MAgQIEIgSENuodRuWAAECBCoExLZC3ZkECBAgECUgtlHrNiwBAgQIVAiIbYW6MwkQIEAgSkBso9ZtWAIECBCoEBDbCnVnEiBAgECUgNhGrduwBAgQIFAhILYV6s4kQIAAgSgBsY1at2EJECBAoEJAbCvUnUmAAAECUQJiG7VuwxIgQIBAhYDYVqg7kwABAgSiBMQ2at2GJUCAAIEKAbGtUHcmAQIECEQJiG3Uug1LgAABAhUCYluh7kwCBAgQiBIQ26h1G5YAAQIEKgTEtkLdmQQIECAQJSC2Ues2LAECBAhUCIhthbozCRAgQCBKQGyj1m1YAgQIEKgQENsKdWcSIECAQJSA2Eat27AECBAgUCEgthXqziRAgACBKAGxjVq3YQkQIECgQkBsK9SdSYAAAQJRAmIbtW7DEiBAgECFgNhWqDuTAAECBKIExDZq3YYlQIAAgQoBsa1QdyYBAgQIRAmIbdS6DUuAAAECFQJiW6HuTAIECBCIEhDbqHUblgABAgQqBMS2Qt2ZBAgQIBAlILZR6zYsAQIECFQIiG2FujMJECBAIEpAbKPWbVgCBAgQqBAQ2wp1ZxIgQIBAlIDYRq3bsAQIECBQISC2FerOJECAAIEoAbGNWrdhCRAgQKBCQGwr1J1JgAABAlECYhu1bsMSIECAQIWA2FaoO5MAAQIEogTENmrdhiVAgACBCgGxrVB3JgECBAhECYht1LoNS4AAAQIVAmJboe5MAgQIEIgSENuodRuWAAECBCoExLZC3ZkECBAgECUgtlHrNiwBAgQIVAiIbYW6MwkQIEAgSkBso9ZtWAIECBCoEBDbCnVnEiBAgECUgNhGrduwBAgQIFAhILYV6s4kQIAAgSgBsY1at2EJECBAoEJAbCvUnUmAAAECUQJiG7VuwxIgQIBAhYDYVqg7kwABAgSiBMQ2at2GJUCAAIEKAbGtUHcmAQIECEQJiG3Uug1LgAABAhUCYluh7kwCBAgQiBIQ26h1G5YAAQIEKgTEtkLdmQQIECAQJSC2Ues2LAECBAhUCIhthbozCRAgQCBKQGyj1m1YAgQIEKgQENsKdWcSIECAQJSA2Eat27AECBAgUCEgthXqziRAgACBKAGxjVq3YQkQIECgQkBsK9SdSYAAAQJRAmIbtW7DEiBAgECFgNhWqDuTAAECBKIExDZq3YYlQIAAgQoBsa1QdyYBAgQIRAmIbdS6DUuAAAECFQJiW6HuTAIECBCIEhDbqHUblgABAgQqBMS2Qt2ZBAgQIBAlILZR6zYsAQIECFQIiG2FujMJECBAIEpAbKPWbVgCBAgQqBAQ2wp1ZxIgQIBAlIDYRq3bsAQIECBQISC2FerOJECAAIEoAbGNWrdhCRAgQKBCQGwr1J1JgAABAlECYhu1bsMSIECAQIWA2FaoO5MAAQIEogTENmrdhiVAgACBCgGxrVB3JgECBAhECYht1LoNS4AAAQIVAmJboe5MAgQIEIgSENuodRuWAAECBCoExLZC3ZkECBAgECUgtlHrNiwBAgQIVAiIbYW6MwkQIEAgSkBso9ZtWAIECBCoEBDbCnVnEiBAgECUgNhGrduwBAgQIFAhILYV6s4kQIAAgSgBsY1at2EJECBAoEJAbCvUnUmAAAECUQJiG7VuwxIgQIBAhYDYVqg7kwABAgSiBMQ2at2GJUCAAIEKAbGtUHcmAQIECEQJiG3Uug1LgAABAhUCYluh7kwCBAgQiBIQ26h1G5YAAQIEKgTEtkLdmQQIECAQJSC2Ues2LAECBAhUCIhthbozCRAgQCBKQGyj1m1YAgQIEKgQENsKdWcSIECAQJSA2Eat27AECBAgUCEgthXqziRAgACBKAGxjVq3YQkQIECgQkBsK9SdSYAAAQJRAmIbtW7DEiBAgECFgNhWqDuTAAECBKIExDZq3YYlQIAAgQoBsa1QdyYBAgQIRAmIbdS6DUuAAAECFQJiW6HuTAIECBCIEhDbqHUblgABAgQqBMS2Qt2ZBAgQIBAlILZR6zYsAQIECFQIiG2FujMJECBAIEpAbKPWbVgCBAgQqBAQ2wp1ZxIgQIBAlIDYRq3bsAQIECBQISC2FerOJECAAIEoAbGNWrdhCRAgQKBCQGwr1J1JgAABAlECYhu1bsMSIECAQIWA2FaoO5MAAQIEogTENmrdhiVAgACBCgGxrVB3JgECBAhECYht1LoNS4AAAQIVAm8nh76/v5+85h0CBAgQIBAp4G+2kWs3NAECBAg8KSC2T2o7iwABAgQiBcQ2cu2GJkCAAIEnBcT2SW1nESBAgECkgNhGrt3QBAgQIPCkgNg+qe0sAgQIEIgUENvItRuaAAECBJ4U+Pnrf/88eaCzCBAgQIBAmoC/2aZt3LwECBAg8LiA2D5O7kACBAgQSBMQ27SNm5cAAQIEHhcQ28fJHUiAAAECaQJim7Zx8xIgQIDA4wJi+zi5AwkQIEAgTUBs0zZuXgIECBB4XOBfkHwasSFrQ3AAAAAASUVORK5CYII=)

#### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#父级透视)父级透视

当X旋转90度后无法看到元素，这时可以控制父级旋转从上看子元素。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7910515.b98ce26d.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    main {
        position: absolute;
        left: 50%;
        top: 50%;
        margin-left: -200px;
        margin-top: -200px;
        width: 400px;
        height: 400px;
        border: solid 5px silver;
        transform-style: preserve-3d;
        transform: perspective(900px) rotateX(-45deg);
    }

    div {
        position: absolute;
        left: 50%;
        top: 50%;
        margin-left: -100px;
        margin-top: -100px;
        width: 200px;
        height: 200px;
        transition: 1s;
    }

    div:nth-child(1) {
        background: #2ecc71;
    }

    main:hover div:nth-child(1) {
        transform: perspective(900px) rotateX(90deg) rotateY(25deg) rotateZ(45deg);
    }
</style>

<main>
	<div></div>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#rotatey)rotateY

按垂直轴旋转，如果旋转90deg 将不可见。

![image-20190902130217250](data:image/png;base64,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)

```text
article div:nth-child(2) {
    transform: rotateY(180deg);
}
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#rotatez)rotateZ

没Z轴旋转元素，效果就是沿X/Y轴的平面旋转。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7824624.322879f9.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        list-style: none;
    }

    body {
        width: 100vw;
        height: 100vh;
        background: #34495e;
    }

    main {
        position: absolute;
        left: 50%;
        top: 50%;
        width: 200px;
        height: 200px;
        background: #f1c40f;
        perspective: 600px;
        transform: perspective(600px) rotateY(35deg);
        transition: 2s;
    }

    body:hover main {
        transform: perspective(600px) rotateY(35deg) rotateZ(160deg);
    }
</style>

<main>
    <div></div>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#rotate)rotate

在X与Y轴平面旋转，效果与使用 `rotateZ` 相同。

![image-20190902130455308](data:image/png;base64,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)

```text
article div:nth-child(2) {
	transform: rotate(90deg);
}
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#rotate3d)rotate3d

同时设置X/Y/Z轴的旋转向量值来控制元素的旋转。

需要同时设置如下四个参数

```text
rotate3d(tx,ty,tz,angle)
```

#### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#只转x轴)只转X轴

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7825021.1b22c5f4.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        list-style: none;
    }

    body {
        width: 100vw;
        height: 100vh;
        background: #34495e;
    }

    main {
        position: absolute;
        left: 50%;
        top: 50%;
        width: 200px;
        height: 200px;
        background: #f1c40f;
        perspective: 600px;
        transform: perspective(600px) rotateY(35deg);
        transition: 2s;
    }

    body:hover main {
        transform: perspective(600px) rotateY(35deg) rotate3d(1, 0, 0, -645deg);
    }
</style>

<main>
	<div></div>
</main>
```

#### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#只转y轴)只转Y轴

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7825124.3529e358.gif)

```text
body:hover main {
	transform: perspective(600px) rotateY(-645deg);
}
```

#### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#只转z轴)只转Z轴

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7825181.9bfa6d74.gif)

#### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#xy旋转)XY旋转

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7825275.8f4b452f.gif)

```text
body:hover main {
	transform: perspective(600px) rotateY(35deg) rotate3d(1, 1, 0, -645deg);
}
```

#### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#xz转换)XZ转换

加入适当的Z向量值，可增加元素沿Z轴旋转的力度。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7825690.7f9d943e.gif)

```text
body:hover main {
	transform: perspective(600px) rotateY(35deg) rotate3d(1, 0, .5, -245deg);
}
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#参数顺序)参数顺序

可以同时设置多个旋转规则，顺序不同结果也会不同。

![image-20190902130625513](http://houdunren.gitee.io/note/assets/img/image-20190902130625513.0bba2c21.png)

```text
article div:nth-child(2) {
	transform: rotateX(30deg) rotateY(30deg);
}
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#旋转文字)旋转文字

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7605104.746a27d4.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
    }

    body {
        height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    main {
        margin: 0 auto;
        width: 400px;
        height: 50vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background: #535c68;
    }

    main div {
        color: #c7ecee;
        cursor: pointer;
    }

    main div strong {
        display: inline-block;
        width: 25px;
        height: 25px;
        margin: 0 3px;
        background: #000;
        border-radius: 50%;
        transition: 2s;
        color: white;
        text-align: center;
        box-shadow: 0 2px 10px rgba(0, 0, 0, .3);
    }

    main div strong:nth-of-type(1) {
        background: #f0932b;
    }

    main div strong:nth-of-type(2) {
        background: #6ab04c;
    }

    main div:hover strong:nth-of-type(1) {
        transform: rotate(360deg);
    }

    main div:hover strong:nth-of-type(2) {
        transform: rotate(-360deg);
    }
</style>

<main>
    <div>
        <strong>h</strong>ou<strong>d</strong>unren.com
    </div>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#电子时钟)电子时钟

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7645507.b3731f7b.gif)

```text
<style>
    body {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        background: #34495e;
    }

    main {
        position: relative;
        width: 400px;
        height: 400px;
        background: #34495e;
        border-radius: 50%;
        box-shadow: 0 0 10px rgba(0, 0, 0, .7);
    }

    main::before {
        position: absolute;
        left: 0;
        top: 0;
        content: '';
        width: 100%;
        height: 100%;
        border-radius: 50%;
        transform: scale(1.2);
        background: radial-gradient(at right, #27ae60, #e67e22, #e74c3c, #e67e22, #27ae60);
        z-index: -1;
    }

    main .line>div {
        position: absolute;
        left: 50%;
        top: 50%;
        width: 10px;
        height: 95%;
        background: white;
    }

    main .line>div:nth-child(1) {
        transform: translate(-50%, -50%) rotate(0deg);
    }

    main .line>div:nth-child(2) {
        transform: translate(-50%, -50%) rotate(30deg);
    }

    main .line>div:nth-child(3) {
        transform: translate(-50%, -50%) rotate(60deg);
    }

    main .line>div:nth-child(4) {
        transform: translate(-50%, -50%) rotate(90deg);
    }

    main .line>div:nth-child(5) {
        transform: translate(-50%, -50%) rotate(120deg);
    }

    main .line>div:nth-child(6) {
        transform: translate(-50%, -50%) rotate(150deg);
    }

    main>div[class="mark"] {
        position: absolute;
        width: 100%;
        height: 100%;
        left: 0%;
        top: 0%;
        background: #34495e;
        border-radius: 50%;
        transform: scale(.8);
    }

    main>.point {
        width: 20px;
        height: 20px;
        background: #e74c3c;
        border-radius: 50%;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        z-index: 2;
    }

    main .hour {
        width: 15px;
        position: absolute;
        height: 25%;
        background: #95a5a6;
        left: 50%;
        bottom: 50%;
        transform: translate(-50%, 0);
    }

    main .minute {
        width: 8px;
        position: absolute;
        height: 35%;
        background: #3498db;
        left: 50%;
        bottom: 50%;
        transform-origin: left bottom;
        transform: translate(-50%, 0) rotate(60deg);
    }

    main .second {
        width: 2px;
        position: absolute;
        height: 35%;
        background: #f1c40f;
        left: 50%;
        bottom: 50%;
        transform-origin: left bottom;
        transform: translate(-50%, 0) rotate(90deg);
    }

    main:hover .second {
        transition: 10s;
        transform: rotate(260deg);
    }

    main .text {
        font-size: 1.2em;
        color: white;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, 20px);
        text-transform: uppercase;
        opacity: .5;
        text-align: center;
    }
</style>

<main>
    <section class="line">
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </section>
    <div class="mark"></div>
    <div class="point"></div>
    <div class="hour"></div>
    <div class="minute"></div>
    <div class="second"></div>
    <div class="text">
        houdunren.com <br>
        向军大叔
    </div>
</main>
```

## [#](http://houdunren.gitee.io/note/css/12 变形动画.html#倾斜操作)倾斜操作

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#skewx)skewX

没X轴倾斜元素

![image-20190902151842782](data:image/png;base64,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)

```text
article div:nth-child(2) {
	transform: skewX(30deg);
}
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#skewy)skewY

沿Y轴倾斜元素

![image-20190902151909797](data:image/png;base64,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)

```text
article div:nth-child(2) {
	transform: skewY(30deg);
}
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#skew)skew

同时设置X/Y轴倾斜操作，不指定第二个参数时Y轴倾斜为零。

![image-20190902152104810](data:image/png;base64,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)

```text
article div:nth-child(2) {
	transform: skew(30deg, 30deg);
}
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#按钮特效)按钮特效

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7636893.3e63a4ce.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
    }

    body {
        background: #34495e;
    }

    main {
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
    }

    main .btn {
        display: block;
        height: 30px;
        width: 150px;
        border: solid 2px #e74c3c;
        background: none;
        color: white;
        position: relative;
        text-align: center;
        display: flex;
        justify-content: center;
        align-items: center;
        overflow: hidden;
        cursor: pointer;
        box-shadow: 0 3px 8px rgba(0, 0, 0, .3);
    }

    main .btn::before {
        transition: all .8s;
        align-self: center;
        content: '';
        position: absolute;
        width: 0;
        height: 100%;
        background: #e74c3c;
        z-index: -1;
        transform: skewX(-45deg);
    }

    main .btn:hover::before {
        width: 200%;
    }
</style>

<main>
    <a class="btn">
        HOUDUNREN
    </a>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#立体按钮)立体按钮

![image-20190906135344963](http://houdunren.gitee.io/note/assets/img/image-20190906135344963.f9a01bf5.png)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    body {
        background: #2c3e50;
        width: 100vw;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .btn {
        color: #ecf0f1;
        text-decoration: none;
        width: 200px;
        height: 40px;
        background: #e74c3c;
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
        transform: skewX(25deg) rotate(-15deg);
        letter-spacing: .5em;
        text-transform: uppercase;
        font-weight: bold;
    }

    .btn::before {
        content: '';
        width: 10px;
        height: 100%;
        left: -10px;
        background: #000;
        position: absolute;
        transform: skewY(-45deg) translate(0, 5px);
    }

    .btn::after {
        content: '';
        width: 100%;
        height: 10px;
        bottom: -10px;
        background: #000;
        position: absolute;
        transform: skewX(-45deg) translate(-5px, 0);
    }
</style>

<a href="" class="btn"> houdunren</a>
```

## [#](http://houdunren.gitee.io/note/css/12 变形动画.html#变形基点)变形基点

使用 `transform-origin` 设置元素的X/YZ操作的基点，用于控制旋转、倾斜等操作。

- 旋转默认以元素中心进行旋转，改变基点后可控制旋转点位置
- 元素移动不受变形基点所影响

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#平面旋转)平面旋转

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7932268.f587aaa0.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    main {
        position: absolute;
        left: 50%;
        top: 50%;
        margin-left: -200px;
        margin-top: -200px;
        width: 400px;
        height: 400px;
        border: solid 5px silver;
    }

    div {
        position: absolute;
        left: 50%;
        top: 50%;
        margin-left: -100px;
        margin-top: -100px;
        width: 200px;
        height: 200px;
        transform-origin: right bottom;
    }

    div:nth-child(1) {
        background: #2ecc71;
    }

    div:nth-child(2) {
        background: #e67e22;
        transition: 1s;
    }

    main:hover div:nth-child(2) {
        transform: rotate(-45deg);
    }
</style>

<main>
    <div></div>
    <div></div>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#倾斜控制)倾斜控制

参考右上角控制倾斜。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7932114.ce3ee8cd.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    main {
        position: absolute;
        left: 50%;
        top: 50%;
        margin-left: -200px;
        margin-top: -200px;
        width: 400px;
        height: 400px;
        border: solid 5px silver;
    }

    div {
        position: absolute;
        left: 50%;
        top: 50%;
        margin-left: -100px;
        margin-top: -100px;
        width: 200px;
        height: 200px;
        transform-origin: top left;
    }

    div:nth-child(1) {
        background: #fff;
    }

    div:nth-child(2) {
        background: #e67e22;
        transition: 1s;
    }

    main:hover div:nth-child(2) {
        transform: skew(45deg);
    }
</style>

<main>
    <div></div>
    <div></div>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#三维旋转)三维旋转

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7932004.12f1c62a.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    main {
        position: absolute;
        left: 50%;
        top: 50%;
        margin-left: -200px;
        margin-top: -200px;
        width: 400px;
        height: 400px;
        border: solid 5px silver;
        transform-style: preserve-3d;
        transform: perspective(900px) rotateY(95deg);
    }

    div {
        position: absolute;
        left: 50%;
        top: 50%;
        margin-left: -100px;
        margin-top: -100px;
        width: 200px;
        height: 200px;
        transform-origin: center center 200px;
    }

    div:nth-child(1) {
        background: #2ecc71;
    }

    div:nth-child(2) {
        background: #e67e22;
        transition: 1s;
    }

    main:hover div:nth-child(2) {
        transform: rotateY(360deg);
    }
</style>

<main>
    <div></div>
    <div></div>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#新年贺卡)新年贺卡

下面是通过设置基点来制作贺卡的效果。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7939019.ed7152ba.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    body {
        width: 100vw;
        height: 100vh;
        background: #34495e;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    main {
        width: 300px;
        height: 200px;
        transform-style: preserve-3d;
        transform: perspective(600px) rotateX(35deg) rotateY(15deg);
    }

    .card {
        width: 300px;
        height: 200px;
        background: #e67e22;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 3em;
        color: whitesmoke;
        position: relative;

    }

    .card::before,
    .card::after {
        transition: 1s;
        background: #e74c3c;
        line-height: 4em;
    }

    .card::before {
        content: '新年';
        width: 150px;
        height: 100%;
        left: 0px;
        top: 0;
        text-align: right;
        position: absolute;
        transform-origin: left bottom;
    }

    .card::after {
        content: '快乐';
        width: 150px;
        height: 100%;
        left: 150px;
        top: 0;
        position: absolute;
        transform-origin: right bottom;
    }

    .card:hover::before {
        transform: rotateY(-179deg);
    }

    .card:hover::after {
        transform: rotateY(179deg);
    }
</style>

<main>
    <div class="card">houdunren</div>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#动感菜单)动感菜单

为了让大家清楚理解，下面把思路给大家解析一下。

![image-20190905200803607](http://houdunren.gitee.io/note/assets/img/image-20190905200803607.95e393c8.png)

![image-20190909154507295](http://houdunren.gitee.io/note/assets/img/image-20190909154507295.cfc5d8b8.png)

#### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#父级有宽度)父级有宽度

设置父级ul有宽度，每层都是居中对齐。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-8015150.745be0aa.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        list-style: none;
    }

    body {
        width: 100vw;
        height: 100vh;
        background: #2c3e50;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    nav {
        width: 400px;
        height: 400px;
        background: transparent;
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;

    }

    nav::after {
        content: '向军老师';
        color: #ecf0f1;
        position: absolute;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 2em;
        font-weight: bold;
        text-shadow: 3px 3px 0px #34495e;
        z-index: 1;
    }

    nav::before {
        content: '';
        width: 200px;
        height: 200px;
        background: #e74c3c;
        border-radius: 50%;
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        z-index: 1;
    }

    nav:hover ul {
        transform: scale(1);
    }

    ul {
        width: 300px;
        height: 300px;
        transform: scale(0);
        transition: .5s;
    }

    ul li {
        width: 80px;
        height: 80px;
        background: #e74c3c;
        border-radius: 50%;
        position: absolute;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 2.5em;
        color: white;
        transition: 1s;
        transform-origin: 150px 150px;
        box-shadow: 0 0 15px rgba(0, 0, 0.8);
    }

    ul li span {
        transition: 1s;
    }

    nav:hover li:nth-child(1) {
        transform: rotate(40deg);
    }

    nav:hover li:nth-child(1)>span {
        transform: rotate(1040deg);
    }

    nav:hover li:nth-child(2) {
        transform: rotate(80deg);
    }

    nav:hover li:nth-child(2)>span {
        transform: rotate(1000deg);
    }

    nav:hover li:nth-child(3) {
        transform: rotate(120deg);
    }

    nav:hover li:nth-child(3)>span {
        transform: rotate(960deg);
    }

    nav:hover li:nth-child(4) {
        transform: rotate(160deg);
    }

    nav:hover li:nth-child(4)>span {
        transform: rotate(720deg);
    }

    nav:hover li:nth-child(5) {
        transform: rotate(200deg);
    }

    nav:hover li:nth-child(5)>span {
        transform: rotate(880deg);
    }

    nav:hover li:nth-child(6) {
        transform: rotate(240deg);
    }

    nav:hover li:nth-child(6)>span {
        transform: rotate(1680deg);
    }

    nav:hover li:nth-child(7) {
        transform: rotate(280deg);
    }

    nav:hover li:nth-child(7)>span {
        transform: rotate(1920deg);
    }

    nav:hover li:nth-child(8) {
        transform: rotate(320deg);
    }

    nav:hover li:nth-child(8)>span {
        transform: rotate(2200deg);
    }

    nav:hover li:nth-child(9) {
        transform: rotate(360deg);
    }

    nav:hover li:nth-child(9)>span {
        transform: rotate(2520deg);
    }
</style>

<nav>
    <ul>
        <li><span><i class="fa fa-address-book" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-adjust" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-bars" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-book" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-bug" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-compress" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-ban" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-beer" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-bus" aria-hidden="true"></i></span></li>
    </ul>
</nav>
```

#### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#父级无宽度)父级无宽度

下面代码父级 UL 没有设置宽度，而是使用边框撑开了空间的效果，基本原理和上面一样。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7667552.863eb27b.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        list-style: none;
    }

    body {
        background: #34495e;
    }

    nav {
        position: absolute;
        margin: 0 auto;
        left: 50%;
        top: 50%;
        width: 180px;
        height: 180px;
        background: #34495e;
        border-radius: 50%;
        text-align: center;
        line-height: 180px;
        color: #2c3e50;
        font-weight: bold;
        font-size: 2em;
        background: #f1c40f;
        box-shadow: 0 0 15px rgba(0, 0, 0, .5);
        cursor: pointer;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    nav strong {
        position: absolute;
    }

    nav:hover ul {
        transform: scale(1.3);
    }

    ul {
        transform: scale(0);
        border: 150px solid transparent;
        transition: .5s;
        cursor: pointer;
        z-index: -1;
    }

    ul li {
        position: absolute;
        top: -100px;
        left: -100px;
        width: 50px;
        height: 50px;
        background: #e67e22;
        border-radius: 50%;
        display: flex;
        justify-content: center;
        align-content: center;
        line-height: 1.5em;
        transition: all 1s;
        transform-origin: 100px 100px;
        box-shadow: 0 0 15px rgba(0, 0, 0, .8);
    }

    ul li span {
        transition: all 1s;
    }

    nav:hover ul li:nth-child(1) {
        transform: rotate(40deg);
    }

    nav:hover ul li:nth-child(1) span {
        transform: rotate(1040deg);
    }

    nav:hover ul li:nth-child(2) {
        transform: rotate(80deg);
    }

    nav:hover ul li:nth-child(2) span {
        transform: rotate(1000deg);
    }

    nav:hover ul li:nth-child(3) {
        transform: rotate(120deg);
    }

    nav:hover ul li:nth-child(3) span {
        transform: rotate(1680deg);
    }

    nav:hover ul li:nth-child(4) {
        transform: rotate(160deg);
    }

    nav:hover ul li:nth-child(4) span {
        transform: rotate(560deg);
    }

    nav:hover ul li:nth-child(5) {
        transform: rotate(200deg);
    }

    nav:hover ul li:nth-child(5) span {
        transform: rotate(520deg);
    }

    nav:hover ul li:nth-child(6) {
        transform: rotate(240deg);
    }

    nav:hover ul li:nth-child(6) span {
        transform: rotate(480deg);
    }

    nav:hover ul li:nth-child(7) {
        transform: rotate(280deg);
    }

    nav:hover ul li:nth-child(7) span {
        transform: rotate(440deg);
    }

    nav:hover ul li:nth-child(8) {
        transform: rotate(320deg);
    }

    nav:hover ul li:nth-child(8) span {
        transform: rotate(400deg);
    }

    nav:hover ul li:nth-child(9) {
        transform: rotate(360deg);
    }

    nav:hover ul li:nth-child(9) span {
        transform: rotate(720deg);
    }
</style>


<nav>
    向军大叔
    <ul>
        <li><span><i class="fa fa-address-book" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-adjust" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-bars" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-book" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-bug" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-compress" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-ban" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-beer" aria-hidden="true"></i></span></li>
        <li><span><i class="fa fa-bus" aria-hidden="true"></i></span></li>
    </ul>
</nav>
```

## [#](http://houdunren.gitee.io/note/css/12 变形动画.html#透视景深)透视景深

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#perspective)perspective

- 使用 `perspective` 来控制元素的透视景深
- `perspective` 规则为舞台元素控制景深， `perspective` 属性为控制单个元素

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#舞台透视)舞台透视

`perspective` 规则用于将父级整个做为透视元素，会造成里面的每个子元素的透视是不一样的。就像现实中摆一排杯子，是使用统一透视的，每个杯子的透视不一样，造成有大有小。

![image-20190902164314985](data:image/png;base64,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)

```text
<style>
    article {
        margin: 0 auto;
        margin-top: 150px;
        width: 400px;
        height: 200px;
        position: relative;
        border: solid 5px silver;
        perspective: 200px;
    }

    article div {
        width: 100px;
        height: 100px;
        background: blueviolet;
        box-sizing: border-box;
        margin-right: 80px;
        float: left;
        transform: rotateY(60deg);
    }
</style>

<article>
	<div></div>
	<div></div>
</article>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#单独透视)单独透视

`perspective` 函数用于为元素设置单独透视，下面是为元素单独设置透视参数，每个元素的透视效果是一样的。

![image-20190902164423476](data:image/png;base64,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)

```text
article div {
    width: 100px;
    height: 100px;
    background: blueviolet;
    box-sizing: border-box;
    margin-right: 80px;
    float: left;
    transform: perspective(100px) rotateY(60deg);
}
```

## [#](http://houdunren.gitee.io/note/css/12 变形动画.html#_3d透视)3D透视

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#transform-style)transform-style

使用 `transform-style` 用于控制3d透视。

- 应用于舞台即变形元素的父级元素
- 设置 `overflow:visible` 时 `preserve-3d` 才无效

| 选项        | 说明       |
| ----------- | ---------- |
| flat        | 2D平面舞台 |
| preserve-3d | 3D透视舞台 |

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#效果体验)效果体验

下面是设置`3D`舞台后看到的效果。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7770216.9f7c32fd.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    body {
        background: #34495e;

    }

    main {
        position: relative;
        width: 100vw;
        height: 100vh;
    }

    div {
        position: absolute;
        left: 50%;
        top: 50%;
        height: 200px;
        width: 200px;
        transition: 1s;
        background: #e67e22;
        transform-style: preserve-3d;

    }

    div img {
        height: 80%;
        transform: perspective(500px) translateZ(100px);
    }

    div:hover {
        transform: perspective(600px) rotateY(50deg);
    }
</style>

<main>
    <div>
        <img src="5.jpg" alt="">
    </div>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#三维图集)三维图集

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7838254.e56c8d56.gif)

```text
<style>
    body {
        background: #34495e;
    }

    main {
        position: absolute;
        width: 400px;
        height: 200px;
        left: 50%;
        top: 50%;
        transform-style: preserve-3d;
        transform-origin: center center -300px;
        transform: translate(-50%, -50%) rotateX(-45deg);
        transition: 2s;
    }

    body:hover main {
        transform: translate(-50%, -50%) rotateX(-45deg) rotateY(900deg);
    }

    div {
        position: absolute;
        width: 100%;
        height: 100%;
        transform-origin: center center -300px;
        overflow: hidden;
    }

    div img {
        height: 100%;
    }

    div:nth-child(1) {
        transform: rotateY(60deg);
    }

    div:nth-child(2) {
        transform: rotateY(120deg);
    }

    div:nth-child(3) {
        transform: rotateY(180deg);
    }

    div:nth-child(4) {
        transform: rotateY(240deg);
    }

    div:nth-child(5) {
        transform: rotateY(300deg);
    }

    div:nth-child(6) {
        transform: rotateY(360deg);
    }
</style>

<main>
    <div>
        <img src="5.jpg" alt="">
    </div>
    <div>
        <img src="1.jpg" alt="">
    </div>
    <div>
        <img src="3.jpg" alt="">
    </div>
    <div>
        <img src="5.jpg" alt="">
    </div>
    <div>
        <img src="1.jpg" alt="">
    </div>
    <div>
        <img src="3.jpg" alt="">
    </div>
</main>
```

## [#](http://houdunren.gitee.io/note/css/12 变形动画.html#观看视角)观看视角

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#perspective-origin)perspective-origin

`perspective-origin`用于控制视线的落点，就像我们眼睛看物体时的聚焦点。可以理解眼镜看物体的位置，比如看一台汽车，是在看车头左边看还是车头右边看。

需要设置 `perspective` 透视后才可以看到效果。

- 一般设置在舞台元素上来控制子元素

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#位置参数)位置参数

| 取值     | 说明                                                         |
| :------- | :----------------------------------------------------------- |
| *x-axis* | 定义该视图在 x 轴上的位置。默认值：50%。可能的值：left、center、right、length、% |
| *y-axis* | 定义该视图在 y 轴上的位置。默认值：50%。可能的值：top、center、bottom、length、% |

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#效果体验-2)效果体验

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-8191457.7ad994e0.gif)

```text
<style>
    body {
        background: #2c3e50;
        display: flex;
        width: 100vw;
        height: 100vh;
        justify-content: center;
        align-items: center;
    }

    main {
        border: solid 2px silver;
        width: 400px;
        height: 200px;
        transform-style: preserve-3d;
        transform: rotateY(65deg);
        perspective-origin: right bottom;
        perspective: 900px;
        transition: 2s;
    }

    body:hover main {
        perspective-origin: 1200% bottom;
        /* transform: rotateY(-65deg); */
    }

    div {
        position: absolute;
        width: 200px;
        height: 200px;
        transform: rotateY(60deg);
        overflow: hidden;
    }

    div>img {
        height: 100%;
    }

    div:nth-child(1) {
        background: #e67e22;
    }

    div:nth-child(2) {
        background: #27ae60;
        transform: rotateY(60deg) translateZ(-200px);
    }
</style>
<main>
    <div><img src="3.jpg" alt=""></div>
    <div><img src="5.jpg" alt=""></div>
</main>
```

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#立方体)立方体

![image-20190906230252608](http://houdunren.gitee.io/note/assets/img/image-20190906230252608.e4e08e3d.png)

效果如下

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-7784965.483715b7.gif)

```text
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        list-style: none;
    }

    body {
        background: #34495e;
    }

    main {
        position: absolute;
        left: 50%;
        top: 50%;
        width: 200px;
        height: 200px;
        transform-style: preserve-3d;
        transform-origin: 50% 50% 50px;
        transform: translate(-50%, -50%) rotateY(0deg);
        transition: 2s;
    }

    main:hover {
        transform: translate(-50%, -50%) rotate3d(1, 1, 0, 180deg);
    }

    div {
        position: absolute;
        width: 200px;
        height: 200px;
        background: #000;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 4em;
    }

    div:nth-child(1) {
        transform-origin: right;
        background: #1abc9c;
        transform-origin: bottom;
        transform: translateY(-200px) rotateX(-90deg);
        opacity: .8;
    }

    div:nth-child(2) {
        transform-origin: right;
        background: #27ae60;
        transform-origin: top;
        transform: translateY(200px) rotateX(90deg);
        opacity: .8;
    }

    div:nth-child(3) {
        transform-origin: bottom;
        background: #e67e22;
        transform-origin: right;
        transform: translateX(-200px) rotateY(90deg);
        opacity: .8;
    }

    div:nth-child(4) {
        transform-origin: top;
        background: #8e44ad;
        transform-origin: left;
        transform: translateX(200px) rotateY(-90deg);
        opacity: .8;
    }

    div:nth-child(5) {
        transform-origin: left bottom;
        background: #ecf0f1;
        opacity: .8;
    }

    div:nth-child(6) {
        transform-origin: left bottom;
        background: #ecf0f1;
        opacity: .5;
        transform: translateZ(200px);
    }
</style>

<main>
    <div>1</div>
    <div>2</div>
    <div>3</div>
    <div>4</div>
    <div>5</div>
    <div>后盾人</div>
</main>
```

## [#](http://houdunren.gitee.io/note/css/12 变形动画.html#隐藏背面)隐藏背面

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#backface-visibility)backface-visibility

使用 `backface-visibility` 用于控制是否可以看到元素的背面。

- 一般设置在元素上而不是舞台元素上
- 需要舞台元素（父级元素）设置 `transform-style: preserve-3d`

| 选项    | 说明     |
| ------- | -------- |
| visible | 背面可见 |
| hidden  | 背面隐藏 |

### [#](http://houdunren.gitee.io/note/css/12 变形动画.html#翻转卡片)翻转卡片

下面使用隐藏背面与透视技术制作的翻转卡片效果。

![Untitled](http://houdunren.gitee.io/note/assets/img/Untitled-8212174.f8db6c8c.gif)

```text
<script src='https://code.jquery.com/jquery-3.3.1.slim.min.js'></script>
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css">
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    main {
        position: absolute;
        width: 100vw;
        height: 100vh;
        transition: 2s;
        transform-style: preserve-3d;
    }

    main.login {
        transform: perspective(900px) rotateY(0deg);
    }

    main.register {
        transform: perspective(900px) rotateY(180deg);
    }

    div {
        position: absolute;
        width: 100%;
        height: 100%;
        font-size: 5em;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        backface-visibility: hidden;
        transition: 2s;
        text-transform: uppercase;
        color: white;
    }

    div span {
        text-transform: lowercase;
        letter-spacing: .2em;
        font-size: .2em;
        color: #2c3e50;
    }

    div:nth-child(1) {
        background: #2ecc71;
        transform: rotateY(0deg);
    }

    div:nth-child(2) {
        background: #e74c3c;
        transform: rotateY(180deg);
    }

    nav {
        position: absolute;
        width: 100%;
        height: 100%;
        z-index: 99;
        text-align: center;
        display: flex;
        align-items: flex-end;
        justify-content: center;
        padding-bottom: 30px;
    }

    nav a {
        padding: 10px;
        text-decoration: none;
        font-size: 1em;
        background: #000;
        color: white;
        margin-right: 10px;
        cursor: pointer;
        left: 0;
        top: 0;
    }
</style>

<main>
    <div>
        <i class="fa fa-home" aria-hidden="true"></i>
        login
        <span>houdunren.com</span>
    </div>
    <div>
        <i class="fa fa-user" aria-hidden="true"></i>
        register
        <span>houdunren.com</span>
    </div>
</main>
<nav>
    <a href="javascript:;" onclick="change('login')">登录</a>
    <a href="javascript:;" onclick="change('register')">注册</a>
</nav>
<script>
    function change(t) {
        switch (t) {
            case 'login':
                $("main").removeClass().addClass('login');
                break;
            case 'register':
                $("main").removeClass().addClass('register');
                break;
        }
    }
</script>
```









---



### 16.css的小知识

当css的一条语句中出现一个错误，那么整个语句将会失效



