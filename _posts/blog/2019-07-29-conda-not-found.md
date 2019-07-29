---
layout: post
title: conda not found      
category: blog
description: zsh shell中增加路径          
--- 

#### 问题现象：安装anaconda3成功后，terminal输入`conda --version`显示"conda not found"  
 



#### 解决办法  
 conda not found的原因是我更改了MAC自带的bash shell，改成了zsh shell，命令行安装是不会自动加路径到zsh shell中，需要手动添加   
 
 **如何手动添加**  
 在.zshrc中添加路径    
 export PATH="<path to anaconda>bin:$PATH"  
 例如本例中添加  
 export PATH="/Users/johnson/anaconda3/bin":$PATH   
 关闭iterm窗口重新打开，就OK了  


