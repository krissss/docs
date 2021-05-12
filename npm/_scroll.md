## moveto

[npm](https://www.npmjs.com/package/moveto)

平滑滚动页面到指定位置，不支持横向滚动，API简单

```js
// 手动触发滚动
const moveTo = new MoveTo()
moveTo.move(document.getElementById('target'))

// 注册滚动监听
const trigger = document.getElementsByClassName('js-trigger')[0]
moveTo.registerTrigger(trigger)
```

## animated-scroll-to

[npm](https://www.npmjs.com/package/animated-scroll-to)

平滑滚动页面到指定位置，支持横向和纵向，支持回调

```js
import animateScrollTo from 'animated-scroll-to'
animateScrollTo([1000, null], () => {
  console.log('over')
})
```

## vuescroll

[npm](https://www.npmjs.com/package/vuescroll)

仅支持 vue2，看上去功能强大，支持 pc/移动，未实际测试使用
