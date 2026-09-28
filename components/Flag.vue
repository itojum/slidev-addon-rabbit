<template>
  <div class="rabbit-container" :style="{left: left + 'px'}">
    <RabbitAddonIcon :src="$slidev.configs?.rabbit?.flagIcon">
      <emojione-monotone-flag-for-chequered-flag />
    </RabbitAddonIcon>
  </div>
</template>

<script>
export default {
  props: {
    left: Number,
  },
}
</script>
