<template>
  <div>
    <textarea :value="modelValue" @input="$emit('update:modelValue', $event.target.value)" rows="5" cols="50" placeholder="Escribe lo que ves en el video"></textarea>
  </div>
</template>

<script>
export default {
  props: {
    modelValue: String,
  },
}
</script>
