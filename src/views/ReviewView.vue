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
  <div class="container">
    <AppHeader />
    <div class="main">
      <ContentText>
        <template #main>
          You look fantastic, {{ name }}!
        </template>
        <template #sub> 
          Retake your photo if you're not completely satisfied with the shot.
        </template>
      </ContentText>
      <div class="review-photo">
        <img
          class="media-canvas"
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
  </div>
</template>
<style scoped>
  .review-photo-controls{
    width: 100%;
    display: flex;  
    justify-content: space-around;
  }
  @media (max-width: 600px) {
  .review-photo-controls {
    flex-direction: column;
    justify-content: center;
    align-content: center;
    gap: var(--space-lg);
    padding: 0 var(--space-xxxl);
  }

  .mobile-actions{
    display: inline;
  }
}
</style>
