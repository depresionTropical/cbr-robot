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
      this.$emit("submit", this.text);
    },
  },
};
</script>
  