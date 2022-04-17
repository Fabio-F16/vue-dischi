<template>
  <main>
    <div class="container">
      <FilterDisc @searchEmit="filterByGenre" />
      <div v-if="discs.length > 0" class="cardlist">
        <CardDisc
          v-for="(item, index) in discsFiltered"
          :key="index"
          :disc="item"
        />
      </div>
      <div v-else>loading</div>
    </div>
  </main>
</template>


<script>
import axios from "axios";
import CardDisc from "@/components/CardDisc.vue";
import FilterDisc from "@/components/FilterDisc.vue";

export default {
  name: "MainComponent",
  data() {
    return {
      discs: [],
      //genre: "",
      //filtered: "",
      typeSelected: "All",
    };
  },
  props: {
    url: String,
  },
  components: {
    CardDisc,
    FilterDisc,
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
            // console.log(response.data.response);
            this.discs = response.data.response;
            //console.log(this.discs);
            // author: "Bon Jovi"
            // genre: "Rock"
            // poster: "https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg"
            // title: "New Jersey"
            // year: "1988"
          }
        })
        .catch((error) => {
          console.log(error);
        });
    },
    filterByGenre(genere) {
      this.typeSelected = genere;
      console.log(this.typeSelected);
    },
  },
  computed: {
    discsFiltered: function () {
      if (this.typeSelected === "All") {
        return this.discs;
      }
      return this.discs.filter((item) => {
        return item.genre === this.typeSelected;
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