---
title: Reids批量删除key
tags:
  - Dev
  - Life
categories:
  - Diary
comments: false
date: 2019-05-06 15:07:25
updated: 2019-05-06 15:07:25
password:
---

项目需求进行一段时间后，需要删除测试期间产生的某部分 key。
比如需要删除 account 为前缀的全部 key

-- 拼刺刀

使用 linux 的 xargs

	redis-cli keys account* | xargs redis-cli del