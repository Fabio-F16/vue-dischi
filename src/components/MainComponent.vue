<template>
  <main>
    <div class="container">
      <FilterDisc @searchByGenre="filterByGenre" />
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
import FilterDisc from "@/components/FilterDisc.vue";

export default {
  name: "MainComponent",
  data() {
    return {
      discs: [],
      genre: "",
      filtered: [],
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
            this.discs = response.data.response;
            console.log(response.data.response);
            // console.log(this.discs);
          }
        })
        .catch((error) => {
          console.log(error);
        });
    },
    filterByGenre(genre) {
      this.genre = genre;
      if (this.filtered === "All") {
        return this.discs;
      }
      const filtered = this.discs.filter((item) => {
        return item.genre.toLowerCase().includes(this.genre.toLowerCase());
      });
      return filtered.filter((item) => {
        item.genre.toLowerCase().includes(this.genre.toLowerCase());
        console.log(this.filtered);
        this.filtered = filtered;
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