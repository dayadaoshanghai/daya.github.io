---
layout: post
title: 问题     
category: blog
description:         
--- 

 
#### 1. html中得class 和 id属性的作用是什么？怎么用？class中可以写什么？  
``` 
<footer class="f" style="margin-top: 100px;">
    <p class="text-center">Copyright ©2019 JDStore
        <br>Design by johnson

    </p>
</footer>  

Bootstrap 

<footer class="container" style="margin-top: 100px;">
    <p class="text-center">Copyright ©2019 JDStore
        <br>Design by johnson

    </p>
</footer>  


```    

```
# style.css
.container {
}

.p {
	color: #f0f;
}
```


#### 2. 这种嵌套Ruby语法怎么读懂？   
```  
 <%= link_to product_path(product) do %>
            <% if product.image.present? %>
              <%= image_tag(product.image.thumb.url, class: "thumbnail") %>
            <% else %>
              <%= image_tag("http://placehold.it/200x200&text=No Pic", class: "thumbnail") %>
            <% end %>
 <% end %>
```   

block

```
<% %>
<%= %>
``` 


#### 3. helper的作用   

#### 4. devise安装步骤  
`rails g devise:install`  
`rails g devise user`

#### 5. 路径设定中namespace是什么作用？    
```
namespaces :admin do
	resources :products
end
```

`/admin`
`/admin/products`

#### 6.layout的来源  
``` 
class Admin::ProductsController < ApplicationController

+ layout "admin"

  before_action :authenticate_user!
  before_action :admin_required
...(略)
 
``` 



