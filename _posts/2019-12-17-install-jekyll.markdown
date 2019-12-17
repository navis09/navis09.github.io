---
layout: post
title:  "使用Jekyll搭建个人博客"
date:   2019-12-17 11:30:35 +0800
categories: jekyll
---

参考 https://jekyllrb.com/docs/  

>  Jekyll is a [Ruby Gem](https://jekyllrb.com/docs/ruby-101/#gems) that can be installed on most systems. 
>
>  Jekyll is a static site generator. You give it text written in your favorite markup language and it uses layouts to create a static website. You can tweak how you want the site URLs to look like, what data gets displayed on the site, and more. 

首先需要安装Ruby 和 RubyGem， 根据Jekyll的官网，对于Windows系统，使用RubyInstaller 安装一个Ruby + Devkit 的版本

根据提示一步步完成，官网所述的```ridk install```也可以在installer的安装流程中完成

开启一个新的cmd窗口，以便于```PATH```路径参数能成功修改，执行 gem install jekyll bundler

检查jekyll是否安装成功，```jekyll -v ```

至此就完成了Jekyll的安装

创建名为'myblog'的项目 ```jekyll new myblog``` 

进入路径 ``` cd myblog ```

运行项目，开启服务 ```  bundle exec jekyll serve  ```

访问网页: [http://localhost:4000](http://localhost:4000/) 





在第三步的 ```jekyll new myblog``` 时，会遇到如下的错误

```
Fetching source index from https://rubygems.org/
Resolving dependencies...
Network error while fetching
https://rubygems.org/quick/Marshal.4.8/tzinfo-1.2.5.gemspec.rz (execution
expired)
```

一般情况无法访问国外的源，这时候需要替换为国内的Ruby的镜像源

国内的源经历过三个阶段

早期： https://ruby.taobao.org/ 

中期： https://gems.ruby-china.org/ 

后期： https://gems.ruby-china.com/  一个是com，一个是org，这里需要注意

 现在能正常使用的就是后期：https://gems.ruby-china.com/ 

直接输入以下命令进行源替换

```
$ gem update --system # 这里请翻墙一下
$ gem -v # 笔者当前最新版是3.1.1
2.6.3

$ gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
$ gem sources -l
https://gems.ruby-china.com
# 确保只有 gems.ruby-china.com
```

然而在替换的过程中，还出现了这个问题

首先需要检查自己的网络状态

```
Error fetching https://gems.ruby-china.com/:
        timed out (https://gems.ruby-china.com/specs.4.8.gz)
       
```

由于开启IPV6导致超时，这里取消勾选即可


