<template>
  <select v-model="typeSelected" @change="$emit('searchEmit', typeSelected)">
    <option value="All">All</option>
    <option value="Rock">Rock</option>
    <option value="Jazz">Jazz</option>
    <option value="Pop">Pop</option>
    <option value="Metal">Metal</option>
  </select>
</template>

<script>
export default {
  name: "FiterDisc",
  data() {
    return {
      typeSelected: "all",
      // elementFiltered: "",
    };
  },
  methods: {
    // setGenre(event) {
    //   console.log(event.target.value);
    //   this.elementFiltered = event.target.value;
    //   this.$emit("searchByGenre", this.elementFiltered);
    // },
  },
};
</script>

<style>
</style>