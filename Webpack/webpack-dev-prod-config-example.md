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