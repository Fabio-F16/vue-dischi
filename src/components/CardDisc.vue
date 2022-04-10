<template>
  <div>
    <img :src="disc.poster" :alt="disc.title" />
    <h3>{{ disc.title }}</h3>
    <p>{{ disc.author }}</p>
  </div>
</template>

<script>
export default {
  name: "CardDisk",
  props: {
    disc: Object,
  },
};
</script>

<style lang="scss" scoped>
</style>