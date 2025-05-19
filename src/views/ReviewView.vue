<script setup>
  import logo from '../assets/gramercy_logo.png';
import ActionButton from '../components/ActionButton.vue';
import AppHeader from '../components/AppHeader.vue';
  import HypeText from '../components/HypeText.vue';

  const emit = defineEmits(['retake', 'submit', 'exit'])
  const props = defineProps({
    photo: {
      type: String,
      default: "",
    }
  });

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
        <ActionButton
          theme="primary"
          @click="retakePhoto"
        >
          Retake
        </ActionButton>
        <ActionButton
          theme="primary"
          @click="submitPhoto"
        >
          Submit
        </ActionButton>
        <ActionButton
          theme="primary"
          @click="exit"
        >
          Exit
        </ActionButton>
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
    border-radius: var(--border-radius);
    margin: 25px;  
  }

  .review-photo-controls{
    width: 100%;
    display: flex;  
    justify-content: space-around;
  }
</style>
