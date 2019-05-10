<template>
  <div>
    <input type="text" v-model="searchTerm">
    <button @click="onClick" class="btn">Search</button>
  </div>
</template>
<script>
export default {
  name: "SearchBar",
  data() {
    return {
      searchTerm: null
    };
  },
  methods: {
    onClick: function() {
      this.$emit("termChange", this.searchTerm);
    }
  }
};
</script>
<style scoped>
input[type="text"] {
  width: 75%;
  margin-bottom: 20px;
}
</style>
