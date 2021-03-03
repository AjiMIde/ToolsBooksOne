# Webpack

* [https://www.webpackjs.com 中文](https://www.webpackjs.com)
* [什么是`webpack`](#什么是webpack)
* [前端模块与`webpack`模块](#前端模块与webpack模块)
* [你需要掌握的](#你需要掌握的)
* [Feature](#Feature)

## 什么是webpack

* 一个现代的`js`应用程序静态模块打包器，通常来讲一个前端项目会包含各类如`js`文件、样式表`css`、图片、数据文件如`json`、`xml`等；
* `webpack`可以将这些资源处理成类`js`的模块（因为`webpack`通常来讲只认`javascript`；
* `webpack`同时构建一个依赖关系图，来根据模块间的依赖关系进行打包成一个或多个`bundle`；
* `webpack`不仅提供了一个打包生产的环境，也提供了一个高效率的开发环境、诸如**热更新**、**web服务**等；
* 关键词：**模块化**、**依赖打包**、**异步加载**


## 前端模块与webpack模块

* 在多年的前端发展过程过程中，出现了很多诸如`sea.js`、`require.js`等前端模块化工具，也提出了像`common.js`、`AMD`等模块的规范；
* 以及`ECMAScript`的`import/export`，还有像`css`中的`@import`等；
* `webpack`天然地对这些模块支持（无须第三方loader或plugin）；
* Webpack 有一个智能解析器，几乎可以处理任何第三方库，无论它们的模块形式是 CommonJS、 AMD 还是普通的 JS 文件。甚至在加载依赖的时候；
* **允许使用动态表达式 require("./templates/" + name + ".jade")**；


## 你需要掌握的

* 什么是`webpack`，`webpack`的基本使用，常用的`webpack`配置
* 常用的`plugin`, `loader`
* `Vue`的`webpack`打包配置，及修改`Vue webpack`的配置的方法；(`vue.config + webpack chain`)
* `React`的`webpack`打包配置，及修改`React webpack`的配置的方法；(`React Rewird`)

## Feature

* **代码拆分**
* Webpack 有两种组织模块依赖的方式，同步和异步。异步依赖作为分割点，形成一个新的块。在优化了依赖树后，每一个异步区块都作为一个文件被打包。
* **智能解析**
* **插件系统**
* Webpack 还有一个功能丰富的插件系统。大多数内容功能都是基于这个插件系统运行的，还可以开发和使用开源的 Webpack 插件，来满足各式各样的需求。
* **快速运行**
* Webpack 使用异步 I/O 和多级缓存提高运行效率，这使得 Webpack 能够以令人难以置信的速度快速增量编译。

