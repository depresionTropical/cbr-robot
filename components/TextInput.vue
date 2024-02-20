<template>
  <div>
    <textarea :value="modelValue" @input="updateText" rows="5" cols="50" placeholder="Escribe lo que ves en el video"></textarea>
  </div>
</template>

<script>
export default {
  props: {
    modelValue: String,
  },
  methods: {
    updateText(event) {
      // Emite el evento `update:modelValue` al escribir en el textarea
      this.$emit('update:modelValue', event.target.value);
    },
  },
};
</script>
