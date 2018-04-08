## flexible 使用

#### 背景
* flexible 由手淘开源的一个用于适应不同设备，不同屏幕（Retina）而开发的一款插件
* flexible 工作原理很简单，设置 html 根元素的 `font-size` 为某个 px 值，如 100px
* 然后其他元素使用 rem (根据根元素的 `font-size` 计算 px值) 来作元素的度量单位
* 当遇到高分屏时，则加大 html 根元素的 `font-size` 值（通常为倍数增加），并使用 viewport 的缩小同样倍数
* 来使得一单位的物理像素，能分配到一单位的 css 像素，达到高清显示的目的
* 目前 flexible 的版本有两个，一个老版本就是上面讲的这些，另一个是通过 viewport 的 vw/vh 单元进行缩放，接下来都会讲

#### 版本1
* 直接引入 `flexible.js`，插件会自动判断环境，加载 viewport 相关值 
* 判断 dpr 的大小，决定 `font-size` 的值，并设计 viewport，如：
    * dpr == 1 时
    * `<html data-dpr="1" style="font-size: 37.5px;">` `font-size`为 client-width * 1 / 10
    * `<meta name="viewport" content="initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no">`
    * dpr == 2 时
    * `<html data-dpr="2" style="font-size: 75px;">` `font-size`放大两倍，为 client-width * 2 / 10
    * `<meta name="viewport" content="initial-scale=0.5, maximum-scale=0.5, minimum-scale=0.5, user-scalable=no">` 缩放 .5倍
    * dpr == 3 时
    * `<html data-dpr="3" style="font-size: 124.2px;">` `font-size` 放大两部，为 client-width * 3 / 10
    * `<meta name="viewport" content="initial-scale=0.33333, maximum-scale=0.3333, minimum-scale=0.3333, user-scalable=no">` 缩放 .3333倍
* 将视觉稿中的 `px` 转为 `rem`
    * 一般会根据设计稿的原大小来定义 html 的 `font-size`，并将一份设计稿分为 100个单元a，另外 1rem = 10a
    * 750px的设计稿 = 100 * a = 10 * 10 * a = 10 * 1rem，则 1rem = 75px
    * 故此时 html font-size 为 75px，假设元素为 30px，则换算成 rem 为 30/75 rem
    * 利用这个公式，很容易换算 1080px 的设计稿
    * 1080px的设计稿 = 100 * a = 10 * 10 * a = 10 * 1rem，则 1rem = 108px
    * 故此时 html font-size 为 108px，假设元素为 30px，则换算成 rem 为 30/108 rem
* 至于上面的换算方法过于复杂，`flexible.js` 也有介绍一些换算工具，如 cssrem for sublimeText， px2rem for npm 等，可参考相关文档
* 此外，也可以在 sass/less 中定义宏、定义函数来解决相关计算

