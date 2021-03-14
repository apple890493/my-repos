<template>
  <div class="tittle-view">
    <h2>{{ toggleChange }}</h2>
  </div>
</template>

<script>
export default {
  name: "FirstView",
  inject: ["parallaxContainer"],
  computed: {
    toggleChange() {
      const { scroll } = this.parallaxContainer;
      const title = scroll === 1 ? "My Repos" : "Welcome Here";
      return title;
    },
  },
};
</script>
