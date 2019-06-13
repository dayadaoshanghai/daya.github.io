---
layout: post
title: 搭建网站步骤之——step1        
category: blog
description: step0基础建设             
--- 

### Part1 安装Bootstrap   
1. 修改Gemfile 
加入`gem 'bootstrap-sass'`   

2. 执行`bundle install`  
(注意：修改完Gemfile都要执行bundle install)  

3. 将Bootstrap的CSS套件装进专案里面    
在terminal输入  
`mv app/assets/stylesheets/application.css app/assets/stylesheets/application.scss`    
修改 app/assets/stylesheets/application.scss 档案，在最后加入以下两行  
![VKSpGD.png](https://s2.ax1x.com/2019/05/29/VKSpGD.png)
   
### Part2 修改样式    
####1. 新增app/views/common资料夹  
`mkdir app/views/common `  
####2. 新增navbar  
`touch app/views/common/_navbar.html.erb`  
填入   
```  
<nav class="navbar navbar-default" role="navigation">
    <div class="container-fluid">
        <!-- Brand and toggle get grouped for better mobile display -->
        <div class="navbar-header">
            <a class="navbar-brand" href="/">JDStore </a>
        </div>

        <!-- Collect the nav links, forms, and other content for toggling -->
        <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
            <ul class="nav navbar-nav navbar-right">
                <li><%= link_to("登入", '#') %></li>
            </ul>
        </div>
        <!-- /.navbar-collapse -->
    </div>
    <!-- /.container-fluid -->
</nav>
```   

####3. 新增footer  
`touch app/views/common/_footer.html.erb`  
填入  
加图片  

####4. 修改全域HTML样式application.html.erb  
``` 
<!DOCTYPE html>
<html>
    <head>
        <title>JDStore </title>
        <%= csrf_meta_tags %>

        <%= stylesheet_link_tag    'application', media: 'all', 'data-turbolinks-track': 'reload' %>
        <%= javascript_include_tag 'application', 'data-turbolinks-track': 'reload' %>
    </head>

    <body>

        <div class="container-fluid">
            <%= render "common/navbar" %>
            <%= yield %>
        </div>

        <%= render "common/footer" %>

    </body>
</html>
``` 
####5. 产生一个新的Hello World页面(放在welcome#index)   

`rails g controller welcome`  

- 新增一个welcome controller   
`touch app/views/welcome/index.html.erb`    
- 新增一个空得Hello World页面  

####6. 将首页指定到welcome下地index.html.erb页面  
修改`config/routes.rb`，改成以下内容  
```
Rails.application.routes.draw do
  root 'welcome#index'
end
```   

### Part3 增加Flash功能  
#### 1. 将Bootstrap的js提示套件bootstrap/alert「挂」在专案里面    
``` 
... (一堆注解)
//= require jquery
//= require jquery_ujs
//= require turbolinks
+//= require bootstrap/alert
//= require_tree .
```  
#### 2. 新增app/views/common/_flashes.html.erb  
``` 
<% if flash.any? %>
  <% user_facing_flashes.each do |key, value| %>
    <div class="alert alert-dismissable alert-><%= flash_class(key) %>">
      <button class="close" data-dismiss="alert">×</button>
      <%= value %>
  <% end %>
    </div>
<% end %>
```  
#### 3. 加入app/helpers/flashes_helper.rb  
`touch app/helpers/flashes_helper.rb`  
填入以下内容  
```
module FlashesHelper
  FLASH_CLASSES = { alert: "danger", notice: "success", warning: "warning"}.freeze

  def flash_class(key)
    FLASH_CLASSES.fetch key.to_sym, key
  end

  def user_facing_flashes
    flash.to_hash.slice "alert", "notice", "warning"
  end
end  
```  
#### 4. 在application.html.erb内加入flash这个partial  
在`<*= yield%>` 前加入`%= render "common/flashes%>`   
```  
<%= render "common/flashes" %>
      <%= yield %>
```  

#### 测试flash helper的功能  
加入`flash[:notice] = "早安！你好！"。你应该可以看到系统跳出「绿色」提示窗  
``` 
class WelcomeController < ApplicationController
  def index
    flash[:notice] = "早安！你好！"
  end
end 
```   

### Part4 安装Devise    
#### 1. 安装登入系统  
Devise是一个内热门的gem，专门用来快速实作「登入系统」。在这一节我们会用devise实作登入功能。   
Gemfile新增一行`gem 'divese`   
然后执行  
`bundle install`    
#### 2. 产生会员系统的必要档案   
执行  
```  
rails g devise:install 
rails g devise user  
rake db:migrate    
```  
重启rails s   
#### 3. 修改app/views/common/_navbar.html.erb   
```  
-                <li> <%= link_to("登入", '#') %>   </li>
+                <% if !current_user %>
+                  <li><%= link_to("注册", new_user_registration_path) %> </li>
+                  <li><%= link_to("登入", new_user_session_path) %></li>
+                <% else %>
+                  <li class="dropdown">
+                    <a href="#" class="dropdown-toggle" data-toggle="dropdown">
+                        Hi!, <%= current_user.email %>
+                        <b class="caret"></b>
+                    </a>
+                    <ul class="dropdown-menu">
+                        <li><%= link_to("登出", destroy_user_session_path, method: :delete) %></li>
+                    </ul>
+                  </li>
+                <% end %>

```  
#### 4. 修改app/assets/javascripts/application.js  
加入一行`//= require bootstrap/dropdown`  
``` 
//= require bootstrap/dropdown
//= require_tree .
```  

### Part5 安装SimpleForm   
#### 1. 首先我们要来安装simple_form   
在Gemfile中新增一行`gem 'simple_form'`  
```  
gem 'bootstrap-sass'
gem 'devise'
+ gem 'simple_form' 
```   
然后执行  
`bundle install`  
安装gem  
#### 2. 安装simple_form for bootstrap设定  
执行  
` rails g simple_form:install --bootstrap`  
![V10W7V.png](https://s2.ax1x.com/2019/06/01/V10W7V.png)  
重启 rails s  

### Part6 安装 font-awesome-rails  
#### 1. 挂上font-awesome-rails  
``` 
gem 'simple_form'
gem 'font-awesome-rails'  
```

#### 2. 执行 `bundle install`   
重启`rails s`  

#### 3. 将font-awesome装进专案里面  
```  
@import "bootstrap";
@import "font-awesome";  
```  
#### 4.修改app/views/common/_navbar.html.erb  
```  
             <% if !current_user %>
               <li><%= link_to("注册", new_user_registration_path) %> </li>
-                  <li><%= link_to("登入", new_user_session_path) %></li>
+                  <li><%= link_to(content_tag(:i, '登入', class: 'fa fa-sign-in'), new_user_session_path) %></li>
             <% else %>
               <li class="dropdown">
                 <a href="#" class="dropdown-toggle" data-toggle="dropdown">
                     Hi!, <%= current_user.email %>
                     <b class="caret"></b>
                 </a>
                 <ul class="dropdown-menu">
-                        <li> <%= link_to("登出", destroy_user_session_path, method: :delete) %> </li>
+                        <li> <%= link_to(content_tag(:i, '登出', class: 'fa fa-sign-out'), destroy_user_session_path, method: :delete) %> </li>
                 </ul>
               </li>
             <% end %>
``` 





**Changelog**  
20190529 初稿Part1  
20190530 增加Part2,3   
20190601 增加Part4,5,6  


