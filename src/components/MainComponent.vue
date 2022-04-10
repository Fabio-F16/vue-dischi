<template>
  <main>
    <div class="container">
      <div class="row">
        <div v-if="discs.lenght > 0" class="col-12 col-md-6">
          <CardDisc v-for="item in discs" :key="item" :disc="item" />
        </div>
      </div>
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
          if (response.status == 200) {
            this.discs = response.data;
            console.log(this.discs);
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
</style>