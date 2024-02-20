<!-- pages/index.vue -->
<template>
  <div class="container">
    <div class="row">
      
        <VideoPlayer
          :videoEmbedUrl="selectedVideo ? selectedVideo.embedUrl : ''"
        />
        <TextInput v-model="text" />
        <SubmitButton @submit="submit" />
      
    </div>
  </div>
</template>

<script>
import VideoPlayer from "~/components/VideoPlayer.vue";
import TextInput from "~/components/TextInput.vue";
import SubmitButton from "~/components/SubmitButton.vue";

export default {
  components: {
    VideoPlayer,
    TextInput,
    SubmitButton,
  },
  data() {
    return {
      videoList: [
        {
          id: 1,
          title: "Video 1",
          embedUrl: "https://www.youtube.com/watch?v=NgWfVITgPnI",
          id: 2,
          title: "Video 2",
          embedUrl: "https://youtu.be/fsxVo6WqI8w?si=-H7V8LTMlt6JFGJX",
        },
        // Agrega más videos según sea necesario
      ],
      selectedVideo: {
        id: 1,
        title: "Video 1",
        embedUrl: "https://www.youtube.com/embed/NgWfVITgPnI",
      },
      text: "",
    };
  },
  methods: {
    selectVideo(video) {
      this.selectedVideo = video;
    },
    submit() {
      // Lógica para enviar el texto
      console.log("Texto enviado:", this.text);
    },
  },
};
</script>
