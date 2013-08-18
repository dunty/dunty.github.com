layout: page title: First Page

# 如何搭建 git github jekyllbootstrap markdownpad 来写自己的Blog #

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

To get started, download the latest version directly from [windows.github.com](http://windwos.github.com/,"").

GitHub for Windows sign in screenWhen you start the app, you'll be given the option to either log into your GitHub account, or create a new one.

GitHub for Windows repository listingOn the left, you'll see your GitHub account, as well as any organizations you're a part of. Clicking on a name will show you which repositories are available. Clicking on clone brings the repository to your computer.

GitHub for Windows new repository buttonAlternatively, you can click on + add at the top of the program, and create a new repository locally.

[download](http://github-windows.s3.amazonaws.com/GitHubSetup.exe, "")

安装后就会在PC上有一个git的环境了，可使用图形界面的，也可使用github shell。


## jekyllbootstrap ##
[http://jekyllbootstrap.com/](http://jekyllbootstrap.com/ "jekyllbootstrap")

按指导进行安装。

1 - Create a New Repository

Go to your https://github.com and create a new repository named USERNAME.github.com

2 - Install Jekyll-Bootstrap

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
