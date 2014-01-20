---
layout: post
title: "config github in nitrous"
description: ""
category: 4tom
tags: [nitrous, github]
---
{% include JB/setup %}

**Nitrous** 

## github ##

1.首先是在github上创建一个账户：xxxxx
然后我个人的主页就是github.com/xxxxx了。
然后在github上创建一个test仓库，进行基本配置后需要在test仓库中添加可以提交代码的电脑的公钥。

这个公钥怎么生成呢？这就要转到我们PC这一边进行设定了。
在linux上有一个ssh-keygen的工具，使用命令

    ssh-keygen -t rsa -C "committer_email@committermail.com"  

设定存放目录和密码后把.ssh/id_rsa.pub的文件内容粘贴进github的test仓库里。
测试是否成功

    ssh -T git@github.com  

2.配置用户名和邮箱

    git config --global user.name 'The Name'  
    git config --global user.email anyemail@mail.com  

这个等效与home下.gitconfig文件中的

    [user]                                                                            
    >---name = LZY under Ubuntu with Hasee  
    >---email = luozhaoyu90@gmail.com  

这里应该是随便配置用户名和邮箱都可以，这个事方便大家联系 

3.复制一个git项目

    git clone git://github.com/luozhaoyu/test.git  

更新项目

    git pull  
    
4.成功后变在本机创建一个git仓库。

    git init  

在远程初始一个git仓库

    git --bare init  

新建一个文件夹test_git，在里面添加若干文件

    git add *  

提交并评论

    git commit -m 'your comment'  

设置github的仓库地址并取名为origin(可能可以取其它名字？)

    git remote add origin git@github.com:luozhaoyu/test.git  

最后把master提交到origin服务器上

    git push origin master  

