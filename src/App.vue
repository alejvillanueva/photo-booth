<script setup>
  import HomeView from "./views/HomeView.vue";
  import WebcamView from "./views/WebcamView.vue";
  import ReviewView from "./views/ReviewView.vue";
  import ExitView from "./views/ExitView.vue";
</script>

<template>
  <HomeView v-if="currentScreen === 'home'" />
  <WebcamView v-else-if="currentScreen === 'webcam'" />
  <ReviewView v-else-if="currentScreen === 'review'" />
  <ExitView v-else-if="currentScreen === 'exit'" />
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
</style>