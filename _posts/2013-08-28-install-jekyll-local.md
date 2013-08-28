---
layout: post
title: "安装使用本地jekyll"
description: ""
category: basic
tags: [jekyll, local]
---
{% include JB/setup %}

**jekyll** 

## install ##

1、[Building portable Jekyll for Windows](http://www.madhur.co.in/blog/2013/07/20/buildportablejekyll.html)
其中打的是x64的包，没法使用

2、自行下载[Ruby 2.0.0-p247](http://dl.bintray.com/oneclick/rubyinstaller/ruby-2.0.0-p247-i386-mingw32.7z?direct)

3、自行下载[DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe](http://rubyforge.org/frs/download.php/76805/DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe)

4、安装jekyll
    gem install jekyll -V
不带-V，则不显示消息。最好用马上有回显消息，出问题也比较清晰问题出在哪里，注意是命令后面加一个大写的V参数，表示详细日志的意思，这样就可以了。

安装出错，是因为devkit没初始化到位。都已被覆盖，因此需要重新设置。

5、I moved to another machine (archlinux, ruby1.9.2-p290) and there I can't run 'rake generate' when I have umlauts in a post.

    /home/ben/.rvm/gems/ruby-1.9.2-p290/gems/jekyll-0.11.0/lib/jekyll/convertible.rb:32:in `read_yaml': invalid byte sequence in US-ASCII (ArgumentError)

I fixed that with changing the line 29 in convertible.rb from

    self.content = File.read(File.join(base, name))

to

    self.content = File.read(File.join(base, name), :encoding => "utf-8")

now it works on both machines with umlauts in code blocks and normal text. (the other machine is an ubuntu 11.04)
