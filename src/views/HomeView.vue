<script setup>
  import logo from '../assets/gramercy_logo.png';
  import { ref } from 'vue';

  const userName = ref('');
  const emit = defineEmits(['start']);

  const submitName = () => {
    const name = userName.value;
    emit('start', name)
  }
</script>
<template>
  <div class="home-screen">
    <img 
      class="home-screen-logo"
      :src="logo"
      alt="Gramercy Tech"
    >
    <h1>Welcome to the Photo Experience!</h1>
    <h2> Smile, snap, and share with our difital photo booth experience.</h2>
    <p>Enter your name to begin.</p> 
    <div class="home-screen-input">
      <input 
        v-model="userName"
        @keydown.enter="submitName"
      >
      <button @click="submitName"> 
        Start
      </button>
    </div>
  </div>
</template>
<style scoped>
  .home-screen{
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
  }
  .home-screen-logo{
      max-width: 5vmax;
      height: auto;
  }
</style>
