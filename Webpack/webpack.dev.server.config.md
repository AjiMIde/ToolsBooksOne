## Webpack dev server 配置说明

* `npm i -D webpack-dev-server`

```js
conf = {
  devServer: {
    port: 8080,    // 或--port 8080
    
    // 重要的配置
    // 可使用 'dist', [path.join(__dirname, 'dist'), ...so on] 多个入口，或直接 false
    // 或使用命令行 --content-base directory-name
    contentBase: path.join(__dirname, 'dist'),
    compress: true,     // 启用g-zip压缩
    allowedHost: [],    // 可访问的服务器的白名单 
    // 可能的值有 none, error, warning 或者 info（默认值），热更新时，会根据此级别来显示相关信息
    clientLogLevel: 'none', 
    headers: { 'X-Custom-Foo': 'bar'}, // 往所有的请求添加此头部
    historyApiFallback: true,          // boolean 或 object，当404时重定向到 index.html
    historyApiFallback2: {             // 或为object进行细致的重定向
       rewrites: [ { from: /^\/$/, to: '/views/landing.html' } ]
    },
    hot: true,          // 启用热更新（热重载），注意！需要引入 HotModuleReplacementPlugin 
    hotOnly: true,      // 启用不刷新页面的热更新
    host: "0.0.0.0",    // 默认为 localhost，当想让外部访问或使用本地局域网打开时，须配置此为 0.0.0.0
    https: true,        // 启用 https，或是 object 来提供自己的证书
    https2: {
      key: fs.readFileSync("/path/to/server.key"),
      cert: fs.readFileSync("/path/to/server.crt"),
      ca: fs.readFileSync("/path/to/ca.pem"),
    },
    index: 'index.htm',       // 默认服务器打开的html文件
    lazy: false,              // --lazy当启用时，文件只有被获取时才编译（而非保存编译noInfo ）
    noInfo: false,            // 启用时，只有编译警告和错误的信息会被显示
    open: false,              // 自动打开浏览器，或 --open 或 --open 'Google Chrome'
    openPage: '',             // 指定打开目录下的哪个文件，或 --open-page '/dir/name.html'
    overlay: true,            // 当编译错误或警告时，显示全遮罩的提示，也可以用object
    overlay2: {
      warnings: true,
      errors: true
    },
    // 代理，这是一个比较重要的概念，使用 proxy 能在当前前后端分离流行的趋势下更好的梳理代码与环境结构
    // webpack dev server 使用了http-proxy-middleware这个包来完成代理的工作，查看相关配置和文档完成
    // 更出色的工作 
    proxy: {
      "/api": "http://localhost:3000"
    },
    public: "myapp.test:80",      // 在使用代理时有用
    publicPath: "",               // 指定可访问的目录
    useLocalIp: true,             // 当true时，使用本地 ip 打开服务，须与 host 配置使用
    watchContentBase: true,       // 当true时，页面会整个刷新当你改文件的时候
    watchOptions: {},
    
    
    // 函数方法
    after: app => { // 在这里可以使用其他中间件 // do sth
    },
    before: app => {},// 同上
    
    // 不清楚用途，或不重要的
    bonjour: true,            // 可使用 webpack-dev-server --bonjour
    color: '?',               // 仅可通过 --color使用
    disableHostCheck: true,   // DNS主机攻击？
    filename: 'bundle.js',    // 须结合 lazy:true使用，当访问bundle.js时才编译此文件，但？只能配置为 string?
    info: '?',                // 仅可通过 --info，默认已启用
    inline: false,            // ?? --inline=false 信息构建？
    pfx: '/path/to/file.pfx',     // ?? 与https有关？
    pfxPassphrase: 'passphrase',  // 同上
    progress: '?',                // --progress
    quiet: true,                  // 或 --quiet
    setup: function() { },        
    socket: '',
    staticOptions: {},
    stats: '',
  }
}
```

* 注意，在启用服务后，可通过：`host:port/webpack-dev-server`来获取当前`dev-server`服务下有哪些文件


#### 使用 http-proxy-middleware 进行代理
     
* 需求是在使用开发服务器时使用后台 API。为此，我们能并行地运行开发服务器和 API后台（或远程地运行）
* 并且可让开发服务器代理所有的真实后台的API请求。
* 配置代理规则，请编辑 `config.js` 中的 `dev.proxyTable` 选项。
* 代理服务器是使用[http-proxy-middleware](https://github.com/chimurai/http-proxy-middleware)
* 进行代理的，固请参阅它的文档获得更多使用细节。这里有个简单的：
```js
  // config.js
  module.exports = {
       // ...
   dev: {
     proxyTable: {
       // proxy all requests starting with /api to jsonplaceholder
       '/api': {
         target: 'http://jsonplaceholder.typicode.com',
         changeOrigin: true,
         pathRewrite: {
           '^/api': ''
         }
       }
     }
   }
  }
```

