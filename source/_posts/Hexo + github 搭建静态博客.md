---
title: Hexo + github 搭建静态博客
date: 2016-12-28 10:08:46
tags:
---
2016年的年底，终于下定决心搭建一个技术博客。谈不上分享经验，就权当是自己的学习笔记吧。第一篇博客，当然是介绍博客是如何搭建的啦！

在继续阅读下文前，请先在本地安装Node、Git并完成相应配置，拥有GitHub账号！

具体步骤可以参考 [CrazyMilk](http://t.cn/R49kCIS) 的这篇文章。本文也是在该篇文章的基础上，记录了一些遇到的问题以及解决的方法。再次感谢 CrazyMilk！

既然题目叫做Hexo+github搭建静态博客，主要分成两个部分： Hexo本地初始化、git同步。

强调一下，本博客搭建时使用的node@v4.4.7、git@2.10.1、hexo@3.2.2、hexo-cli@1.0.2。

## Hexo本地初始化

参考 [Hexo官网](https://hexo.io/zh-cn/) 的安装步骤：

```

$ npm install hexo-cli -g

$ hexo init blog

$ cd blog

$ npm install

$ hexo server

```

首先安装hexo-cli，网上有一部分安装教程使用的都是早期的版本，不需要安装hexo-cli，哭...

接下来$ hexo init blog初始化hexo，blog是你存放hexo的文件夹名称，在何处运行就在何处生成blog文件夹。cd blog进入blog下的路径，执行npm install安装相应的依赖文件。hexo s启动服务器，成功后显示：

```

INFO Start processing

INFO Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.

```

## git同步（工程文件&静态文件）

在GitHub上先新建一个repo命名为username.github.io，默认分支为master（之后我们用来存放博客静态文件），再新建一个分支命名为Hexo（之后用来存放工程文件，保证无论到哪台电脑都可以clone工程文件到本地进行写作）并且在setting里updat为默认分支。

在blog文件夹以外任意路径执行：

```

$ git clone git@github.com:username/username.github.io.git

```

同步GitHub上的仓库到本地。之所以和参考文章的步骤不同，原因是在hexo init时会生成的.git 会覆盖clone时生成的.git 导致最后无法push到hexo分支存放工程文件。

解决的方法是，复制clone后生成的.git文件夹，返回blog并且覆盖.git。

接下来修改_config.yml（默认文件夹下，不是theme中的同名文件）：

```javascript

deploy:

type: git

repo: https://github.com/username/username.github.io.git

branch: master

```

repo是仓库地址，branch更改推送的分支为master。

接下来就可以愉快的写文章啦！写作方法可以直接看 [官方中文文档](https://hexo.io/zh-cn/docs/writing.html)。

有任何对工程文件的修改，依次执行git add .、git commit -m “…”、git push origin hexo 推送到hexo分之下存放。