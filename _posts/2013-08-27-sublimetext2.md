---
layout: post
title: "安装使用Sublime Text 2"
description: ""
category: basic
tags: [sublime, plugins]
---
{% include JB/setup %}

**Sublime Text 2** 轻量、简洁、高效、跨平台的编辑器，方便的配色以及兼容vim快捷键等各种优点博得了很多前端开发人员的喜爱

## install ##

1、下载地址：
-----------

[Sublime Text 2](http://www.sublimetext.com/2 "sublimetext")
Download

The current version of Sublime Text 2 is 2.0.2.

OS X (OS X 10.6 or later is required) 
Windows - also available as a [portable](http://c758482.r82.cf2.rackcdn.com/Sublime%20Text%202.0.2.zip) version  
Windows 64 bit - also available as a portable version  
Linux 32 bit  
Linux 64 bit  

2、package control  安装
-----------------

(仅适用于Sublime Text2 ，Text3中由于更新了python函数,无法安装，但是由于text3为测试版，插件也不是很多，等成熟以后更新)

我们用sublime几乎都会首先安装这个插件，这个插件是管理插件的功能，先安装它，再安装其他插件就方便了。

点击sublime的菜单栏 view->show console ；现在打开了控制台， 这个控制台有上下两栏，上面一栏会实时显示sublime执行了什么插件，输出执行结果， 如果你安装的某个插件不能正常运行，应该先在这里看看有没有报错。下面栏是一个输入框，可以运行python代码。我们输入下面的代码点击回车运行， 就能安装好package control了。

    import urllib2,os;pf='Package Control.sublime-package';ipp=sublime.installed_packages_path();os.makedirs(ipp) if not os.path.exists(ipp) else None;open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read())  

运行结束以后，记得重启编辑器，就能在Preferences中看到 package control了。

然后我们按住 ctrl+shift+p。此时会输出一个输入框， 输入install。选择package contrl： install package 回车，需要稍定一会儿，右下角状态栏会显示正在连接的提示文字。使用sublime时注意看右下角状态栏，很多插件的提示信息都显示在这里，这个状态栏很小，初次使用的人都有可能没有注意到它。   

稍等一会儿后，它会出现一个插件列表， 你也可以在输入框中输入文字进行搜索插件。 搜索到自己想安装的插件，再选择它，回车。 就自动给你安装好了。

如果要卸载插件， ctrl+shift+p 输入 remove， 选择package control:remove package 然后再选择已安装的插件， 回车即可卸载。

当然也可以这样：Preferences--> package control  选择安装和移除插件。

点击Install Package之后，稍等一会，就出先搜索安装的列表。

3、 ctags  
-------------

这个插件能跨文件跳转，跳转到指定函数声明的地方。 使用package control 搜索ctags 进行安装。 （最舍不得netbeans就是这个函数跳转功能了，这个插件实现了！！）。

但是，还需要

1>下载ctages.exe [这里有提供下载地址](http://untidy.net/blog/2006/10/04/ctags-php-5-support/) 然后将ctages.exe放到环境变量能访问到的地方（我直接放到了某个文件下，然后添加到了环境变量）

2>运行cmd命令 执行下ctages 如果能执行就ok ，然后在命令行格式下到所需打开项目的目录下，运行命令

    ctags -R -f .tags  

会生成一个.tags 文件。这用sublime打开项目以后，就可以用下面方法跳转到函数声明

    ctrl+t   ctrl+t   //鼠标在函数出执行，跳到函数处  
    ctrl+t   ctrl+b  //调回函数  

当然用 ctrl+shift+鼠标左键 也可以跳到。

或者在sublime项目文件夹右键， 会出现Ctag:Rebuild Tags 的菜单。点击它，然后会生成.tags的文件。

4、 SVN

搜索svn显示以后直接回车，安装，安装以后可以直接在文件目录或者文件编辑中右键来提交和更新文件了。
快捷键 alt+c 提交 ，alt+u 更新。


5、emmet (ex - zencoding)

敲打html和css神器啊，强烈推荐。在window显示下方输入框命令是ctrl+alt+enter.在mac下面是control+alt+enter.




## 支持PHP
1、配置php调试环境
-----------------
步骤一：
首先确保你电脑安装了php，并把php设置到环境变量里了。

步骤二：点击 sublime text的“工具”->"编译系统"->"编译新系统" 
步骤三：输入编译脚本，输入如下：

    {
    "cmd": ["php", "$file"],
    "file_regex": "^(...*?):([0-9]*):?([0-9]*)",
    "selector": "source.php"
    }

另存到Sublime Tex的Data目录下，如下是我的目录： 

    E:\softwave\Sublime Text 2.0.1\Data\Packages\PHP

文件名叫：PHP.sublime-build
步骤四：新建个文件，写几句脚本，保存。按Ctrl+B编译

    <?php
    echo "test";
    ?>

2、sublimecodeintel 代码提示。 

sublime默认的代码提示只能提示系统函数，用户自己创建的函数、类不能提示。 如果想要提示自己建立的函数。 可以安装sublimecodeintel插件。

sublimecodeintel 安装后需要配置，文件：插件目录/.codeintel/config 中 增加

    {
    "PHP": {  
            "php": 'D:\SaeServer\php\php.exe',  
            "phpExtraPaths": ['D:\SaeServer\php\stdlib'],  
            "phpConfigFile": 'D:\SaeServer\apache\php.ini'  
        },  
      
    "JavaScript": { "javascriptExtraPaths": [] }
    }  
      
    //自己的php解释器和配置文件  

3、 sublimelint 和 Phpcs  语法错误提示。

我们需要在写代码的时候如果有语法错误，能立即提示我们， 可以安装这两个插件：sublimelint 和Phpcs ， sublimeint 需要系统有php命令。 所以需要设置好php的环境变量。 sublimelint的语法错误提示是显示在状态栏上面的，所以在编写程序的时候注意时常看看状态栏。 而Phpcs的语法错误提示是在我们保存文件时弹出万能面板显示错误，sublimelint的错误提示实时但不明显。 Phpcs的错误提示不是实时的，但很明显。 因此我们一般这两个插件都要安装。

4、 function name display。 

这个插件可以在状态栏显示出当前光标处于哪个函数中。

5、 additional PHP snippet 和 DocBlockr  代码注释格式化。

additional PHP snippet插件能提示phpdocument格式的代码，还能快速输出开源协议， 输入php- 会有提示
安装DocBlockr 插件，能形成注释块。不用每次敲注释的斜杠或星号。

6、 BracketHighlighter 成对匹配的增强。

像这些符号是成对的：花括号{}， 中括号[],括号：() ，引号“” 等。 这些符号当我们鼠标放在开始符号的位置的时候， 希望能明显看到结尾符号在哪儿sublime默认是下划线，很不明显， 想要明显一点，可以安装插件  BracketHighlighter。

7、 goto document

这个插件能帮助我们快速查看手册。 比如我们在写php代码时， 突然忘记了某个函数怎么用了，将鼠标放在这个函数上，然后按F1，它能快速打开PHP手册中说明这个函数用法的地方。 
安装好 goto document插件后我们再配置快捷键F1 跳转到文档。 打开sublime的菜单栏Preferences->key bindings -User  设置快捷键：

    [
        { "keys": ["f1"], "command": "goto_documentation" }
    ] 


8、 GBK Encoding Support

sublime本身不支持GBK编码， 可以安装这个插件让它支持。


9、格式化PHP代码 php-beautifier

安装 php-beautifier 插件，使用php-beautifier还需要安装 PHP Beutifier的pear包：

    pear install PHP_Beautifier

安装好后， 打开PHP文件,ctrl+alt+f 就能为你自动格式化代码。
 

13.Thinkphp

使用框架开发的可以安装此插件，包括CI等都有。

我的配置(preferrences.sublime-settings)：

    {
    "color_scheme": "Packages/Color Scheme - Default/Monokai.tmTheme",
    "font_face": "Courier New",
    "font_size": 11,
    "highlight_line": true,
    "ignored_packages":
    [
    "Vintage"
    ],
    "theme": "Soda Light.sublime-theme",
    "word_wrap": true
    }



## 支持 Markdown

三、安装Markdown Preview

按Ctrl + Shift + P
输入pci 后回车(Package Control: Install Package)
稍等... 
输入Markdown Preview回车

四、编辑

按Ctrl + N 新建一个文档
按Ctrl + Shift + P
使用Markdown语法编辑文档
语法高亮，输入ssm 后回车(Set Syntax: Markdown)

五、在浏览器预览Markdown文档

按Ctrl + Shift + P
输入mp 后回车(Markdown Preview: current file in browser)
此时就可以在浏览器里看到刚才编辑的文档了



## 配置
1、配置tab为4个空格 

    Preference-defalut:
    // The number of spaces a tab is considered equal to
    “tab_size”: 4,
    // Set to true to insert spaces when tab is pressed
    “translate_tabs_to_spaces”: true,

2、参考

Setting User

    "font_face": "courier new",
    "font_size": 9.0,
    "highlight_line": true,
    "scroll_past_end": false,
    "tab_size": 4,
    "theme": "Soda Dark.sublime-theme",
    "word_wrap": true
    }


## 其他plugins
[Package Control](https://sublime.wbond.net/)

[ZenCoding](http://www.qianduan.net/zen-coding-a-new-way-to-write-html-code.html)

不得不用的一款前端开发方面的插件，Write less , show more.安装后可直接使用，Tab键触发，Alt+Shift+W是个代码机器。

Alignment

代码对齐，如写几个变量，选中这几行，Ctrl+Alt+A，哇，齐了。

Prefixr

写 CSS可自动添加 -webkit 等私有词缀，Ctrl+Alt+X触发。

Tag

Html格式化，右键Auto-Format Tags on Ducument。

Clipboard History

剪贴板历史记录，显示更多历史复制，Ctrl+Shift+V触发。

SideBarEnhancements

侧栏右键功能增强，非常实用

Theme – Soda

完美的编码主题，用过的都说好，Setting user里面添加”theme”: “Soda Dark.sublime-theme”

GBK to UTF8

将文件编码从GBK转黄成UTF8，菜单 – File里面找

SFTP

直接编辑 FTP 或 SFTP 服务器上的文件，绝对FTP浮云

WordPress

集成一些WordPress的函数，对于像我这种经常要写WP模版和插件的人特别有用

PHPTidy

整理排版PHP代码

YUI Compressor

压缩JS和CSS文件

jQuery Package for sublime Text

如果你离不开jQuery的话，这个必备～～

Sublime Prefixr

Prefixr，CSS3 私有前缀自动补全插件，显然也很有用哇

JS Format

一个JS代码格式化插件。

 
Placeholders

故名思意，占位用，包括一些占位文字和HTML代码片段，实用。

Sublime Alignment

用于代码格式的自动对齐。传说最新版Sublime 已经集成。
 
Clipboard History

粘贴板历史记录，方便使用复制/剪切的内容。

DetectSyntax

这是一个代码检测插件。

Nettuts Fetch

如果你在用一些公用的或者开源的框架，比如 Normalize.css或者modernizr.js，但是，过了一段时间后，可能该开源库已经更新了，而你没有发现，这个时候可能已经不太适合你的项目了，那么你就要重新折腾一遍或者继续用陈旧的文件。Nettuts Fetch可以让你设置一些需要同步的文件列表，然后保存更新。


JsMinifier

该插件基于Google Closure compiler，自动压缩js文件。

Hex to HSL

自动转换颜色值，从16进制到HSL格式，快捷键 Ctrl+Shift+U

 
GBK to UTF8

将文件编码从GBK转黄成UTF8，快捷键Ctrl+Shift+C

Git

该插件基本上实现了git的所有功能。

[PHPChina](http://www.phpchina.com/archives/view-41577-1.html)


## Sublime Text快捷键

    Ctrl+Shift+P：打开命令面板
    Ctrl+P：搜索项目中的文件
    Ctrl+G：跳转到第几行
    Ctrl+W：关闭当前打开文件
    Ctrl+Shift+W：关闭所有打开文件
    Ctrl+Shift+V：粘贴并格式化
    Ctrl+D：选择单词，重复可增加选择下一个相同的单词
    Ctrl+L：选择行，重复可依次增加选择下一行
    Ctrl+Shift+L：选择多行
    Ctrl+Shift+Enter：在当前行前插入新行
    Ctrl+X：删除当前行
    Ctrl+M：跳转到对应括号
    Ctrl+U：软撤销，撤销光标位置
    Ctrl+J：选择标签内容
    Ctrl+F：查找内容
    Ctrl+Shift+F：查找并替换
    Ctrl+H：替换
    Ctrl+R：前往 method
    Ctrl+N：新建窗口
    Ctrl+K+B：开关侧栏
    Ctrl+Shift+M：选中当前括号内容，重复可选着括号本身
    Ctrl+F2：设置/删除标记
    Ctrl+/：注释当前行
    Ctrl+Shift+/：当前位置插入注释
    Ctrl+Alt+/：块注释，并Focus到首行，写注释说明用的
    Ctrl+Shift+A：选择当前标签前后，修改标签用的
    F11：全屏
    Shift+F11：全屏免打扰模式，只编辑当前文件
    Alt+F3：选择所有相同的词
    Alt+.：闭合标签
    Alt+Shift+数字：分屏显示
    Alt+数字：切换打开第N个文件
    Shift+右键拖动：光标多不，用来更改或插入列内容
    鼠标的前进后退键可切换Tab文件
    按Ctrl，依次点击或选取，可需要编辑的多个位置
    按Ctrl+Shift+上下键，可替换行


## 其他

[Sublime Text 2 入门及技巧](http://lucifr.com/139225/sublime-text-2-tricks-and-tips/)。

[ZenCoding in Sublime Text 2](http://lucifr.com/139231/zencoding-in-sublime-text-2/) 关于 ZenCoding 参考小众的介绍：[Zen Coding – 超快地写网页代码](http://www.appinn.com/zen-coding/)

[Sublime Text 2 实用快捷键Mac OS X](http://lucifr.com/139235/sublime-text-2-useful-shortcuts/)

[Sublime Text 2 右键菜单中的实用选项](http://lucifr.com/2012/02/08/useful-entries-in-sublime-text-2-context-menu/)

[关于Sublime Text2的一些记录](http://www.cnblogs.com/varlxj/archive/2012/01/26/2329788.html)

[Sublime Text 使用介绍/全套快捷键及插件推荐](http://www.ithome.com/html/soft/31560.htm)
