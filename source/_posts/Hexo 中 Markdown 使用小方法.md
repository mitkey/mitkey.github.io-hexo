---
title: Hexo 中 Markdown 使用小方法
tags:
  - Dev
  - Life
categories:
  - Diary
comments: false
date: 2017-08-15 21:41:34
updated: 2017-08-15 21:41:34
---

关于 Hexo 中 Markdown 使用的小方法，有些语法 Markdown 自带的也支持。请自行测试

<!-- more -->

##  位置居中定制
{% note default %} 
	{% codeblock %} <center>内容</center>> {% endcodeblock %}
	
	效果如下
	<center>我是已经设置为居中的文本</center>
	我是默认的文本，默认左边对齐


{% endnote %}


## 定制图片

{% note default %}

在 hexo 中图片插入默认是居中的。

- [hexo资源引用(引用图片)](https://hexo.io/zh-cn/docs/asset-folders.html#相对路径引用的标签插件)
- [hexo标签插件内置](https://hexo.io/zh-cn/docs/tag-plugins.html#Image)  ---> 没用过
- [next内置](http://theme-next.iissnan.com/tag-plugins.html#full-width-image)
- [html方式] ----> 下面使用的全部是这种方式
- [markdown自带]  ---> 这里就不说了

<!-- 生成效果的代码块 -->
{% codeblock %}
	<img src="demo.jpg" title="默认大小" />
	<img src="demo.jpg" width="150px" height="150px" title="固定大小(150px 150px)" />
	<img src="demo.jpg" width="50%" height="50%" title="百分比大小(50%)" />
{% endcodeblock %}

<img src="demo.jpg" title="默认大小" />
<img src="demo.jpg" width="150px" height="150px" title="固定大小(150px 150px)" />
<img src="demo.jpg" width="50%" height="50%" title="百分比大小(50%)" />

{% endnote %}


## 字体大小颜色定制

{% note default %}
	{% codeblock %} <center><font size='9px' color='#01B468' face='华文琥珀'>字体大小颜色测试</font></center> {% endcodeblock %}
	<center><font size='9px' color='#01B468' face='华文琥珀'>字体大小颜色测试</font></center>
{% endnote %}


## 首行缩进

{% note default %}
　　我是已经首行缩进的2个字符

	实现方式为输入法切换到全角模式，敲击2下 space 键
	<img src="2017-08-16_181203.png" title="搜狗输入法的状态栏"/>
{% endnote %}


