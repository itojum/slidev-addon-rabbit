<template>
  <div class="rabbit-container" :style="{left: left + 'px'}">
    <RabbitAddonIcon :src="$slidev.configs?.rabbit?.turtleIcon" flip>
      <emojione-monotone-turtle class="icon" />
    </RabbitAddonIcon>
  </div>
</template>

<script>
export default {
  props: {
    current: Number
  },
  data() {
    const maxWidth = this.$slidev.configs.canvasWidth - 20; // 20 is margin-right
    // URL query (?time=) takes precedence over the `rabbit.time` config
    const time = this.$route?.query?.time || this.$slidev.configs?.rabbit?.time || 10;
    return {
      left: 0,
      intervalId: null,
      maxWidth: maxWidth,
      speed: maxWidth / (time * 60 * 10) // 100ms毎の変化量
    }
  },
  beforeUpdate() {
    // Reset when opening the first page
    if (this.current == 1) {
      this.left = 0;
      if (this.intervalId) {
        clearInterval(this.intervalId);
        this.intervalId = null;
      }
    }
    // do nothing if the turtle already starts
    if (this.intervalId) {
      return;
    }
    // let the turtle run
    this.intervalId = setInterval(() => {
      if (this.left < this.maxWidth) {
        this.left += this.speed;
      }
    }, 100); // update per 100ms
  }
};
</script>
