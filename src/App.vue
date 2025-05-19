<script setup>
  import { ref } from "vue";
  import HomeView from "./views/HomeView.vue";
  import WebcamView from "./views/WebcamView.vue";
  import ReviewView from "./views/ReviewView.vue";
  import ThankYouView from "./views/ThankYouView.vue";

  const currentScreen = ref('home');
  const name = ref('');
  const photo = ref('');

  const startWebcam = userName => {
    name.value = userName;
    currentScreen.value = 'webcam';
  }

  const reviewPhoto = photoData => {
    photo.value = photoData;
    currentScreen.value = 'review';
  };

  const submitPhoto = () => {
    currentScreen.value = 'thank you';
  };

  const retakePhoto = () => {
    photo.value = '';
    currentScreen.value = 'webcam';
  }

  const goHome = () => {
    name.value = '';
    photo.value = '';
    currentScreen.value = 'home'
  }
</script>

<template>
  <Transition name="home">
    <HomeView 
      v-if="currentScreen === 'home'" 
      @start="startWebcam" 
    />
  </Transition>
  <Transition 
    name="webcam" 
    appear
  >
    <WebcamView 
      v-if="currentScreen === 'webcam'" 
      @review="reviewPhoto"
      @exit="goHome"
    />
  </Transition>
  <ReviewView 
    v-if="currentScreen === 'review'" 
    :name="name"
    :photo="photo"
    @retake="retakePhoto"
    @submit="submitPhoto"
    @exit="goHome"
  />
  <ThankYouView 
    v-if="currentScreen === 'thank you'" 
    :name="name"
    :photo="photo"
    @reset="goHome"
  />
</template>

<style>

  .home-enter-active,
  .home-leave-active
   {
    transition: opacity 1s ease;
  }

  .home-enter-from,
  .home-leave-to {
    opacity: 0;
  }

  .webcam-enter-active {
    transition: opacity 3s ease;
  }
  .webcam-enter-from {
    opacity: 0;
  }

</style>