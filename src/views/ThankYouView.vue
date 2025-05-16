<script setup>
  const props = defineProps(['name', 'photo']);
  const emit = defineEmits(['reset']);

  const startOver = () => {
    emit('reset');
  }
</script>
<template>
  <div class="thank-you">
    <h2>Thanks, {{ name }}</h2>
    <img :src="photo">
    <button @click="startOver">
      Start Over?
    </button>
  </div>
</template>
<style scoped></style>
