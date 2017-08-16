# mitkey.github.io-hexo
 	当前项目是部署到 github

　　部署个人博客工具

　　hexo [官方文档](https://hexo.io/zh-cn/docs)

　　next [主题文档](http://theme-next.iissnan.com)


## 部署 ##

	hexo g -d
	
　　首先会生成 html 静态文件到 public 目录，然后发布到 git。

## 本地预览 ##

	hexo s

　　运行该指令，本地会启动一个 web 服务器。访问 [http://localhost:4000](http://localhost:4000 "本地服务") 即可预览

## 创建新文章 ##

	hexo new [文章标题]

　　运行该指令会创建一个指定 <font size="4px" color="red">文章标题.md</font> 的文件到 <font size="4px" color="red">source/_post</font> 目录

## next 主题添加文章摘录 ##

	在需要摘录截止下一行加上 <!-- more -->