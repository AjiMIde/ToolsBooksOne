## Webpack

#### 参考：

* [https://www.webpackjs.com 中文](https://www.webpackjs.com)


#### vita

* 什么是`webpack`
* 为何使用`webpack`而不是其他
* 什么是`webpack`的入口文件
* 什么是`webpack`的出口文件   
* 解释下`loader`
* 解释下`plugins`
* 解释下前端模块或`webpack`模块



* 什么是`webpack`
    * 一个现代的`js`应用程序静态模块打包器，通常来讲一个前端项目会包含各类如`js`文件、样式表`css`、图片、数据文件如`json`、`xml`等；
    * `webpack`可以将这些资源处理成类`js`的模块（因为`webpack`通常来讲只认`javascript`；
    * `webpack`同时构建一个依赖关系图，来根据模块间的依赖关系进行打包成一个或多个`bundle`；
    * `webpack`不仅提供了一个打包生产的环境，也提供了一个高效率的开发环境、诸如**热更新**、**web服务**等；
    * 关键词：**模块化**、**依赖打包**、**异步加载**
* 为何使用`webpack`而不是其他
    * 与其他工具相比，像`grunt gulp`相比，`webpack`提供了面向多个模块语言的打包选项如`common.js, Es6, AMD`等，
    * `webpack`强调了开发、生产两套环境，比起`grunt gulp`后两者更像是工作流工具（对形成大项目开发来讲太过薄弱）
    * 流行、稳定、内容多是`webpack`的一大优势
* 什么是`webpack`的入口文件
    * `entry`也可认为是`webpack`的打包入口，即一个程序最先从哪里开始启动的；
    * `entry`指引了`webpack`是从哪个文件开始构建依赖关系的；
* 什么是`webpack`的出口文件   
    * `bundle`即`webpack`的出口文件，即打包完成后的文件，可通过配置来完成一些像**样式表**、**图片**、**公用模块**的不同`bundles`；
* 解释下`loader`
    * 由于 `webpack` 只认识（处理）`JavaScript`文件，固，非`JavaScript`文件的，需要使用`loader`处理成`webpack`能处理的模块；
* 解释下`plugins`
    * `loader` 用于处理模块，而`plugins`则用来执行更多任务，如打包优化、压缩、定义环境变量等等；
    
    
    
* 解释下前端模块或`webpack`模块
    * 在多年的前端发展过程过程中，出现了很多诸如`sea.js`、`require.js`等前端模块化工具，也提出了像`common.js`、`AMD`等模块的规范；
    * 以及`ECMAScript`的`import/export`，还有像`css`中的`@import`等；
    * `webpack`天然地对这些模块支持（无须第三方loader或plugin）；
    * Webpack 有一个智能解析器，几乎可以处理任何第三方库，无论它们的模块形式是 CommonJS、 AMD 还是普通的 JS 文件。甚至在加载依赖的时候；
    * **允许使用动态表达式 require("./templates/" + name + ".jade")**；


#### Feature
* **代码拆分**
* Webpack 有两种组织模块依赖的方式，同步和异步。异步依赖作为分割点，形成一个新的块。在优化了依赖树后，每一个异步区块都作为一个文件被打包。
* **智能解析**
* **插件系统**
* Webpack 还有一个功能丰富的插件系统。大多数内容功能都是基于这个插件系统运行的，还可以开发和使用开源的 Webpack 插件，来满足各式各样的需求。
* **快速运行**
* Webpack 使用异步 I/O 和多级缓存提高运行效率，这使得 Webpack 能够以令人难以置信的速度快速增量编译。


