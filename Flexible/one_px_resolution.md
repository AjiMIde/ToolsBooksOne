## 1px 解决方案

#### 理解
* **移动端1px变粗**
* css中 1px 为抽象像素，不一定代表物理像素中的 1px 
* devicePixelRatio 属性表示设备物理像素和 css 像素的比例, 在 retina 屏的 iphone 手机上, 这个值为 2 或 3
* css 里写的 1px 长度渲染着物理像素上的 2px / 3px

#### 解决方案
* **小数点写 px**
* `优` 简单易理解 
* `缺` ios8 不支持，android 不支持
```less
@media screen and (-webkit-min-device-pixel-ratio: 2) {
    .border { border: 0.5px solid #999 } // .3333px when dpr = 3
}
```

* **border-image**
* `优` 无
* `缺` 无法更改颜色，圆角支持有限，限制性太大
```less
@media screen and (-webkit-min-device-pixel-ratio: 2){ 
    .border{ 
        border: 1px solid transparent;
        border-image: url(border.png) 2 0 repeat; // border.png 是一张两像素的图片，一个像素有颜色，一个像素透明
    }
}
```

* **css3 gradient 背景渐变**
* `优` 好理解，一个1px 的宽度，渐变为 .5 带颜色，.5 透明即可
* `缺` 代码量大、难维护、局限性、不支持圆角
```less
@media screen and (-webkit-min-device-pixel-ratio: 2){
    .ui-border-t {
        background-position: left top;
        background-image: -webkit-gradient(linear,left bottom,left top,color-stop(0.5,transparent),color-stop(0.5,#e0e0e0),to(#e0e0e0));
    }
}
```

* **after:before: transform**
* `优` 好理解，无非就是一个 1px 的元素进行 scale.5/scale.3333 来完全效果
* `缺` 维护难，会占据伪类，会冲突
```less
@media screen and (-webkit-min-device-pixel-ratio: 2){
    .radius-border:before{
        content: "";
        pointer-events: none; /* 防止点击触发 */
        box-sizing: border-box;
        position: absolute;
        width: 200%;
        height: 200%;
        left: 0;
        top: 0;
        border:1px solid;
        transform: scale(0.5);
    }
}
```

* **flexible.js** 
* `优` 无
* `缺` 无
