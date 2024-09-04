# eslint-plugin-vue

* [eslint.vue](https://eslint.vuejs.org/)
* 这是`vue`项目绕不开的`eslint`插件
* 用于`vue2`和`vue3`

## 初使化

* 一般不单独安装，使用`eslint9`或`eslint8`时，提示安装

## 配置

* 由于`eslint9`现在是`flat`模式，所以你需要在`eslint.config.js`中配置`pluginVue`

```js
// in eslint.config.js，一般为 eslint 9+ 的配置
import pluginVue from "eslint-plugin-vue";

export default [
  ...pluginVue.configs["flat/essential"],
  // 以下两个选填 
  // 加强版
  ...pluginVue.configs["flat/strongly-recommended"],
  // 社区推荐版
  ...pluginVue.configs["flat/recommended"],
];
```

* `eslint8`需要在`eslintrc`中配置，叠个甲以后再补 todo

## webstorm 用法

* 在`setting`中找到`eslint`配置，注意，`eslint.config.js`是`eslint9`，所以`webstorm`需要`2024.01`以上版本
* 而且不能`auto find config`，还要`manual find config`手动添加

## rules

* 你可以在这里看到你想要全部的`eslint-plugin-vue`[规则列表](https://eslint.vuejs.org/rules)

## 验证

* 在`.vue`中整一个`vfor`，不指定`key`，此时`webstorm`会`tip error`，如果无，则有问题!
