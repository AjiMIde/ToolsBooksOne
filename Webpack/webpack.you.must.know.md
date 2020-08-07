## Webpack须知

#### 模块化

我们知道`webpack`支持基本上现在`JavaScript`世界流行的各种模块化语言的结构，如`require.js, AMD, CMD, Common.js`
这些模块化语法提供了开箱即用的体验，如以下：

```js
//main.js
import _ from 'lodash'
_.join(['a', 'b', 'c'])
```

上面的语法，是可以直接被打包的，此外还有`Common.js`

```js
const _ = require('lodash')
```

当然了，更多的`ES6`特性的语法或其他的，需要自行添加各式各样的`loader`来打包

更多详情，请点击：[https://www.webpackjs.com/api/module-methods/](https://www.webpackjs.com/api/module-methods/)

