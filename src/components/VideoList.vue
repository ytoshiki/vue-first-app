<template>
  <ul>
    <VideoListItem v-for="(video, index) in videos" :key="index" :video="video" @videoSelect="onVideoSelect" />
  </ul>
</template>

<script>
import VideoListItem from './VideoListItem';
export default {
  components: {
    VideoListItem
  },
  name: 'VideoList',
  props: {
    videos: Array
  },
  methods: {
    onVideoSelect(video) {
      this.$emit('videoSelect', video);
    }
  }
};
</script>

<style></style>
