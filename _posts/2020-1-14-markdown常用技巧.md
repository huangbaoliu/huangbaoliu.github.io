---
layout:     post
title:      markdown常用技巧
date:       2021-1-14
author:     huangbaoLiu
header-img: img/post-bg-desk.jpg
catalog: true
tags:
    - Tool skills
---
## 基本技巧

&ensp;以下符号均为英文符号。

* **目录** 一般是在首行顶格用`[TOC]`

* **标题** 一般在每行定格处用n个连续的 **#**，例如一级标题用一个`#`，二级标题用`##`，以此类推，最多六级标题

* **强调** 两个``*``或``-``代表加粗，一个``*``或``-``代表斜体，``~~``代表删除。
如在需要加粗文字段首尾处各用  ```**```

* **换行**：

1. 方法1: 连续两个以上空格+回车

2. 方法2：使用html语言换行标签： `<br>`  

* **首行缩进** 两个字符：(每个表示一个空格，连续使用两个即可）

1. ```&ensp;``` 半角的空格

2. ```&emsp;``` 全角的空格

* **插入链接**

```
[链接描述](链接地址)如：

[markdown常用技巧](https://www.w3cschool.cn/lme/ckdj1sng.html)
```

* **插入图片**

``` html
![随意，文内不显示](图片网址或地址)如：

![](https://image-static.segmentfault.com/100/909/1009091425-5ad41bf3653c7)
```
* **无序列表** 在行首使用-、+和*作为列表标记

* 使用[^]来定义脚注：

* **引用** 以``>``来表示，引用中支持多级引用、标题、列表、代码块、分割线等常规语法。

* **代码** :分为行内代码和代码块。

  1.行内代码在首尾处使用1个 **`**  标识，可嵌入文字中

  2.代码块使用4个空格或在首尾处用3个 **`** 标识。
* **代码语法高亮** 在 **```** 后面加上空格和语言名称即可

* **表格**
&emsp;&emsp;表格对齐格式
  1.居左：`:----`
  2.居中：`:----:或-----`
  3.居右：`----:`
```  
|标题|标题|标题|
|:---|:---:|---:|
|居左测试文本|居中测试文本|居右测试文本|
|居左测试文本1|居中测试文本2|居右测试文本3|
|居左测试文本11|居中测试文本22|居右测试文本33|
|居左测试文本111|居中测试文本222|居右测试文本333|
```

## 内嵌HTML功能
&emsp;&emsp;**Markdown** 是一种可以使用普通文本编辑器编写的标记语言，通过类似HTML的标记语法，它可以使普通文本内容具有一定的格式。但是它本身是不支持修改字体、字号与颜色等功能的！接下来要讲的功能就需要使用内嵌HTML的方法

* **字体、字号与颜色**

``` html
<font size=5> 字体、字号和颜色 </font>
<font face="黑体"> 我是黑体字 </font>
<font color=#0099ff size=7 face="黑体">  color=#0099ff size=7 face="黑体"  </font>
<font color=#00ffff size=20> color=#00ffff </font>
<font color=gray size=20> color=gray </font>
```
* 文本对齐

``` html
<p align="left">居左文本</p>
<p align="center">居中文本</p>
<p align="right">居右文本</p>
```
* 下划线

`<u>下划线文本</u>`

* 注释（采用如下格式）

` <!--想要注释掉的内容--> `

* 指定插入图片大小以及位置和图标

``` html
<center>
<img src="https://ws1.sinaimg.cn/large/007bc5ofly1fusn6n3k2gj30sc0ep0u7.jpg" width="75%" height="75%" />
Figure 1. Semantic Segmentation
</center>
```
#### 进阶

* [Kramdown](http://gohom.win/2015/11/06/Kramdown-note/)
