---
layout: post
title: rails s失败端口localhost:3000被占用     
category: blog
description: 杀死占用的进程就行了        
---

**错误截图**  
![EfhOZ8.png](https://s2.ax1x.com/2019/05/11/EfhOZ8.png)

**解决办法**  
终端输入：`lsof -wni tcp:3000`
![Ef4CMq.png](https://s2.ax1x.com/2019/05/11/Ef4CMq.png)  

杀死占用进程  
终端输入： `kill 9 PID`  

再次输入 `rails s`就成功了  
