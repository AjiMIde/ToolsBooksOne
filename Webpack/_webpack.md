## Webpack

#### 参考：
* [https://www.webpackjs.com 中文](https://www.webpackjs.com)
* [https://zhaoda.gitbooks.io/webpack](https://zhaoda.gitbooks.io/webpack)


#### Description
* Webpack 是一个现代 JS 应用程序的静态模块打包器
* 打包程序时，构建一个依赖关系图，将模块打包成一个或多个 bundle (查看 `webpack模块` 小节)
* 前端资源模块化管理和打包工具；
* 将许多松散的模块按照依赖和规则打包成符合生产环境部署的前端资源；
* 实现加载模块，实现代码分隔，实现异步加载；
* 通过 loader 的转换，任何形式的资源都可以视作模块，比如 CommonJs 模块、 AMD 模块、 ES6 模块、CSS、图片、 JSON、Coffeescript、 LESS 等；


#### 入口文件
* 指示 `webpack` 首先因为使用哪个模块，来构建它的内部模块依赖图；
* 即通过入口文件来一步步索引哪些模块需要被打包处理，最后输出到 `bundles`


#### 出口 output
* 指示 `webpack` 在哪里输出它创建的 `bundles`，默认值为 `dist`


#### loader
* 由于 `webpack` 只认识（处理）`JavaScript`文件，固，非`JavaScript`文件的，需要使用`loader`处理成`webpack`能处理的模块；


#### 插件 plugins
* `loader` 用于处理模块，而`plugins`则用来执行更多任务，如打包优化、压缩、定义环境变量等等；


#### 模式
* 根据 `mode` 参数的值不同，启用相应模块下的 `webpack` 内置优化；
```js
module.exports = {
  mode: 'production'  // or development
}
```


#### Feature
* **代码拆分**
* Webpack 有两种组织模块依赖的方式，同步和异步。异步依赖作为分割点，形成一个新的块。在优化了依赖树后，每一个异步区块都作为一个文件被打包。
* **Loader** 
* Webpack 本身只能处理原生的 JavaScript 模块，但是 loader 转换器可以将各种类型的资源转换成 JavaScript 模块。这样，任何资源都可以成为 Webpack 可以处理的模块。
* **智能解析**
* Webpack 有一个智能解析器，几乎可以处理任何第三方库，无论它们的模块形式是 CommonJS、 AMD 还是普通的 JS 文件。甚至在加载依赖的时候，允许使用动态表达式 require("./templates/" + name + ".jade")。
* **插件系统**
* Webpack 还有一个功能丰富的插件系统。大多数内容功能都是基于这个插件系统运行的，还可以开发和使用开源的 Webpack 插件，来满足各式各样的需求。
* **快速运行**
* Webpack 使用异步 I/O 和多级缓存提高运行效率，这使得 Webpack 能够以令人难以置信的速度快速增量编译。



