<template>
  <ul class="list-group">
    <video-list-item v-for="video in videos" :key="video.id.videoId" :video="video"></video-list-item>
  </ul>
</template>
<script>
import VideoListItem from "@/components/VideoListItem.vue";

export default {
  name: "VideoList",
  props: ["videos"],
  components: {
    VideoListItem
  }
};
</script>
<style>
</style>
