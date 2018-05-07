## webpack node server 在本地局域网内打开

#### 原因和方法 
> webpack node server 一般只配置在 localhost/127.0.0.1 打开程序，而无法在局域网内，如
> 10.10.10.20:8888/index.html 打开程序，修改配置即可

打开 index.js 修改配置

```js 
dev: {
    host: 'localhost', // 修改成 0.0.0.0
    env: require('./dev.env'),
    port: 8081,
    autoOpenBrowser: true,
    assetsSubDirectory: 'static',
    assetsPublicPath: '/',
    proxyTable: {},
}
```

