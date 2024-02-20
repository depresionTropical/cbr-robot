<!-- pages/index.vue -->
<template>
  <div class="container">
    <div class="row align-items-center">
      <VideoPlayer
        class="col"
        :videoEmbedUrl="selectedVideo ? selectedVideo.embedUrl : ''"
      />
    </div>
    <div class="row align-items-center">
      <TextInput class="col" v-model="text" />
    </div>
    <div class="row align-items-center">
      <SubmitButton class="col" @click="submit" />
    </div>
  </div>
</template>

<script>
import VideoPlayer from "~/components/VideoPlayer.vue";
import TextInput from "~/components/TextInput.vue";
import SubmitButton from "~/components/SubmitButton.vue";
import axios from "axios"; // Importa Axios

export default {
  modules: [
    // Otros módulos...
    "@nuxtjs/dotenv",
  ],
  publicRuntimeConfig: {
    apiUrl: process.env.API_URL,
  },
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
          embedUrl: "https://www.youtube.com/embed/8LcQa0EZdGA?si=3EzUfCeFrxkWU3UB",
        },
        {
          id: 2,
          title: "Video 2",
          embedUrl:
            "https://www.youtube.com/embed/GVM0wis_s4k?si=QW163N3gRQhW3jMJ",
        },
        {
          id: 3,
          title: "Video 3",
          embedUrl:
            "https://www.youtube.com/embed/ozLj0fAHUrQ?si=EKCigZ8gaYwX9097",
        },
        {
          id: 4,
          title: "Video 4",
          embedUrl:
            "https://www.youtube.com/embed/0bW356bMBLk?si=g2xdzMI39DKlwsPt",
        },
        {
          id: 5,
          title: "Video 5",
          embedUrl:
            "https://www.youtube.com/embed/0msVUCTPIbM?si=FwqxSbSTMfXVZZ_h",
        },
        {
          id: 6,
          title: "Video 6",
          embedUrl:
            "https://www.youtube.com/embed/AKHcLYFjCGo?si=eldYpEyEPndXnVh9",
        },
      ],
      selectedVideo: {
        id: 1,
          title: "Video 1",
          embedUrl: "https://www.youtube.com/embed/8LcQa0EZdGA?si=3EzUfCeFrxkWU3UB",
      },
      text: "",
      userId: null,
    };
  },
  mounted() {
    this.generateUserId();
  },
  methods: {
    generateUserId() {
      // Genera un ID de usuario aleatorio
      this.userId = Date.now() + Math.floor(Math.random() * 1000);
      console.log("Nuevo userId:", this.userId);
    },
    selectVideo(video) {
      this.selectedVideo = video;
    },
    submit() {
      const apiUrl = "https://backrobotcbr.onrender.com/crear-video-response/"; // Reemplaza "API_URL" con la URL de tu API
      console.log("URL de la API:", process.env.API_URL);
      const data = {
        user_id: parseInt(this.userId), // Asegúrate de que userId sea un número
        video_name: this.selectedVideo.title, // Usa el título del video como 'video_name'
        response: this.text, // La respuesta del usuario
      };
      // Envía una solicitud POST con Axios
      axios
        .post(apiUrl, data)
        .then((response) => {
          // Maneja la respuesta del servidor aquí
          console.log("Respuesta enviada con éxito:", response.data);
          // Llama a selectNextVideoOrRegenerateUserId aquí para avanzar al siguiente video
          this.selectNextVideoOrRegenerateUserId();
        })
        .catch((error) => {
          // Maneja un posible error aquí
          console.error("Error al enviar la respuesta:", error);
        });
    },
    selectNextVideoOrRegenerateUserId() {
      const currentIndex = this.videoList.findIndex(
        (video) => video.id === this.selectedVideo.id
      );
      const nextIndex = (currentIndex + 1) % this.videoList.length;

      if (nextIndex === 0) {
        this.generateUserId(); // Regenera el userId después de ver todos los videos
        alert(
          "¡Has visto todos los videos!\n Refresca la página para volver a empezar."
        );
      } else {
        this.selectedVideo = this.videoList[nextIndex];
      }

      // Opcional: Reinicia el texto solo si es necesario
      this.text = "";
    },
  },
};
</script>