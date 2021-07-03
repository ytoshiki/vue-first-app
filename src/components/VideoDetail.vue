<template>
  <div v-if="video">
    {{ title }}
  </div>
</template>

<script>
export default {
  name: 'VideoDetail',
  props: {
    video: Object
  },
  computed: {
    title() {
      const { videoId } = this.video.id;

      return videoId;
    }
  }
};
</script>
