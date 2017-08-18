---
title: Hexo文章加密访问
tags:
  - Hexo
categories:
  - Diary
comments: false
date: 2017-08-17 11:52:13
updated: 2017-08-17 11:52:13
password: admin
---

如何对 hexo 创建的文章进行访问加密呢？实现方式下文再说。当然因为 hexo 是生成的静态页面是未和服务器交互的，该实现加密方式的密码在源码中是能找到的，因此这种加密安全性是不高，只能拦截住一小部分人，当然聊胜于无吗，玩玩而已。

访问密码为 <b style="color:red">admin</b>

<!-- more --->

## 效果图

访问设置了加密的文章链接，在 google 下弹出
{% asset_img  2017-08-17_120857.png 效果图 %}


## 实现方式

{% note %}
打开 next 主题的 <font color="red">layout/_partials/header.swig</font> 文件进行编译。在该文件头部添加如下代码
{% endnote %}

```
	<script>
		(function() {
			if ('{{ page.password }}'){
				if (prompt('请输入文章密码') !== '{{ page.password }}'){
					alert('密码错误！');
					history.back();
				}
			}
		})();
	</script>
```




{% note %}
下面为 header.swig 文件的修改后的内容
<img src="2017-08-18_113243.png" title="header.swig文件" />
{% endnote %}

{% note %}
之后为需要加密访问的文章中配置 password 的值，该 password 的值对应上面 js 中 page.password 值。下面为文章配置的访问密码为 admin
<img src="2017-08-18_114037.png" title="文章md文件">
{% endnote %}

{% note %}
最好是在 <font color="red">scaffolds/post.md</font> 模板中添加 password 配置，这样后面创建的文件默认都有 password 属性。效果图如下，该 post 模板默认配置的访问密码是空的
<img src="2017-08-18_114449.png" title="post模板配置">
{% endnote %}


{% note default %}
原文 [http://blog.csdn.net/qq_33699981/article/details/72716951#t23](http://blog.csdn.net/qq_33699981/article/details/72716951#t23)
{% endnote %}

