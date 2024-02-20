<template>
    <div>
      <textarea v-model="text" rows="5" cols="50" placeholder="Escribe lo que ves en el video"></textarea>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        text: '',
      };
    },
  }
  </script>
  