## H5 Canvas 转换 dataURL/Blob/File对象 

#### 创建 Canvas 及 context 上下文对象 
```js
// 创建  canvas 与 context 对象
var canvas = document.createElement('canvas')
var context = canvas.getContext('2d') // canvas对图片进行缩放
var image = document.getElementById('img')

// 设置 canvas
var w = image.width
var h = image.height
canvas.width = w
canvas.height = h

// 清除画布
context.clearRect(0, 0, w, h)

// 图片绘
context.drawImage(image, 0, 0, w, h)
```

##### 读取 dataUrl, blob ，并互相转换，转换成 dataUrl, blob, File 格式
```js
function dataURLtoBlob(dataurl) {
  var arr = dataurl.split(','), mime = arr[0].match(/:(.*?);/)[1],
    bstr = atob(arr[1]), n = bstr.length, u8arr = new Uint8Array(n);
  while(n--){
    u8arr[n] = bstr.charCodeAt(n);
  }
  return new Blob([u8arr], {type:mime});
}

function dataURLtoFile(dataurl, filename) {
  var arr = dataurl.split(','), mime = arr[0].match(/:(.*?);/)[1],
    bstr = atob(arr[1]), n = bstr.length, u8arr = new Uint8Array(n);
  while(n--){
    u8arr[n] = bstr.charCodeAt(n);
  }
  return new File([u8arr], filename, {type:mime});
}

let dataUrl = canvas.toDataURL()

let blob = canvas.toBlob(blob => {
  console.log('blob: ' + blob)
})

```

#### 参考 
* [csdn Blog](http://blog.csdn.net/cuixiping/article/details/45932793)

