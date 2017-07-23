---
layout: post
title:  "Jekyll deploy problem!"
date:   2017-04-17 06:29:26 +0800
categories: ruby
---

in mac sierra, ruby version is 2.0.0, so it has problem when start jekyll
use rvm to manage ruby version

check Gemfile.lock

curl -L get.rvm.io | bash -s stable

source ~/.bashrc
source ~/.bash_profile

ruby -v

rvm list known

rvm install 2.3.3

Bundler 会连接rubygems.org（或者其他你声明的源），然后列出所有你指定的符合你需要的 gem。因为所有你在Gemfile里的依赖有它们自己的依赖，所以基于上面的Gemfile运行bundle install会安装相当多的的 gem。

bundle install

bundle exec jekyll serve
```
jekyll 采用ruby来构建，因此需要了解一下ruby的基本概念和工具。
RVM
用于帮你安装Ruby环境，帮你管理多个Ruby环境，帮你管理你开发的每个Ruby应用使用机器上哪个Ruby环境。Ruby环境不仅仅是Ruby本身，还包括依赖的第三方Ruby插件。都由RVM管理。
Rails
这个也不用多说，著名开发框架。详细看 http://zh.wikipedia.org/wiki/Ruby_on_Rails
RubyGems
RubyGems是一个方便而强大的Ruby程序包管理器（ package manager），类似RedHat的RPM.它将一个Ruby应用程序打包到一个gem里，作为一个安装单元。无需安装，最新的Ruby版本已经包含RubyGems了。
Gem
Gem是封装起来的Ruby应用程序或代码库。
注：在终端使用的gem命令，是指通过RubyGems管理Gem包。
Gemfile
定义你的应用依赖哪些第三方包，bundle根据该配置去寻找这些包。
Rake
Rake是所有需要安装的Gem中最重要的一个，并且它应该始终是你在系统上第一个安装的Gem。Rake是一个构建工具，和Make很相似，但它允许用Ruby来写Rakefile（如何进行构建的定义文件），其中使用了一种特定的DSL（domain-specific language，领域专用语言），在保持Ruby强大功能的同时提供很高的可读性。 Rails用rake扩展来完成多种不容任务，如数据库初始化、更新等。
Rake is a build language, similar in purpose to make and ant. Like make and ant it's a Domain Specific Language, unlike those two it's an internal DSL programmed in the Ruby language.
PS：个人感觉有点类似Symfony2中的app/console
详细 http://rake.rubyforge.org/
Rakefile
Rakefile是由Ruby编写，Rake的命令执行就是由Rakefile文件定义。
In a gem's context, the Rakefile is extremely useful. It can hold various tasks to help building, testing and debugging your gem, among all other things that you might find useful.
详细： http://rake.rubyforge.org/files/doc/rakefile_rdoc.html
Bundle
相当于多个RubyGems批处理运行。在配置文件gemfilel里说明你的应用依赖哪些第三方包，他自动帮你下载安装多个包，并且会下载这些包依赖的包。
Bundler maintains a consistent environment for ruby applications. It tracks an application's code and the rubygems it needs to run, so that an application will always have the exact gems (and versions) that it needs to run.
```
