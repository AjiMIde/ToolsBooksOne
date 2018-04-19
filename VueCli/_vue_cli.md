## vue-cli

#### 简介 

> vue-cli 是用来创建整个 vue 项目的开发体系的工具命令行，包括

* 交互式的项目脚手架
* 快速从 0 构建 vue 项目原型
* 运行环境从属
    * 可升级
    * webpack 构建，自带好用的基础配置
    * 通过 config 文件配置
    * 通过插件拓展
* 一堆丰富的官方插件集合了前端生态系统中的最佳工具。    
* vue cli旨在成为vue生态系统的标准工具基准。
* 它可以确保各种构建工具的顺利运行以及搭配了合理的默认设置，因此您可以专注于编写应用程序，而不用花费时间与配置进行争论 。
* 与此同时，它仍然可以灵活地调整每个工具的配置。

#### 安装 
```bash
* npm install -g @vue/cli
* vue create my-project
```

#### 项目约定
> 通过 vue-cli 构建的项目，有以下约定


##### index.html
* `index.html`文件会被 `html-webpack-plugin`当成模板处理。
* 处理期间，资源会被自动注入，此外，`vue-cli` 会自动注入预处理/预读 的资源，并处理一些图标、清单等


##### 静态资源
* 静态资源，会被以下两种方法处理：
* 通过相对路径引入、然后被 `webpack` 处理掉
* 放在公共路径下，不通过 `webpack` 简单复制地使用
* 详情看(重要) [处理静态资源](https://github.com/vuejs/vue-cli/blob/dev/docs/assets.md)


##### 环境变量及模式
* 普通来说，都是通过控制环境来自定制 app 的行为的，如需要在不同的环境（开发、生产）配置不同的 Api 结节或凭据
* `vue-cli` 能全面支持指定不同环境的变量参数（通过配置 .env files 、 modes参数等）
* 详情看（重要）[环境参数配置](https://github.com/vuejs/vue-cli/blob/dev/docs/env.md)


##### 配置
* 通过 `vue create` 创建的项目就能达到开箱即用，所有的插件都被设计成能协调使用的状态，只需要在创建时选择选项即可。
* 当然，项目、需求都是多变的，你可以随时修改配置。


##### Vue.config.js
* `vue.cli`项目构建，可以在根目录下放一个 vue.config.js 来配置。像这样：(node.js写法)
* 了解更多： [vue.config.js](https://github.com/vuejs/vue-cli/blob/dev/docs/config.md)
```js
// vue.config.js
module.exports = {
  lintOnSave: true
}
```


##### Webpack
* 最常的，更改配置，当然是通过更改 webpack 配置来实现
* [vue webpack config](https://github.com/vuejs/vue-cli/blob/dev/docs/webpack.md)


##### browserslist 浏览器列表 
* package.json 指定了浏览器列表。该值会被 `babel-preset-env` 和 `autoprefixer` 自动发现被使用在 `JavaScript polyfills`和`CSS vendor prefixes`css 自动前缀上。
* 查看详细 [browserlist](https://github.com/ai/browserslist)


##### Dev Server proxy 开发服务器代理
* 如果你的前后端分离中，且不在同一个域名下，你需要在开发期间做 Api 代理请求
* 通过 `vue.config.js` 中的 `devServer.proxy`配置即可完成
* 查看 [Dev server proxy](https://github.com/vuejs/vue-cli/blob/dev/docs/cli-service.md#configuring-proxy)


##### Babel
* 通过 `.babelrc` 或 `babel field in package.json`配置.
* 所有 Vue Cli 程序都通过 `@vue/babel-preset-app` 配置，包括了 `babel-preset-env`, `JSX`, `减少包配置大小`
* 查看详情 [Babel](https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/babel-preset-app)


##### CSS
* `Vue CLI` 支持 `PostCSS`, `CSS Modules` and `pre-processors` 如 `Sass`, `Less` 及 `Stylus`
* [css](https://github.com/vuejs/vue-cli/blob/dev/docs/css.md)


##### ESLint
* 通过 `.eslintrc` 或 `eslintConfig field in package.json` 配置 EsLint.
* 看 [cli-plugin-eslint](https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint)


##### TypeScript
* 通过 `tsconfig.json` 配置细节 
* 查看 [cli-plugin-typescript](https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-typescript)


##### Unit Testing
* Jest
* [vue/cli-plugin-unit-jest](https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-unit-jest)
* --
* Mocha (via mocha-webpack)
* [vue/cli-plugin-unit-mocha](https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-unit-mocha)


#####  E2E Testing
* Cypress
* [vue/cli-plugin-e2e-cypress](https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-e2e-cypress)
* --
* Nightwatch
* [vue/cli-plugin-e2e-nightwatch](https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-e2e-nightwatch)
* --
* Development
* [Contributing Guide](https://github.com/vuejs/vue-cli/blob/dev/.github/CONTRIBUTING.md)
* [Plugin Development Guide](https://github.com/vuejs/vue-cli/blob/dev/docs/plugin-dev.md)