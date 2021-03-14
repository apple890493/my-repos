<template>
  <div class="parallax-container">
    <slot />
  </div>
</template>

<script>
export default {
  name: "ParallaxContainer",
  provide() {
    return { parallaxContainer: this.data };
  },
  data() {
    return {
      data: { height: 0, width: 0, scroll: 0 },
    };
  },
  mounted() {
    this.parallax();

    const eventHandler = () => requestAnimationFrame(this.parallax);
    window.addEventListener(`scroll`, eventHandler);
  },
  methods: {
    parallax() {
      const containerRect = this.$el.getBoundingClientRect();
      // console.log(containerRect);
      this.data.height = containerRect.height;
      this.data.width = containerRect.width;

      const offsetTop = containerRect.top;
      const offsetBottom = window.innerHeight - offsetTop;
      this.data.scroll = offsetBottom / (window.innerHeight + this.data.height);
    },
  },
};
</script>

<style scoped>
.parallax-container {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
