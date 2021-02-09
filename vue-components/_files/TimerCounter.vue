<template>
  <div class="timer-bg">
    <div class="timer timer-1">
      <span>{{ counterStr[0] }}</span>
      <span>{{ counterStr[1] }}</span>
    </div>
    <div class="timer timer-2">
      <span>{{ counterStr[2] }}</span>
      <span>{{ counterStr[3] }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "TimerCounter",
  data() {
    return {
      counterStr: '0000',
      counterMax: '9999',
      interval: null,
      startTs: 0
    }
  },
  methods: {
    start() {
      this.startTs = (new Date()).getTime()
      this.interval = setInterval(() => {
        const diff = this.getDiff()
        if (diff >= this.counterMax) {
          this.counterStr = this.counterMax
          clearInterval(this.interval)
          return
        }
        this.counterStr = diff
      }, 10)

      this.$emit('started')
    },
    stop() {
      clearInterval(this.interval)

      this.$emit('stopped')
    },
    // 获取从开始到目前为止的时间差，'0812' 表示 8.12 秒，最大 '9999'
    getDiff() {
      let diff = (new Date()).getTime() - this.startTs
      diff = (diff+'').padStart(5, '0').substr(-5, 4)
      if (diff > this.counterMax) {
        return this.counterMax
      }
      return diff
    },
    getCounter() {
      return this.getDiff()
    },
    setCounter(counter) {
      if (counter > this.counterMax) {
        counter = this.counterMax
      }
      this.counter = parseInt(counter)
      this.counterStr = (counter + '').padStart(4, '0')
    }
  }
}
</script>

<style scoped lang="scss">
.timer-bg {
  width: 460px;
  height: 210px;
  margin: 0 auto;
  background-image: url("../../image/cai-shen/timer-bg.png");
  background-size: cover;
  position: relative;
}

.timer {
  position: absolute;
  top: 49px;
}

.timer span {
  font-size: 86px;
  color: #F9EFC0;
  letter-spacing: 0;
  display: block;
  float: left;
  /*数字在不同字体下大小不一，会造成位置错位，因此选择一个所有移动平台都有的字体*/
  font-family: Helvetica, sans-serif;
}

.timer-1 {
  left: 96px;
}

.timer-2 {
  left: 260px;
}
</style>
