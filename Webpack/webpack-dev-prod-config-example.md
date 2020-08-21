#### 安装

* 安装下列npm包

```js
// 建议使用下面的json序列下载npm包
conf = {
  "clean-webpack-plugin": "^3.0.0",
  "css-loader": "^4.2.0",
  "file-loader": "^6.0.0",
  "html-webpack-plugin": "^4.3.0",
  "image-webpack-loader": "^6.0.0",
  
  "sass": "^1.26.10",
  "sass-loader": "^9.0.3",
  "style-loader": "^1.2.1",
  "url-loader": "^4.1.0",
  
  "webpack": "^4.44.1",
  "webpack-cli": "^3.3.12",
  "webpack-dev-server": "^3.11.0",
  "webpack-manifest-plugin": "^2.2.0",
  "webpack-merge": "^5.1.1"
}
```

#### webpack.commom.js

```js

```

```js
// dev.js
const HtmlWebpackPlugin = require('html-webpack-plugin')
const {CleanWebpackPlugin} = require('clean-webpack-plugin')
const ManifestPlugin = require('webpack-manifest-plugin')
const webpack = require('webpack')

const path = require('path');

module.exports = {
  devtool: '',

  devServer: {
    contentBase: './dist',
    historyApiFallback: true,
    overlay: true,
    watchContentBase: true,
    host: '0.0.0.0',
    open: true,
    useLocalIp: true,

    hot: true, // 启用热更
  },

  entry: {
    index: './src/index.js',
    app: './src/app.js'
  },
  plugins: [
    new CleanWebpackPlugin(),
    new ManifestPlugin(),
    new HtmlWebpackPlugin(),

    new webpack.NamedModulesPlugin(),
    new webpack.HotModuleReplacementPlugin()
  ],
  output: {
    filename: '[name].[hash].js',
    path: path.resolve(__dirname, 'dist')
  },
  module: {
    rules: [
      {
        test: /\.(css|s[ac]ss)$/,
        use: ['style-loader', 'css-loader', 'sass-loader']
      },
      {
        test: /\.(png|svg|jpg|gif)$/,
        use: [
          {
            loader: 'url-loader',
            options: {
              limit: 8192
            }
          },
          {
            loader: 'image-webpack-loader',
            options: {
              // disable: true, // webpack@2.x and newer
            }
          }
        ]
      },
      // {
      //   test: /\.json$/,
      //   user: ['file-loader']
      // }
    ]
  },
}
```