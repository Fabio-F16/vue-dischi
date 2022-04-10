<template>
  <main></main>
</template>


<script>
import axios from "axios";
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
  mounted() {
    this.loadData();
  },
  methods: {
    loadData() {
      axios
        .get(this.url)
        .then((response) => {
          //console.log(response);
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