## Webpack template for vue.js

* 自带 webpack, hot-reload, lint-on-save, unit testing, css 拓展
* For large, serious projects 
* 需要提前熟悉 Vue-loader, webpack 等插件/框架
* 文档：[vue template webpack](http://vuejs-templates.github.io/webpack/commands.html)

#### Installation
```bash
vue init webpack my project

#....and so on...prompts

npm run dev
```

* 默认使用 master 分支，使用其他分支，看文档


#### 项目结构
```
.
├── build/                      # webpack config files 这个目录配置了开发服务器和 webpack的相关生产配置，一般不修改
│   └── ...                         除非你想定义 webpack loader，那此时应该操作 webpack.base.conf.js
├── config/
│   ├── index.js                # main project config  主配置文件，最常用的构建配置，查看 Api 代理和 后端框架 来获取更多细节
│   └── ...
├── src/                        # 基本上的开发代码都在这里，如何组织随你发挥。如何使用 vuex，注意去查看相关的。
│   ├── main.js                 # app entry file app 入口文件，即开发的主要对象
│   ├── App.vue                 # main app component 主要的入口 vue 组件
│   ├── components/             # ui components 自定义的 vue 组件，都放在这里
│   │   └── ...
│   └── assets/                 # module assets (processed by webpack) 自定义的资源集合
│       └── ...
├── static/                     # pure static assets (directly copied) 静态输出的资源集，运行环境就用这个，无需自己动手处理
├── test/
│   └── unit/                   # unit tests    单元测试
│   │   ├── specs/              # test spec files
│   │   ├── eslintrc            # 针对单元测试的额外 eslint 配置
│   │   ├── index.js            # test build entry file
│   │   ├── jest.conf.js        # jest 单元测试配置文件
│   │   ├── karma.conf.js       # test runner config file
│   │   └── setup.js            # jest 会先跑此文件，再跑你的单元测试
│   └── e2e/                    # e2e tests end-to-end test
│   │   ├── specs/              # test spec files
│   │   ├── custom-assertions/  # custom assertions for e2e tests
│   │   ├── runner.js           # test runner script
│   │   └── nightwatch.conf.js  # test runner config file
├── .babelrc                    # babel config          babel运行时的配置
├── .editorconfig.js            # editor config         编辑器的配置？？
├── .eslintrc.js                # eslint config         eslint检测
├── .eslintignore               # eslint 忽略规则
├── index.html                  # index.html template   index.html 模板，单页面程序的入口，相关的组件、资源等等都会自动注入到此 html 文件里面去
└── package.json                # build scripts and dependencies
└── README.md
```

##### 文件（夹）详细解析 

##### build/
> 包含了很多的开发、生产的配置荐，一般不需要修改到，除非你要自定制，如有需要，你可能会对 `build/webpack.base.confg.js` 进行操作

##### config/index.js
> `build setup` 最多的配置项都来自于此文件。在后面的章节 `开发阶段 API 代理` 及 `整合后台框架` 会有涉及

##### src/
> 开发代码都居于此。您自由打算

##### static/
> 此文件夹存放静态资源（不想被 webpack 处理掉的资源）。他们会被直接复制到相同的文件夹。下面会讲到

##### test/unit
> 单元测试

##### test/e2e
> e2e 测试

##### index.html
> 此文件为我们单页面应用程序的 `index.html` 模板。开发亦或生产，webpack 都会生成资源集、URLs 并自动注入到这里

##### package.json
> Npm 包、meta 文件包含所有的 build 依赖 及 `build commands`


#### 构建命令

> 所有的命令都通过 [npm 脚本命令执行](https://docs.npmjs.com/misc/scripts)

* `npm run dev`
    * `webpack` + `vue-loader` 来应付 `.vue` 文件
    * 热更新
    * 错误提示
    * ESLint
    * Source Maps
    
* `npm run build` 提供生产版本
    * `UglifyJs v3` 提供 js 压缩
    * `html-minifier` 提供 html 压缩
    * `cssnano` 提供了 css 压缩、提取、生成到单一文件
    * 静态资源输出成带 hash 版本号的文件，以方便长期缓存，并自动生成产品模式下的 `index.html` 及对应正确的链接
    * `npm run build --report` 获取 build analytics
    
* `npm run unit` 单元测试，提供了 jest/karma + mocha + karma-webpack    
    * 测试文件支持 `ES6`
    * 简单模拟
    
* `npm run e2e` 端到端的 `Nightwatch` 测试
    * 多个浏览器间的平行测试
    * 一个命令，开箱即用
        * Selenium 和 chromedriver 依赖自动控制
        * 自动化的 Selenium Server
        
* `npm run Lint`        
    * 检查代码
    

#### Babel Configuration 
* 此模板使用 `babel-preset-evn` 来配置 `babel`，点此[了解更多](http://2ality.com/2017/02/babel-preset-env.html)
* `Babel`预设将自动根据 `Babel 插件` 及 `polyfills`(设成你的目标浏览器或运行环境) 来将 `ES2015+`编译成 `ES5`
* 它使用 `browserslist` 来编译这些信息，故我们可用任何 `browserslist`所支持的值
* 不过这是个警告行为，`browserslist 建议定义目标值在 `package.json` 或`.browserslistrc` 配置文件中
* 这可以允许像 `autoprefixer` 及 `eslint-plugin-compat` 来分享配置，如以下（定义在 `package.json`）
```json
{
  "...": "...",
  "browserslist": [
    "> 1%",
    "last 2 versions",
    "not ie <= 8"
  ]
}
```
* 但最新发布的 `babel-preset-dev` v1.6.1 不支持从 `package.json` 中读取值。
* 故目标环境将在 `.babelrc` 中读取，如果你要改变你的目标环境，注意同时更新 `package.json` 和 `.babelrc`
* 注意，下个版本 `babel/preset-env@7.0.0.0-bata.34` 将会解决此问题，同时模板也会更新

* 未完待续 http://vuejs-templates.github.io/webpack/linter.html
