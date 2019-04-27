---
layout: post
title: install puma error
category: blog
description: 手动安装，然后更改gemfile  
---


**报错信息截图**  
[![EEWQCF.md.png](https://s2.ax1x.com/2019/04/23/EEWQCF.md.png)](https://imgchr.com/i/EEWQCF)  

**解法**   
手动安装puma 
命令行输入 `gem install puma ` 
结果如下： 
[![EEW1gJ.md.png](https://s2.ax1x.com/2019/04/23/EEW1gJ.md.png)](https://imgchr.com/i/EEW1gJ)    
因为安装的是puma版本是3.12.1，修改gemfile  
`gem 'puma', '~> 3.12.1' `   

然后执行 `bundle install`   
顺利解决  
[![EEWjGF.md.png](https://s2.ax1x.com/2019/04/23/EEWjGF.md.png)](https://imgchr.com/i/EEWjGF)


  

  

 






