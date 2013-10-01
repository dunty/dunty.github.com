---
layout: post
title: "如何搭建 git github jekyllbootstrap markdownpad 来写自己的Blog"
description: ""
category: TOOLS
tags: [github, jekyll, markdown, blog]
---
{% include JB/setup %}

**github** 开放、进取、共享。

## github ##
1、Get an account：

[http://github.com](http://github.com/ "github.com")

创建后的 account name 就是 你的 USERNAME。

2、Create a New Repository

Go to your https://github.com and create a new repository named USERNAME.github.com

注意，无论前面自己建了几个仓库，必须要新建一个与自己的USERNAME相同的，并且要有 .github.com 后缀的 仓库名。
如，dunty.github.com，否则后继的提交总会失败，因为不存在jekyllbootstrap需要仓库！！

3、下载安装 github for windows

[github for windows guide](https://help.github.com/articles/getting-started-with-github-for-windows "windows")
Getting Started with GitHub for Windows

GitHub for Windows was designed from the ground-up to not only be the best GitHub client available, but the best git client, period. It makes heavy use of Windows' sexy Metro look. Everything looks, acts, and feels like a native Windows program.

To get started, download the latest version directly from [windows.github.com](http://windwos.github.com/ "title").

GitHub for Windows sign in screenWhen you start the app, you'll be given the option to either log into your GitHub account, or create a new one.

GitHub for Windows repository listingOn the left, you'll see your GitHub account, as well as any organizations you're a part of. Clicking on a name will show you which repositories are available. Clicking on clone brings the repository to your computer.

GitHub for Windows new repository buttonAlternatively, you can click on + add at the top of the program, and create a new repository locally.

[download](http://github-windows.s3.amazonaws.com/GitHubSetup.exe "title")

安装后就会在PC上有一个git的环境了，可使用图形界面的，也可使用github shell。

2013-09-01: （以前安装时是在win7/8下）在XP和IE下下载时，会自动使用讯雷下载，然后运行 `GitHubSetup.exe`，则无法安装上，查到
[Introducing GitHub For Windows](http://haacked.com/archive/2012/05/21/introducing-github-for-windows.aspx#87324)中说明：

	We use ClickOnce to install the application and to provide Google Chrome style silent, automated, updates that install in the background to keep it up-to-date.

因此，尝试在Chrome下下载并点击运行，安装成功。


## jekyllbootstrap ##
[http://jekyllbootstrap.com/](http://jekyllbootstrap.com/ "jekyllbootstrap")

按指导进行安装。

1 - Create a New Repository

Go to your https://github.com and create a new repository named USERNAME.github.com

2 - Install Jekyll-Bootstrap 以下各步在本地机的 github shell 中执行

    $ git clone https://github.com/plusjade/jekyll-bootstrap.git USERNAME.github.com
    $ cd USERNAME.github.com
    $ git remote set-url origin git@github.com:USERNAME/USERNAME.github.com.git
    $ git push origin master
    

3 - Profit

After GitHub has a couple minutes to do its magic your blog will be publicly available at http://USERNAME.github.com 

## Markdown ##
写Post时，只需要使用文本编辑器写Markdown标记的文件就可以了。

[Markdown标记](http://qingbo.net/picky/502-markdown-syntax.html "Markdown标记")

[英文完整版](http://daringfireball.net/projects/markdown/syntax "英文完整版")

Windows平台推荐使用 [MarkdownPad](http://markdownpad.com/)


## 语法检查 ##
push本地的repository之后却收到`Page build failure`的邮件，原因是github的jekyll更新版本了，在生成静态HTML文件的时候加强了语法和错误的检查，所以过去可以忽略的一点小错误成了现在致命的伤。
如 超链接标识中的 title 部分不能为空`[MarkdownPad](http://markdownpad.com/ "")`，必须要填写文字`[MarkdownPad](http://markdownpad.com/ "title")`。

## 目录组织 ##

index.md 是根下的文件，需要修改成自己用的

\_posts目录下则是保存post的地方，文件名格式必须是 YYYY-MM-DD-titles.md

## 主要的git命令 ##
这些命名需要在自己的 本地 仓库名 目录下 执行：

    git add .
    git commit -m \"comment\"
    git push

`git add .`用于标识修改的内容，本地所有

`git commit`本地提交

`git push`提交到github
