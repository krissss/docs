## animate.css

[npm](https://www.npmjs.com/package/animate.css)

通过简单的 css 控制动画

对于图片，建议在图片加载完成后再添加动画 css：

```html
<img src="../../image/cai-shen/title.png" alt="" @load="titleAnimate='animate__animated animate__tada'" :class="titleAnimate">
```

注意：使用时会导致页面宽度或高度超出父级，导致出现滚动条，可以通过给父级添加 `overflow:hidden` 解决，[详见](https://animate.style/#Overflow)

## vue2-animate

[npm](https://www.npmjs.com/package/vue2-animate)

使用 vue 的 transition 体现动画：

```vue
<transition name="fade">
  <p v-if="show">hello</p>
</transition>
```

注意：不完全支持`animate.css`的全部动画效果，但是基本够用，且因为执行完后会删除css名，因此没有超出宽高的问题
