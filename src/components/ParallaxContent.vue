<template>
  <div
    class="parallax-content"
    :style="{
      transform: `translate3d(0, ${offset}px, 0)`,
    }"
  >
    <slot />
  </div>
</template>

<script>
export default {
  name: "ParallaxContent",
  inject: ["parallaxContainer"],
  props: {
    moveFactor: {
      type: Number,
      require: true,
    },
  },
  computed: {
    offset() {
      const { height, scroll } = this.parallaxContainer;
      return scroll * height * this.moveFactor;
    },
  },
};
</script>
