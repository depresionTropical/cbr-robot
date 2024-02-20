<template>
  <div>
    <button type="button" class="btn btn-outline-success" @click="submit">
      Enviar
    </button>
  </div>
</template>

<script>
export default {
  methods: {
    submit() {
      // Emite el evento `submit` al hacer clic en el botón
      this.$emit("submit");
    },
  },
};
</script>
