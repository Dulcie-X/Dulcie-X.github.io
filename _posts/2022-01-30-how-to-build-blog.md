---
layout: post
title:  "如何用github搭建个人博客"
date:   2022-01-30 10:00:40
blurb: "简单记录利用github搭建博客的过程"
---

## 一、搭建基本页面
### 1. 在github上新建一个Repository
Repository name的格式必须为`username.GitHub.io`  
<img src="{{ "/assets/img/content/build-blog/create.png" | absolute_url }}" alt="bay" class="post-pic"/>

### 2. 修改设置
在Setting中找到`GitHub Pages`选项，先随意选择一个官方提供的主题
<img src="{{ "/assets/img/content/build-blog/setting.png" | absolute_url }}" alt="bay" class="post-pic"/>
<img src="{{ "/assets/img/content/build-blog/choose-theme.png" | absolute_url }}" alt="bay" class="post-pic"/>

### 3. 页面预览
在浏览器中输入之前填写的仓库名称，如：xiaomin.GitHub.io,即可看到之前搭建好的基本页面，目前还比较丑，因为是官方的样式，并且现在的页面是单页面无法跳转，所以接下来会介绍利用工具来进一步优化我们的博客
<img src="{{ "/assets/img/content/build-blog/my-page.png" | absolute_url }}" alt="bay" class="post-pic"/>

## 二、一个官方推荐的github page生成工具——Jekyll
为了让大家关注点放在博客的创作上，而非代码和页面样式的处理上。利用工具是很好的一个办法。而Jekyll就可以做到这一点  

因为Jekyll是基于Ruby的静态网页生成系统，因此我们得先安装Ruby环境，这里仅简单介绍在Mac上的安装方法。
### 1. 安装Ruby  
在Mac上可以通过Homebrew来进行安装，如果没有安装Homebrew，这里贴一个安装教程的链接：[Mac安装Homebrew的正确姿势](https://cloud.tencent.com/developer/article/1853162)  

```
brew install ruby
```
**小tip：在使用brew时可能会遇见报错提示：`zsh: command not found: brew`，这时大概率是环境变量配置不对，解决方案可参考[：command not found: brew的解决方案](https://blog.csdn.net/lyz21/article/details/114683483)

### 2. 安装Jekyll
在安装完Ruby后就可以安装Jekyll了，执行如下命令即可
```
gem install jekyll bundler
```
**小tip1：如果报错：`You don't have write permissions for the /Library/Ruby/Gems/2.3.0 directory`,可以在命令前加上sudo，当然也可以进行环境变量配置，就不在本文进行赘述了**

### 3. 接下来就是见证奇迹的一步啦～
进入到clone到本地的项目路径中，执行以下命令。项目中的目录会被替换掉，将代码推到远程仓库，再次访问页面即可
```
jekyll new . --force
```

## 三、继续美化博客
由于默认的界面看起来非常没有美感，因此网上也有很多模板，这里简单介绍一个：[jekyllthemes.org](http://jekyllthemes.org/)  
<img src="{{ "/assets/img/content/build-blog/jekyll.png" | absolute_url }}" alt="bay" class="post-pic"/>

安装方法很简单，一般情况下只需要下载主题包解压后完整的，复制到你的 GitHub Pages 的项目目录里，并覆盖你之前的文件即可，有些特殊的主题要参考作者给的安装步骤

一般常见的步骤为：
1.项目拷贝下来后执行`bundle install`安装依赖，但有可能失败，需要使用`bundle update`命令更新bundle，更新后再进行安装
2.使用`jekyll --server`或者`bundle exec jekyll serve`启动项目
3.步骤2有可能启动失败报错，需根据报错提示进行操作。如：在我本次使用中提示：“Please append `--trace` to the `serve` command for any additional information or backtrace”,因此我在启动命令后加上`--trace`,会得到`cannot load such file -- webrick`的报错。这是说缺少`webrick`这个包，使用`bundle add webrick`命令后，可以在Gemfile中发现增加了这个依赖，这时再启动项目就不会有问题啦～

主题里的所有关键性配置都在 _config.yml 文件中，你可以根据个人的喜好和不同主题支持的功能来修改具体的内容，这里就不做展开。大家可以慢慢进行摸索，因为我也还在摸索中……

至此所有的操作都已经结束，大家可以尽情发挥创作激情啦～

**最后的一个tip：文章的内容和标题需要按照 Jekyll 的格式进行，如下：**  
**文章的格式：**
```
年-月-日-标题.markdown
```
**文章内容顶部必须有下面的 YAML 头信息：**
```
---
layout: post
title: Blogging Like a Hacker
---
```

目前只是还不太完整的最基本的搭建，我再去多研究研究，后续学会新技能再进行补充……


---
