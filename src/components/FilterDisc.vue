<template>
  <div>
    <select @change="setGenre($event)">
      <option value="Rock">Rock</option>
      <option value="Jazz">Jazz</option>
      <option value="Pop">Pop</option>
      <option value="Metal">Metal</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "FiterDisc",
  data() {
    return {
      elementFiltered: "",
    };
  },
  methods: {
    setGenre(event) {
      console.log(event.target.value);
      this.elementFiltered = event.target.value;
      this.$emit("searchByGenre", this.elementFiltered);
    },
  },
};
</script>

<style>
</style>