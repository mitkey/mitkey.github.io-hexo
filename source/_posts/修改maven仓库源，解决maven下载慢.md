---
title: 修改maven仓库源，解决maven下载慢
tags:
  - Dev
  - Maven
categories:
  - Maven
comments: false
date: 2019-04-27 16:39:03
updated: 2019-04-27 16:39:03
password:
---

使用 maven 下载依赖时，速度慢的不要不要的。现有需求是加快下载速度。
默认已按照 maven 环境

<!-- more -->
	
## how？##

> 进入 **%install path%/confg** 目录下,打开 settings.xml 进行编译


在第二级节点下(根节点 settings 的下一级)找到 mirrors 节点，在 mirrors 下添加子节点

	<mirror>  
      <id>alimaven</id>  
      <mirrorOf>central</mirrorOf>  
      <name>aliyun maven</name>  
      <url>http://maven.aliyun.com/nexus/content/repositories/central/</url>  
    </mirror>

已修改的 settings.xml 的部分内容如下

	<!-- mirrors
	 | This is a list of mirrors to be used in downloading artifacts from remote repositories.
	 |
	 | It works like this: a POM may declare a repository to use in resolving certain artifacts.
	 | However, this repository may have problems with heavy traffic at times, so people have mirrored
	 | it to several places.
	 |
	 | That repository definition will have a unique id, so we can create a mirror reference for that
	 | repository, to be used as an alternate download site. The mirror site will be the preferred
	 | server for that repository.
	 |-->
	<mirrors>

		<!-- mirror
		 | Specifies a repository mirror site to use instead of a given repository. The repository that
		 | this mirror serves has an ID that matches the mirrorOf element of this mirror. IDs are used
		 | for inheritance and direct lookup purposes, and must be unique across the set of mirrors.
		 |
		<mirror>
			<id>mirrorId</id>
			<mirrorOf>repositoryId</mirrorOf>
			<name>Human Readable Name for this Mirror.</name>
			<url>http://my.repository.com/repo/path</url>
		</mirror>
		-->
	 
		<mirror>  
			<id>alimaven</id>  
			<mirrorOf>central</mirrorOf>  
			<name>aliyun maven</name>  
			<url>http://maven.aliyun.com/nexus/content/repositories/central/</url>  
		</mirror> 
	</mirrors>