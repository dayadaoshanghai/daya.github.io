---
layout: post
title: rails101 login fault
category: blog
description:  devise的问题
---


**报错信息截图**  
[![A5Ry2F.md.png](https://s2.ax1x.com/2019/04/09/A5Ry2F.md.png)](https://imgchr.com/i/A5Ry2F)  

**刘老师远程解决办法**   
>>>  
*问题原因*：数据库紊乱，devise没有安装成功，user也没有创建成功   

*解决途径*：使用rake三兄弟  
rake db:drop 删除数据库  
rake db:create 新建数据库  
rake db:migrate 更改数据库  

重新创建数据库后可以正常登录了，问题解决  
![A5RhUx.png](https://s2.ax1x.com/2019/04/09/A5RhUx.png)






