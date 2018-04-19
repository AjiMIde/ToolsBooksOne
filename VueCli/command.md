## Command

#### Installation
```bash
npm install -g @vue/cli
vue create my-project
```

#### Usage
```bash
vue <command> [option] 命令基础用法
vue <command> --help 查看某个命令的基础用法

* 命令
create [options] <app-name>      
invoke <plugin> [pluginOptions]  从已存在的项目中调用一个可用插件
inspect [options] [paths...]     检查 webpack config 
serve [options] [entry]          serve a .js or .vue file in development mode with zero config
build [options] [entry]          build a .js or .vue file in production mode with zero config
init <template> <app-name>       通过远程模板生成一个项目 ，老接口
```


#### Create project
```bash
  -p, --preset <presetName>       使用预设，从而跳过提示
  -d, --default                   使用默认预计，从而跳过提示
  -i, --inlinePreset <json>       使用 Json 字符串来跳过提示
  -m, --packageManager <command>  使用指定的 npm client 当安装依赖时
  -r, --registry <url>            使用指定的 npm registry 当安装依赖时
  -f, --force                     覆盖当前目录，当目录已经存在时
  -h, --help                      output usage information
```

#### Preset 预设 
* 当你选择了一些设置时，可以将其保存起来，以便重复使用
* 可通过编辑 .vuerc 来完成。preset 由 JSON 格式形成
```json
{
  "useConfigFiles": true,
  "router": true,
  "vuex": true,
  "cssPreprocessor": "sass",
  "plugins": {
    "@vue/cli-plugin-babel": {},
    "@vue/cli-plugin-eslint": {
      "config": "airbnb",
      "lintOn": ["save", "commit"]
    }
  }
```

* 插件生成器使用预设数据生成相应的项目文件。
* 除上述字段外，还可以为集成工具添加其他配置
```json
{
  "useConfigFiles": true,
  "plugins": {...},
  "configs": {
    "vue": {...},
    "postcss": {...},
    "eslintConfig": {...},
    "jest": {...}
  }
}
```

* 额外的配置顶会被 package.json 或对应的 config.js 文件合并进去，取决于 userConfigFiles 的值。
* 如当 "useConfigFiles": true, 则 `configs.vue` 会被合并到 `vue.config.js`

#### 预设插件版本
* 如配置插件的版本号。
* 这不是必须要做的，推荐的是，不做，让 vue-cli 自动选择最新的版本
```json
{
  "plugins": {
    "@vue/cli-plugin-eslint": {
      "version": "^3.0.0",
      // ... other options for this plugin
    }
  }
}
```

#### Remote Presets
* 在 git 上分享你的 preset 让别人使用（仓库中须包含 preset.json）
```bash
vue create --preset username/repo my-project

## GitLab and BitBucket are also supported. Make sure to use the --clone option if fetching from private repos:

vue create --preset gitlab:username/repo --clone my-project
vue create --preset bitbucket:username/repo --clone my-project
```


#### Zero-config Prototyping 0 配置原型
* 可快速地使用 `vue serve/vue build`命令来运行一个 vue 文件，但需要一个额外的插件
* 缺点是依赖全局的依赖文件(不同机器上)。因此只在快速原型上使用？
```bash
npm install -g @vue/cli-service-global

# vue serve
Usage: serve [options] [entry]
serve a .js or .vue file in development mode with zero config

Options:

  -o, --open  Open browser
  -h, --help  output usage information
```

#### 
