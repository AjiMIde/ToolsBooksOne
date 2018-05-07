## onLine/offLine

#### 属性
```js
if (navigator.onLine) {
  alert('online')
} else {
  alert('offline')
}
```

#### 监听方法
```js
window.addEventListener("online", () => {
    that._fnNetworkHandler() ;
}, true)

window.addEventListener("offline", () => {
    that._fnNetworkHandler() ;
}, true)

```

