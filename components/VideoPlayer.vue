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

<style>
.video-player iframe {
  margin-left: 20px;
  width: 50%;
  height: 500px; /* Ajusta el tamaño según sea necesario */
}
</style>
