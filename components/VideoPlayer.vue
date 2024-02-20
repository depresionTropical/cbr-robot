<template>
  <div v-if="videoEmbedUrl" class="video-player">
    <iframe
      :src="videoEmbedUrl"
      frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    ></iframe>
  </div>
</template>

<script>
export default {
  props: {
    videoEmbedUrl: String,
  },
};
</script>

<style scoped>
.video-player {
  position: relative;
  width: 100%;
  padding-bottom: 56.25%; /* Proporción 16:9 para hacer que el contenedor sea responsive */
}

.video-player iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.instructions {
  font-size: 18px;
  margin-bottom: 15px;
}
</style>
