#### 基础命令
* 基础命令

```bash
npm -v                    查看npm 版本
npm update -g npm         更新 npm，-g 是全局的意思

#
npm init                             初使化项目

#
npm install <package-name>           安装包
npm i <package-name>                 简写

#
npm i --save <package-name>          安装插件到《产品依赖》下面dependencies
npm i <package-name> -S              简写

#
npm i --save-dev <package-name>      安装插件到《开发依赖》下面devDependencies
npm i <package-name> -D              简写

# 
npm i --save-optional <package-name> 安装插件到《自定义依赖》下面optionalDependencies
npm i <package-name> -O              简写

#
npm i <package-name>@version        安装指定版本插件

#
npm update <package-name>
npm uninstall xxx remove, rm, r, un, unlink 卸载某模块，也可以指定参数 --save-dev 等

#  
npm i                根据 package.json的依赖下载插件到node_modules
npm i --production   根据 package.json的《产品依赖》下载插件到 node_modules
npm ls               查看当下目录下所安装的包
npm help             查看帮助，可指定命令如：npm help install
npm ?  
npm root             查看 node_modules 路径
npm config           配置 npm
npm start            启动模块
npm restart          重启模块
npm stop             停止模块
npm test             测试模块

