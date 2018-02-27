## 基础命令

#### NPM（node package manager）
* 基础命令
```shell
npm -v                    查看npm 版本
npm update -g npm         更新 npm，-g 是全局的意思
npm init                  初使化项目
```
  
npm install --save XXX -S 安装插件到《产品依赖》下面dependencies
npm install xxx@version  安装指定版本插件
npm install --save-dev  XXX -D 安装插件到《开发依赖》下面devDependencies
npm install --save-optional XXX -O 安装插件到《自定义依赖》下面optionalDependencies
npm update xxx  
npm uninstall xxx remove, rm, r, un, unlink 卸载某模块，也可以指定参数 --save-dev 等
  
 npm install   根据 package.json的依赖下载插件到node_modules
 npm install --production   根据 package.json的《产品依赖》下载插件到 node_modules
npm ls   查看当下目录下所安装的包
     
 npm help  npm help ?  查看帮助，可指定命令如：npm help install
npm root   查看 node_modules 路径
npm config  配置 npm
npm start  启动模块
npm restart  重启模块
npm stop  停止模块
npm test  测试模块
  
  
  
  
  
  


配置淘宝 NPM

* 链接：htts://npm.taobao.org
* 优点：替代管理 npm ，速度快
* 安装：$ npm install -g cnpm --registry=https://registry.npm.taobao.org




