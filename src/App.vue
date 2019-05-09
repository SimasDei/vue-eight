<template>
  <div>
    <search-bar @termChange="onTermChange"></search-bar>
  </div>
</template>
<script>
import SearchBar from "@/components/SearchBar.vue";
import API from "../config.js";
export default {
  name: "App",
  components: {
    SearchBar
  },
  methods: {
    onTermChange(e) {
      console.log(e.data);
    }
  }
};
</script>
<style>
</style>
