<template>
  <div class="ff-card col-12 col-md-2 row">
    <img :src="disc.poster" :alt="disc.title" />
    <h5>{{ disc.title }}</h5>
    <p>{{ disc.author }}</p>
    <p>{{ disc.year }}</p>
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
.ff-card {
  display: flex;
  justify-content: center;
  text-align: center;
  background-color: #2e3a46;
  margin: 5px;
  padding: 10px 0px;
  img {
    height: 150px;
    width: 150px;
  }
  h5 {
    margin-top: 10px;
    font-size: 0.8rem;
    color: white;
  }
  p {
    color: #79756f;
  }
}
</style>
