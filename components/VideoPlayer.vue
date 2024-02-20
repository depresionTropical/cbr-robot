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

  width: 1300px;
  height: 500px; 
}
</style>
