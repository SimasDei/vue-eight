<template>
  <ul class="list-group list-group-flush">
    <video-list-item
      v-for="video in videos"
      :key="video.id.videoId"
      :video="video"
      @videoSelect="onVideoSelect"
    ></video-list-item>
  </ul>
</template>
<script>
import VideoListItem from "@/components/VideoListItem.vue";

export default {
  name: "VideoList",
  props: ["videos"],
  components: {
    VideoListItem
  },
  methods: {
    onVideoSelect(video) {
      this.$emit("videoSelect", video);
    }
  }
};
</script>
<style>
</style>
