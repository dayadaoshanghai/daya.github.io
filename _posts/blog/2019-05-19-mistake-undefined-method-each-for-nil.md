---
layout: post
title: 错误：undefined method 'each' for nil:NilClass       
category: blog
description:        
---

**错误截图**  
[![EjnInH.md.png](https://s2.ax1x.com/2019/05/19/EjnInH.md.png)](https://imgchr.com/i/EjnInH)

**解决办法**  
一般这种报错都是，jobs_controller_rb中index这个函数写的不对，本次错误  
```   
#错误代码
def index
    @job = Job.all
  end 
```   
正确代码   
```
def index
    @jobs = Job.all
  end 
```   
改完后代码正常运行  



