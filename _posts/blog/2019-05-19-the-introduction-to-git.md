---
layout: post
title: git  
category: blog
description: git入门篇   
---

### Fork & Clone的区别  
*Fork*，直接建立一个一样的Project在仓库上，管理者是你，但进度不会与原作者同步（需自行更新），用意是共同协作开源代码    
*Clone*，知识单纯复制代码到机器上，并会把仓库地址复制下来  

### Work follow工作流程 
1. master就是稳定的production
2. develop用来当做开发的主要分支
3. 其他开发都是从develop切出去，最后会并回来  

### git 常用指令 
`git checkout -b 新分支名`   建立新分支       
`git checkout 分支名 `   切换分支      
`git branch -D 分支名 `  删除分支   
`git merge 分支名` 合并分支    

`git remote -v` 查看远程部署情况   
`git merge 分支名` 合并分支到master  
`git remote rm heroku` 删除本质与heroku的链接   
`git push origin master` 推送本地的master分支到远程的origin仓库  
`git push -u origin master` 预设以后都是推到远程的origin仓库   
`git pull` 拉下远程仓库的变更  
`git push heroku 分支名:master` 把「分支名」这个分支推送到远程  


#### 存档  
`cd 你的项目文件夹名称`      
`git init`    
`git add .`    
`git commit -m "对于修改部分的简述"`   

### gitignore  
- 可以设定哪一些档案不被git存取  
- 比如说config/database.yml  


