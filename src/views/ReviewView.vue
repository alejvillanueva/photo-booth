<script setup>
  const emit = defineEmits(['retake', 'submit', 'exit'])
  const props = defineProps(['photo']);

  // Can I make this dynamic
  const submitPhoto = () => {
    emit('submit');
  };

  const retakePhoto = () => {
    emit('retake');
  };

  const exit = () => {
    emit('exit');
  }
</script>
<template>
  <div class="review">
    <img :src="photo">
    <button @click="retakePhoto">
      Retake
    </button>
    <button @click="submitPhoto">
      Submit
    </button>
    <button @click="exit">
      Exit
    </button>
  </div>
</template>
<style scoped>
  .review{
    display: flex;
  }
  img{
    max-width: 50vmax;
  }
</style>
