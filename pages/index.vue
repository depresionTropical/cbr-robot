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
        },
        {
          id: 2,
          title: "Video 2",
          embedUrl:
            "https://www.youtube.com/embed/fsxVo6WqI8w?si=utBEkBHGResAe0Zi",
        },
        {
          id: 3,
          title: "Video 3",
          embedUrl:
            "https://www.youtube.com/embed/IPa-RRuUNaA?si=Ra6KJxV1-bj5jtod",
        },
        {
          id: 4,
          title: "Video 4",
          embedUrl:
            "https://www.youtube-nocookie.com/embed/n768i9tfFOs?si=KzR-6iGROLQcu466",
        },
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
    console.log("Texto enviado:", this.text);

    const currentIndex = this.videoList.findIndex(
      (video) => video.id === this.selectedVideo.id
    );
    const nextIndex = (currentIndex + 1) % this.videoList.length;

    if (nextIndex === 0) {
      // Si nextIndex es 0, significa que hemos llegado al final de la lista
      // Aquí puedes mostrar un mensaje indicando que el usuario ha visto todos los videos
      alert("¡Has visto todos los videos!");
      // También puedes reiniciar la lista de videos si quieres que comience desde el principio nuevamente
      // this.selectedVideo = this.videoList[0];
    } else {
      // Si no es el último video, simplemente pasa al siguiente
      this.selectedVideo = this.videoList[nextIndex];
    }

    // Opcional: Reinicia el texto solo si es necesario
    this.text = '';
  },
  },
};
</script>
