## animate.css

[npm](https://www.npmjs.com/package/animate.css)

通过简单的 css 控制动画

对于图片，建议在图片加载完成后再添加动画 css：

```html
<img src="../../image/cai-shen/title.png" alt="" @load="titleAnimate='animate__animated animate__tada'" :class="titleAnimate">
```