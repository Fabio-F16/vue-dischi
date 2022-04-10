<template>
  <header>
    <div class="container-xl">
      <img alt="Vue logo" src="../assets/spotify-logo.png" />
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderComponent",
};
</script>

<style lang="scss" scoped>
@import "@/style/variables";

header {
  background-color: #2e3a46;
  padding: 10px 0px;
  img {
    width: 50px;
  }
}
</style>