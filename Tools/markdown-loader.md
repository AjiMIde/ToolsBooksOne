## markdown-loader for webpack

#### Introduction
* `Webpack` 的一个 `loader`，专门用来编译 `markdown` 文件成 `html` 文件
* 基于 `marked.js` 构建
* 注意的是，此插件必须与 `html-loader` 一起使用
* [github markdown-loader](https://github.com/peerigon/markdown-loader)


#### 安装
```bash
npm i html-loader markdown-loader --save-dev
```

#### 使用(在 webpack 中配置，vue 项目同理)
```js
let c = {
  module: {
    rules: [{
      test: /\.md$/,
      use: [
        {
          loader: "html-loader"
        },
        {
          loader: "markdown-loader",
          options: {
            /* your options here , see marked get more*/
          }
        }
      ]
    }]
  }
}
```


#### 指定选项
```js
const marked = require("marked");
const renderer = new marked.Renderer();
 
return {
  module: {
   rules: [{
     test: /\.md$/,
     use: [
       {
         loader: "html-loader"
       },
       {
         loader: "markdown-loader",
         options: {
           pedantic: true,
           renderer
         }
       }
     ]
   }]
 }
}
```


