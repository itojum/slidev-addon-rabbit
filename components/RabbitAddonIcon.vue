<template>
  <img v-if="isImage" :src="src" class="rabbit-addon-image" alt="" />
  <span v-else-if="src" class="rabbit-addon-emoji" :class="{ icon: flip }">{{ src }}</span>
  <slot v-else />
</template>

<script>
// Render a custom icon from config.
//   - starts with "/", "./", "http://", "https://" or "data:" -> image (displayed as-is)
//   - any other non-empty string                               -> emoji / text
//   - empty                                                    -> default icon (slot)
export default {
  props: {
    src: String,
    flip: Boolean,
  },
  computed: {
    isImage() {
      return typeof this.src === 'string' && /^(\/|\.\/|https?:\/\/|data:)/.test(this.src);
    },
  },
};
</script>
