# 常用的 vue 自写组件

复制直接可用（可能需要做部分修改以适应项目需求）

[背景音乐](_files/AudioBg.vue)

```html
<audio-bg :src="require('../../audio/post.mp3')"/>
```

[遮罩引导](_files/MaskGuide.vue)

```html
<mask-guide v-if="subscribeShow" width="594" height="629" top="257"
  :img="require('../../image/pop-subscribe.png')"
  @close="closeSubscribe"/>
```

[进度条加载](_files/ProgressLoading.vue)

```html
<progress-loading :value="loadingValue" animate-ts="200ms"/>
```
