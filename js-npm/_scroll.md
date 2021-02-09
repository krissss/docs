## moveto

[npm](https://www.npmjs.com/package/moveto)

平滑滚动页面到指定位置

```js
// 手动触发滚动
const moveTo = new MoveTo()
moveTo.move(document.getElementById('target'))

// 注册滚动监听
const trigger = document.getElementsByClassName('js-trigger')[0]
moveTo.registerTrigger(trigger)
```
