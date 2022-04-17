<template>
  <div class="ff-card row col-12 col-md-4 col-lg-2">
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
    text-transform: uppercase;
  }
  p {
    color: #79756f;
    font-size: 0.8rem;
    margin-bottom: -5px;
  }
}
</style>
