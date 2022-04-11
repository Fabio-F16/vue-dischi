<template>
  <main>
    <div class="container">
      <div v-if="discs.length > 0" class="cardlist">
        <CardDisc v-for="(item, index) in discs" :key="index" :disc="item" />
      </div>
      <div v-else>loading</div>
    </div>
  </main>
</template>


<script>
import axios from "axios";
import CardDisc from "@/components/CardDisc.vue";

export default {
  name: "MainComponent",
  data() {
    return {
      discs: [],
    };
  },
  props: {
    url: String,
  },
  components: {
    CardDisc,
  },
  mounted() {
    this.loadData();
  },
  methods: {
    loadData() {
      axios
        .get(this.url)
        .then((response) => {
          if (response.status === 200) {
            this.discs = response.data.response;
            // console.log(response.data);
            // console.log(this.discs);
          }
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
main {
  overflow-y: auto;
  height: calc(100vh - 70px);
  background-color: #1e2d3b;
  padding: 25px;
}
.cardlist {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>