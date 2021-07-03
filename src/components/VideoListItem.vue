<template>
  <li @click="onVideoSelect">
    <img :src="url" />
    {{ video.snippet.title }}
  </li>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: {
    video: Object
  },
  computed: {
    url() {
      return this.video.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoSelect() {
      this.$emit('videoSelect', this.video);
    }
  }
};
</script>

<style scoped>
li {
  list-style: none;
}
</style>
