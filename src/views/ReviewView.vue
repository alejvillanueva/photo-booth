<script setup>
  import { ref } from 'vue';
  const props = defineProps(['photo']);
</script>
<template>
  <img :src="photo">
  <button>Retake</button>
  <button>Submit</button>
  <button>Exit</button>
</template>
<style scoped>
img{
  max-width: 50vmax;
}
</style>
