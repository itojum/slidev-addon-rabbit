<template>
  <!-- when exporting, this footer isn't exported -->
  <footer
    v-if="$route.query.print === undefined && $route.name !== 'export' && ($route.query.time || $slidev.configs?.rabbit?.time)"
    class="rablte-container"
  >
    <Flag :left="goalPosition"/>
    <Rabbit :current="$slidev.nav.currentPage"/>
    <Turtle :current="$slidev.nav.currentPage"/>
  </footer>
</template>

<script>
export default {
  data() {
    const canvasWidth = this.$slidev.configs.canvasWidth;
    return {
      goalPosition: canvasWidth-20, // 20 is margin-right
    }
  },
};
</script>
