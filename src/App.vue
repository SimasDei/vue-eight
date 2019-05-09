<template>
  <div>
    <search-bar @termChange="onTermChange"></search-bar>
    <video-list :videos="videos"></video-list>
  </div>
</template>
<script>
import axios from "axios";
import SearchBar from "@/components/SearchBar.vue";
import VideoList from "@/components/VideoList.vue";
import API from "../config.js";

export default {
  name: "App",
  data() {
    return {
      videos: []
    };
  },
  components: {
    SearchBar,
    VideoList
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get(`${API.url}`, {
          params: {
            key: API.key,
            type: "video",
            part: "snippet",
            q: searchTerm
          }
        })
        .then(response => (this.videos = response.data.items));
    }
  }
};
</script>
<style>
</style>
