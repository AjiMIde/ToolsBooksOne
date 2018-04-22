## marked

#### Introduction
* 速度而生
* 低量级编译器，编译 `markdown` 无需缓存，不阻塞
* 轻量的同时支持 `markdown` 所有特性、风格、规范
* 浏览器、服务器、命令行 `CLI` 一侓支持
* 支持多种 markdown specification


#### Related Url
* [marked](https://marked.js.org/)
* [marked github: 16k starred](https://github.com/markedjs/marked)
* [marked.js documentation](https://marked.js.org/#/README.md#README.md)


#### Installation
```bash
npm i -g marked
# or
npm i marked --save
```

#### Usage
**CLI**
```bash
## 注意，这里好像是 linux/macOs 命令，故 window cmd.exe 好像行不通
marked -o hello.html
hello world
^D
$ cat hello.html
<p>hello world</p>
```
**Browser**
```js
let dom = document.getElementById('content')
dom.innerHTML = marked('# Marked in the browser\n\nRendered by **marked**.');
```

#### More 更多
**使用option**
```js
marked(markdownString [options], [callback]) // 后面两个为可选
```

**选项列表**

| 选项 | 类型 | 默认值 | desc | 
| --- | --- | --- | --- |
| baseUrl | ? | null | ? |
| breaks | bool | false | 换行符是否编译为 < br > 此选项需要 gfm 为 true |
| gfm | bool | false | 使用 Github Flavored Markdown? |
| headerIds | bool | true | 是否为 header 添加 id 属性？ |
| headerPrefix | str | '' | 为 header 标签添加 id 属性时，额外加上的前缀 |
| highlight | function |  | 高亮代码，可参考： Asynchronous highlighting |
| langPrefix | string | lang- | 默认为 lang- |
| mangle | bool | true | ?? |
| pedantic | bool | false | 尽可能地符合 `markdown.pl` 标准，不去修复 `markdown` 原来的 bugs 或行为。关闭此选项并覆盖 gfm |
| renderer | obj | new Renderer() | 一个对象，包含了函数，为了渲染 tokens 给 HTML，查看 `extensibility` 文档获取更多 |
| sanitize | bool |  |  |
| sanitizer | ? | null | ?? |
| silent | bool | false | ?? |
| smartlists | bool | true | 智能 list ? 来由于：`markdown.pl` |
| smartypants | bool | true | 智能标点符号？用于如：`quotes`, `dashes` |
| tables | bool |  | 使用 GFM 表格拓展，需要 gfm 为 true |
| xhtml | bool | false | 添加关闭标签，如 < br /> < img />，此选项专为 XHTML 使用 |


## 未完待补： 高亮问题~拓展问题~markdown 规范选项