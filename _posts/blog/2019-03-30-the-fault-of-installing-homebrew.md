---
layout: post
title: 搭建环境
category: blog
description:  rails搭建环境
---

homebrew安装失败 
**报错信息截图**  
[![ABtVb9.md.png](https://s2.ax1x.com/2019/03/30/ABtVb9.md.png)](https://imgchr.com/i/ABtVb9)  

**Google搜索方法**   
>>>  
解决办法（分两种）
	1.	网络上往往都会说这是由于大文件造成的提交或者拉取失败。 但是，经过本人测试。如果 errno 56，那么应该是有大文件或者提交缓存方面的问题。 而 errno 54 则不是这个问题。对于 56 错误的解决方式与网络上大部分文章的一致。 都是增大缓存配置，比如下面就是配置提交缓存为 500M。
git config http.postBuffer 524288000
git config https.postBuffer 524288000


还是出现错误，错误截图   
![AB0VbD.png](https://s2.ax1x.com/2019/03/30/AB0VbD.png)  

放弃睡觉 
第二天一早6：50开始重新安装，安装成功，发现下载速度快了很多，原来是网速太慢，导致安装到一半就挂了。   
所以得赶快加快网速






