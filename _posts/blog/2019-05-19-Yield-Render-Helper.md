---
layout: post
title: Yield, Render, Helper的作用      
category: blog
description:        
--- 

 
## yield作用     
Controller在处理View的时候，并不是单纯的取用index.html.erb，而是先调用预设layout档案中的内容（app/views/layouts/apllication.html.erb），然后把index.html.erb中的内容填到<%= yield %>   

#### 预设版型  
前面说的预设版型是app/views/layouts/application.html.erb，其实不完全正确，真正的预设版型是与[controller]同名的版型。举例来说，有个Controller叫做 JobsController ，其实它先找的是app/views/layouts 下面的job.html.erb，如果找不到才找application.html.erb   

## Partial render局部渲染   
局部渲染是一种在rails专案中常见的代码代理方法之一  
比如 `<%= render "form" %> `   
完整的写法 `<%= render partial: "form"`    
这行代码的意思是去找同目录下_form这个档案，并把这个档案安插在这个地方    

## View Helper也是用来整理代码常用的方法  
例如平常写的 `link_to` `image_tag` `form_for`，它都是一种View Helper 


### 下面这段代码中ruby语言部分如何理解？  
``` 
  <head>
    <title>MyCandidates</title>
    <%= csrf_meta_tags %>
    <%= stylesheet_link_tag    'application', media: 'all', 'data-turbolinks-track': 'reload' %>
    <%= javascript_include_tag 'application', 'data-turbolinks-track': 'reload' %>
  </head> 
``` 


   



