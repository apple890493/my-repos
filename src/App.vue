<template>
  <div id="app">
    <section>
      <ParallaxContainer class="first-element">
        <ParallaxContent class="element" :moveFactor="0.6">
          <FirstView />
        </ParallaxContent>
      </ParallaxContainer>
    </section>
    <section>
      <ParallaxContainer class="second-element">
        <ParallaxContent :moveFactor="0">
          <MainView />
        </ParallaxContent>
      </ParallaxContainer>
    </section>
  </div>
</template>

<script>
import ParallaxContainer from "./components/ParallaxContainer.vue";
import ParallaxContent from "./components/ParallaxContent.vue";
import MainView from "./components/MainView.vue";
import FirstView from "./components/FirstView.vue";

export default {
  name: "App",
  components: {
    ParallaxContainer,
    ParallaxContent,
    FirstView,
    MainView,
  },
};
</script>

<style>
@import "./assets/rest.css";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
}

.first-element {
  background: url("~@/assets/images/nature.jpg") center center no-repeat;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
  background-attachment: fixed;
  height: 100vh;
}

.second-element {
  /* background: #2b5454;
  opacity: 0.5; */
  background: url("~@/assets/images/nature2.jpg") center center no-repeat;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
  height: 100vh;
}

.element {
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(255, 255, 255, 0.5);
  border-radius: 15px;
}

h2 {
  font-size: 60px;
  padding: 5px 20px;
  color: #2b5454;
}
</style>
