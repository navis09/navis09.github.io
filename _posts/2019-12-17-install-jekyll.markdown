---
title: 使用Jekyll搭建个人博客的问题记录
date:   2019-12-17 11:30:35 +0800
categories:
- General
comments: true
excerpt: |
  Build Blog by Jekyll
feature_text: |
  ## Blog with Jekyll
  Jekyll is a static site generator. You give it text written in your favorite markup language and it uses layouts to create a static website. You can tweak how you want the site URLs to look like, what data gets displayed on the site, and more. 
---


>  Jekyll is a [Ruby Gem](https://jekyllrb.com/docs/ruby-101/#gems) that can be installed on most systems. 
>
>  Jekyll is a static site generator. You give it text written in your favorite markup language and it uses layouts to create a static website. You can tweak how you want the site URLs to look like, what data gets displayed on the site, and more. 

### Jekyll的安装与部署

1.参考[Jekyll的官方流程](https://jekyllrb.com/docs/installation/#requirements) 进行安装环境的搭建

2.根据[QuickStart](https://jekyllrb.com/docs/) 创建博客项目

---

### 遇到的问题

##### 问题1: Network error

在执行 ```jekyll new myblog``` 时，遇到如下的错误

```
Fetching source index from https://rubygems.org/
Resolving dependencies...
Network error while fetching
https://rubygems.org/quick/Marshal.4.8/tzinfo-1.2.5.gemspec.rz (execution
expired)
```

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
原因:

一般情况无法访问国外的源，这时候需要替换为国内的Ruby的镜像源

> 国内的源经历过三个阶段
>
> 早期： https://ruby.taobao.org/ 
>
> 中期： https://gems.ruby-china.org/ 
>
> 后期： https://gems.ruby-china.com/  一个是com，一个是org，这里需要注意

现在能正常使用的就是后期：https://gems.ruby-china.com/ 

---

##### 问题2: Time out

在替换的过程中，还出现了这个问题
```
Error fetching https://gems.ruby-china.com/:
        timed out (https://gems.ruby-china.com/specs.4.8.gz)
       
```

出现超时问题。几番搜索无果后（在他人的帮助下）尝试ping该地址，结果返回的是ipv6格式。
由于笔者之前在内网环境下进行过ipv6的测试，但未开通ipv6公网，导致超时。这时候去关闭一下ipv6就可以了...

这种场景一般人不会有的吧，正常情况下更多的可能:

就是你的网络不行>_<



