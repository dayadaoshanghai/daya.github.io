---
layout: post
title: heroku上传     
category: blog
description: heroku上传步骤       
---

文章未完待续，待加入每个步骤的图  

1. `heroku login` 登录heroku 
2. `heroku create` 创造一个heroku app 
3.  修改Gemfile，加入'pg' gem  
```
group :production do
  gem 'pg'
end
```

4. `git push heroku master` push本地master到heroku 
    也可以push最新分支到heroku，方法是`git push heroku 分支名:master`   
5. `heroku run rake db:migrate` 数据库  
6. `heroku open` 打开heroku app   


备注： 
`git remote rm heroku`  删除heroku的方法
`heroku run rails console`  打开heroku控制台  






