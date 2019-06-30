---
layout: post
title: db/migrate/XXX_add_devise_to_user.rb冲突  
category: blog
description:  
---


**报错信息截图**  
  ![ZlHZTJ.png](https://s2.ax1x.com/2019/06/30/ZlHZTJ.png) 

**Google搜索方法**   
>>>    
>>> 
[解法链接](http://xbthh-blog.logdown.com/posts/1233486-20161221)  

**解决步骤**   
	1.	remove "devise_for :users" in routes.rb
	2.	run the command "rails destroy scaffold User"
	3.	remove add_devise_to_users file in db/migrate
	4.	re-run "rails generate devise User" to create a brand new devise_create_users file in db/migrate
	5.	re-run "rake db:migrate"


  

 






