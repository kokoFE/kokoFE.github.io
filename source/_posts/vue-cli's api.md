---
title: vue-cli's api
date: 2017-02-05 17:57:50
tags:
---
网上关于vue的入门文章，通常都是以安装开发环境开始：
安装node，npm注册淘宝镜像，安装vue-cli脚手架工具，使用vue-cli初始化项目：
```
vue init webpack-simple yourProjectName
```
那vue-cli就那么简单？没有其他可以配置的地方？直到一次初始化项目时，多了很多配置选项...并且之后执行npm run dev报错了...还是去github上看一下文档吧，传送门：
>[github vue-cli](https://github.com/vuejs/vue-cli)

# 总结
## 用法
```
vue init <template-name> <project-name>
```
## 例子
```
vue init webpack my-project
```
## 官方模板
1. webpack - 使用完整的webpack + vue-loader，包含热加载、校验、测试以及css提取等设置。
2. webpack-simple 使用部分webpack功能，结合vue-loader，快速搭建项目原型。
3. browserify 相当于第一点，只不过使用的browserify。
4. browserify-simple 相当于第二点，只不过使用的browserify。
5. simple 使用单个HTML文件开发，拥有最简单的设置。
6. add
## 定制模板
