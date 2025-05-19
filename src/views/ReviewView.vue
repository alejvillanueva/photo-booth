<script setup>
  import ActionButton from '../components/ActionButton.vue';
  import AppHeader from '../components/AppHeader.vue';
  import ContentText from '../components/ContentText.vue';

  const emit = defineEmits(['retake', 'submit', 'exit']);
  
  const props = defineProps({
    photo: {
      type: String,
      default: "",
    },
    name: {
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
    <ContentText>
      <template #main>
        You look fantastic, {{ name }}!
      </template>
      <template #sub> 
        Retake your photo if you're notcompletely satisfied with the shot.
      </template>
    </ContentText>
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
    width: var(--sanvas-size);;
    border-radius: var(--border-radius);
    margin: 25px;  
  }

  .review-photo-controls{
    width: 100%;
    display: flex;  
    justify-content: space-around;
  }
</style>
