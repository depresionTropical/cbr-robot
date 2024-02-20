<!-- pages/index.vue -->
<template>
  <div>
    <VideoPlayer :videoEmbedUrl="selectedVideo ? selectedVideo.embedUrl : ''" />
    <TextInput v-model="text" />
    <SubmitButton @submit="submit" />
    <ul>
      <li v-for="video in videoList" :key="video.id">
        <button @click="selectVideo(video)">{{ video.title }}</button>
      </li>
    </ul>
  </div>
</template>

<script>
import VideoPlayer from '~/components/VideoPlayer.vue';
import TextInput from '~/components/TextInput.vue';
import SubmitButton from '~/components/SubmitButton.vue';

export default {
  components: {
    VideoPlayer,
    TextInput,
    SubmitButton,
  },
  data() {
    return {
      videoList: [
        { id: 1, title: 'Video 1', embedUrl: 'https://www.youtube.com/watch?v=NgWfVITgPnI' },
        // Agrega más videos según sea necesario
      ],
      selectedVideo: null,
      text: '',
    };
  },
  methods: {
    selectVideo(video) {
      this.selectedVideo = video;
    },
    submit() {
      // Lógica para enviar el texto
      console.log('Texto enviado:', this.text);
    },
  },
}
</script>
