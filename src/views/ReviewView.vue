<script setup>
  import logo from '../assets/gramercy_logo.png';
import AppHeader from '../components/AppHeader.vue';
  import HypeText from '../components/HypeText.vue';

  const emit = defineEmits(['retake', 'submit', 'exit'])
  const props = defineProps(['photo']);

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
  <div class="review-container">
    <AppHeader />
    <HypeText>
      <template #main>
        You look fantastic!
      </template>
      <template #sub> 
        What do you think? 
      </template>
    </HypeText>
    <div class="review-photo">
      <img
        class="photo"
        :src="photo"
      >
      <div class="review-photo-controls">
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
    </div>
  </div>
</template>
<style scoped>
  .review-container{
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .photo{
    width: 50vmin;
    border-radius: 25px;
    margin: 25px;  
  }

  .review-photo-controls{
    width: 100%;
    display: flex;  
    justify-content: space-around;

  }
</style>
