---
title: "Setup Github Page"
categories:
  - Github
tags:
  - Blog
  - Github Page
  - Web 
  - Github
---

#  如何设置github page Jekyll 页面

## 假定以下前提：
 * 有Github账号
 * 在windowns平台下
 * 已安装Github Desktop

---

# 前言：
相信各位从事IT有做笔记习惯的人都习惯使用Markdown来写，可很多时候需要各种辅助软件来编辑和预览。跨平台和分享有时候会因为软件的限制不那么方便。

而Github作为一个开源社区也很慷慨的提供了一个免费的静态博客平台，复杂度比自己做服务器运行博客要简易的多，相对于各网站的内置博客平台也有着更多的开放度。因为各种原因使得Github Page成为搭建个人博客的首选。

如果使用Github Page搭建博客会有两个问题： 1. 如和高效的同步自己的笔记  2.如何快速搭建平台


----


## 步骤:

### 1. 找个准备copy的案例
如果是自己写Jekyll或者通过html来写一个基本的博客平台对于新手来讲就很困难，而且可能需要一周多的时间来进行完善，显然这并不太符合我们的需求。
文章这里通过clone开源的Jekyll案例通过修改设置来快速搭建自己的博客平台。 
总用时：约3小时(完全无基础)
找到一个自己喜欢的Jekyll案例
这里以 Minimal Mistakes 为例
https://github.com/mmistakes/minimal-mistakes

<img src="https://github.com/mmistakes/minimal-mistakes/raw/master/screenshot-layouts.png">

这个案例个人还是比较喜欢的，有清晰的结构 能很方便的查看文章的内容。

### 2. Clone 到自己的Github
https://github.com/mmistakes/minimal-mistakes


### 3. 在Github设置 Github Page
新建 Repo 
Repo 的名字设置为 (你的用户名).github.io


### 4. 将repo同步到本地
打开Github Desktop
File - Clone repo - 分别Clone 你的Github Page repo 和 minimal-mistakes


### 5. 复制案例到自己的Github Page
打开repo在本地的位置 将Minimal-mistakes里的文件复制到自己GithubPage的本地文件夹里


### 6. Push到Github 
回到Github Desktop, 切换到Github Page repo， 点击Commit来确认文件的更改， 然后点击菜单栏的Repository-Push(Ctrl+P) 将所有的文件Push到Github.
这时候如果在浏览器输入 (你的用户名).github.io 就能看到自己初始化出来的博客了。

不过这时候所有的内容还是空的。下面就继续来进行设置。


### 7. 设置主页
这时候可以进入网页进行编辑设置: 打开自己的Github主站进入自己的GithubPage Repo 点击进入 _config.yml

也可以在本地文件打开 _config.yml 用Atom或自己常用的编辑器来编辑。

通过编辑个人名字，个人邮箱等便可以将博客信息更改成为自己的。


### 8. 如何添加博文
到这里基本的主页已经搭建完成了，如果想要添加文章的话，需要在_posts这个文件夹里添加页面

注意！ 新建的页面必须以[年-月-日-文章名.md]来命名！


### 到这里你已经可以进行基本的博文编辑并显示了

记得在编辑或上传完文章后点击 保存(web)或者Push到github(Github Desktop)

----








