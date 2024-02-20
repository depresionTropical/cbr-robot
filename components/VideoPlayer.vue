<!-- components/VideoPlayer.vue -->
<template>
  <div>
    <button @click="openVideo">Ver Video</button>
  </div>
</template>

<script>
export default {
  props: {
    videoEmbedUrl: String,
  },
  methods: {
    openVideo() {
      if (this.videoEmbedUrl) {
        window.open(this.videoEmbedUrl, '_blank');
      }
    },
  },
};
</script>
