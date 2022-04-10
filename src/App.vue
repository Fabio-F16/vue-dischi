<template>
  <div id="app">
    <HeaderComponent />
    <MainComponent :url="urlApi" />
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";

export default {
  name: "App",
  components: {
    HeaderComponent,
    MainComponent,
  },
  data() {
    return {
      urlApi: "https://flynn.boolean.careers/exercises/api/array/music",
    };
  },
};
</script>

<style lang="scss">
@import "@/style/mother";
@import "@/style/variables";

#app {
  font-family: $font;
}
</style>
