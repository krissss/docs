<template>
  <div class="progress">
    <div class="bar" :style="barStyle" :class="{over: value >= max}"></div>
  </div>
</template>

<script>
export default {
  name: "ProgressLoading",
  props: {
    value: Number,
    max: {
      type: Number,
      default: 100
    },
    animateTs: {
      type: String,
      default: '100ms'
    },
  },
  computed: {
    barStyle() {
      return {
        width: `${this.value/this.max*100}%`,
        transition: `width ${this.animateTs}`
      }
    }
  }
}
</script>

<style scoped lang="scss">
$barColor: #CC6F6A;
$barMargin: 6px;
$barHeight: 10px;
$barRadius: $barHeight / 2;
$progressBorder: 6px;
$progressColor: #7D1616;
$progressRadius: ($barHeight + $barMargin * 2 + $progressBorder * 2) / 2;

.progress {
  width: 100%;
  border-radius: $progressRadius;
  border: $progressBorder solid $progressColor;
  padding: $barMargin;

  .bar {
    text-align: center;
    height: $barHeight;
    background-color: $barColor;
    border-top-left-radius: $barRadius;
    border-bottom-left-radius: $barRadius;

    &.over {
      border-radius: $barRadius;
    }
  }
}
</style>
