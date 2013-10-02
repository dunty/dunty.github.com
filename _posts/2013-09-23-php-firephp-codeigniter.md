---
layout: post
title: "线上系统调试利器firephp+codeigniter"
description: ""
category: php
tags: [php, firephp, codeigniter]
---
{% include JB/setup %}

**firephp codeigniter** 

## firephp ##

[线上系统调试利器：FirePHP （附：结合CodeIgniter）](http://blog.chinaunix.net/uid-16235175-id-3275031.html)

4、与CodeIgniter结合使用：

a、将FirePHP.class.php、fb.php移动至system/application/libraries 

b、重命名：FirePHP.class.php=>Firephp.php，fb.php=>Fb.php 

c、编辑这两个文件的第一行，改为：`<?php  if ( ! defined('BASEPATH')) exit('No direct script access allowed');` 

d、注释掉fb.php的第45行：`//require_once dirname(__FILE__).'/FirePHP.class.php';` 

e、编辑(或增加)config/autoload.php ：`$autoload['libraries'] = array("firephp", "fb");` 


[ Issue 6803 (Console panel throws an exception because this.filterMatchSet is not defined)](https://github.com/firebug/firebug/commit/b01414c03f260a1b12f68f7ec824c4afee67433c)


Open the FireBug xpi file with your favourite archive/zip manager. For linux users, you should find the file here:

    ~/.mozilla/firefox/[unique-id].default/extensions/firebug@software.joehewitt.com.xpi


Navigate to `/content/firebug/console/` in the archive/zip manager and open `consolePanel.js`

    {
         Firebug.ActivablePanel.initialize.apply(this, arguments);  // loads persisted content
 
    +    this.filterMatchSet = [];
    +
         if (!this.persistedContent && Firebug.Console.isAlwaysEnabled())
             this.insertLogLimit(this.context); 

