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
  @import url('https://fonts.googleapis.com/css2?family=Lexend:wght@100..900&display=swap');
  body {
    font-family: 'Lexend', sans-serif;
    color: white;
    background: url('./assets/gramercy_background.png');
    background-size: cover;
    background-position: center;
    height: 100vh;
    margin: 0;
  }
  h2{
    font-weight: 200;
  }

  p{
    font-weight: 100;
  }

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


<!-- ADD TRANSITION -->