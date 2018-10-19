## 模块系统

* 模块化编程，是将程序分解成离散功能块；
* 模块化的目的是实现高内聚、低耦合的程序，并使得程序易校验、调试、测试；
* 好的模块会有可靠的抽象和明显的封装界限，有着明确的设计目的；

#### CommonJs

* 通常以 `exports/module.exports` 来导出暴露接口；
* 通常以 `require` 来同步加载其他接口；
* 代表框架：`Node.js`
* 注意：Npm的包大都基于此规范(亦有支持 ES6 模块的)；
* 注意：CommonJs 通常只用于服务端的 `Node.js` （同步）而不能用于浏览器（会造成加载的阻塞）
```js
exports.doStuff = function() {};
module.exports = someValue;

require("module");
require("../file.js");
```


#### ES6 模块

* 以 `export` 来暴露接口；
* 以 `import` 来加载接口；
* ES6 模块的设计思想，是尽量的静态化，使得编译时就能确定模块的依赖关系，以及输入和输出的变量。
* CommonJS 和 AMD 模块，都只能在运行时确定这些东西。
```js
import "jquery";

export function doStuff() {}
export default function doStuff() {}
```
* **优点：**
* 容易进行静态分析
* 面向未来的 ECMAScript 标准
* **缺点：**
* 原生浏览器端还没有实现该标准
* 全新的命令字，新版的 Node.js才支持


#### AMD Asynchronous Module Definition 

* 以 `define` 来定义接口；
* 以 `require` 来引用接口；
* 在声明模块的时候指定所有的依赖 dependencies，并且还要当做形参传到 factory 中；
* 对于依赖的模块提前执行，依赖前置；
* 优点：适合在浏览器环境中异步加载模块；
* 优点：可以并行加载多个模块；
* 缺点：提高了开发成本，代码的阅读和书写比较困难，模块定义方式的语义不顺畅；
* 缺点：不符合通用的模块化思维方式，是一种妥协的实现；
* RequireJS 就是基于 `AMD` 去实现的架构；
* curl

```js
define("module", ["dep1", "dep2"], function(d1, d2) {
  return someExportedValue;
});
require(["module", "../file"], function(module, file) { /* ... */ });
```


#### CMD Common Module Definition 
* 与 AMD 很相似，并同时兼容的 `CommonJs` 中的规范；
* 依赖就近，与 `AMD` 不同，`AMD` 是依赖前置；
* 可以在 `Node.js` 中执行；
* 实现：`Sea.js` 就是基于此规范组织架构的；

```js
define(function(require, exports, module) {
  var $ = require('jquery');
  var Spinning = require('./spinning');
  exports.doSomething = ''
  module.exports = ''
})
```


