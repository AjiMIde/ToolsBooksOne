## Webpack source map 配置

#### 配置：devtool 生成 source map

* 具体配置可查看：https://www.webpackjs.com/configuration/devtool/
* 每个配置项生成的代码品质及打包速度都是不一样的，需要根据需求和环境来选择不同的配置
* **开发环境下**适合使用：`eval, eval-source-map, cheap-eval-source-map`等 
* **生产环境下**适合使用：`none, source-map, hidden-source-map`等，注意，使用这些配置有可能生成`map`文件，注意部署时
* 不应将`map`文件部署到服务器上，或是不应让普通用户访问到`map`文件

```js
conf = {
  devtool: 'source-map',
  // 不指定：打包后的代码（强压缩，强混淆，一行）
  // eval：生成后的代码（源代码，只是生成后而已）
  // cheap-eval-source-map: 转化后的代码（换行后的源代码？）
  
  // inline-source-map: 打包后的代码（可定位到源文件位置，不生成.map文件，体积超大），
  // source-map: 会在打包目录下生成.map文件，(可定位到原位置，可用于生产）
  // 。。。
}
```

#### 使用`source-map-dev-tool-plugin`来生成`source-map`配置

* `SourceMapDevToolPlugin`提供了比`devtool`配置更细颗粒的配置选项，选择安装它并进行相关配置
* 详情见**98.the-plugins**

```js
new webpack.SourceMapDevToolPlugin({
  filename: '[name].js.map',
  exclude: ['vendor.js']
})
```
