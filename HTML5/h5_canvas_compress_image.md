## HTML5 canvas 上传图片时压缩

#### 原理与要点
* [canvas](https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial)
* [FileReader](https://developer.mozilla.org/zh-CN/docs/Web/API/FileReader)
* [Image](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLImageElement/Image)
* 1. 通过读取 input file 上的文件对象，将对象使用 fileReader 读成 base64 格式
* 2. 将上面读下来的 base64 格式的数据，挂载到一个 Image 对象上
* 3. 绘制一下固定大小的 canvas (要压缩的大小)，根据上面的 image 对象进行宽、高比例的获取
* 4. 将宽、高、image 对象都绘制到 canvas 上
* 5. 读取 canvas 对象的 blob 数据，将数据上传

#### 参考 
* [张鑫旭](http://www.zhangxinxu.com/wordpress/2017/07/html5-canvas-image-compress-upload/)


#### 代码实现 
```html
<input id="file" type="file">
```

```js
// 原 input file element 对象
var eleFile = document.getElementById('file')

// File Reader
var reader = new FileReader()

// Image 对象
var img = new Image();

// 选择的文件对象
var file = null;

// 缩放图片需要的canvas
var canvas = document.createElement('canvas');
var context = canvas.getContext('2d');

// 获取要获取的真正的宽、高
function getWidthAndHeight(image) {
    // 图片原始尺寸
    var originWidth = image.width;
    var originHeight = image.height;
    
    // 限定要压缩的宽、高
    var maxWidth = 400, maxHeight = 400;
    
    // 目标尺寸
    var targetWidth = originWidth, targetHeight = originHeight;
  
    // 计算超出的 宽、高，并做出限制计算
    if (originWidth > maxWidth || originHeight > maxHeight) {
        if (originWidth / originHeight > maxWidth / maxHeight) {
            // 更宽，按照宽度限定尺寸
            targetWidth = maxWidth;
            targetHeight = Math.round(maxWidth * (originHeight / originWidth));
        } else {
            // 更高，按照高度限定尺寸
            targetHeight = maxHeight;
            targetWidth = Math.round(maxHeight * (originWidth / originHeight));
        }
    }
    return {w: targetWidth, h: targetHeight}
}

// base64地址图片加载完毕后
img.onload = function () {
    // 最大尺寸限制
    var wh = getWidthAndHeight(img)
        
    // canvas对图片进行缩放
    canvas.width = wh.w;
    canvas.height = wh.h;
    
    // 清除画布
    context.clearRect(0, 0, targetWidth, targetHeight);
    
    // 图片压缩
    context.drawImage(img, 0, 0, targetWidth, targetHeight);
    
    // canvas转为blob并上传
    canvas.toBlob(function (blob) {
      // 上传 blob，一般到这里都结束了，将 blob（二进制格式数据）发过去之后，后台作处理(easy)
      // 如果需要以 file 文件格式上传，请参考 blob 与 file 互转的代码
    }, file.type || 'image/png');
};

// 文件base64化，以便获知图片原始尺寸
reader.onload = function(e) {
    img.src = e.target.result;
};

// 监听 input file 改变（即上传了文件）
eleFile.addEventListener('change', function (event) {
    file = event.target.files[0];
    // 选择的文件是图片
    if (file.type.indexOf("image") === 0) {
        reader.readAsDataURL(file);    
    }
});
```

