<template>
  <li class="list-group-item media" @click="onVideoSelect">
    <img :src="thumbnailUrl" class="mr-3">
    <div class="media-body">{{video.snippet.title}}</div>
  </li>
</template>
<script>
export default {
  name: "VideoListItem",
  props: ["video"],
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoSelect() {
      this.$emit("videoSelect", this.video);
    }
  }
};
</script>
<style scoped>
li {
  display: flex;
}
li:hover {
  cursor: pointer;
  background-color: #eee;
}
</style>
