<template lang="html">
  <div class="canvas" @mousemove="move($event)">
    <div class="sticker"
      @mousedown="down($event)"
      @mouseup="up($event)"
      :style="
        'left: ' + boxX + 'px;' +
        'top: ' + boxY + 'px;' +
        'transform: rotate(' + r + 'deg);'
      "
      >
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      isDrag: false,
      offsetX: 0,
      offsetY: 0,
      boxX: 100,
      boxY: 100
    }
  },
  computed: {
    r () {
      return this.boxX % 360
    }
  },
  methods: {
    down (event) {
      this.offsetX = event.offsetX
      this.offsetY = event.offsetY
      this.isDrag = true
    },
    move (event) {
      // console.log('move')
      console.log(event)
      if (this.isDrag) {
        this.boxX = event.x - this.offsetX
        this.boxY = event.y - this.offsetY
      }
    },
    up (event) {
      this.isDrag = false
    }
  }
}
</script>

<style lang="css">
.canvas {
  background: #0F0;
  width: 100vw;
  height: 100vh;
}
.sticker {
  background: #F00;
  width: 100px;
  height: 100px;
  position: absolute;
  left: 100px;
  top: 100px;
}
</style>
