<script setup>
  import logo from '../assets/gramercy_logo.png';
import AppHeader from '../components/AppHeader.vue';
  import HypeText from '../components/HypeText.vue';
  const props = defineProps(['name', 'photo']);
  const emit = defineEmits(['reset']);

  const startOver = () => {
    emit('reset');
  }
</script>
<template>
  <div class="thank-you-container">
    <AppHeader />
    <HypeText>
      <template #main> 
        Thanks, {{ name }}
      </template>
    </HypeText>
    <div class="thank-you-photo-controls">
      <img
        class="photo"
        :src="photo"
      >
      <button @click="startOver">
        Start Over?
      </button>
    </div>
  </div>
</template>
<style scoped>
  .thank-you-container{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .thank-you-photo-controls{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  .photo{
    width: 50vmin;
    border-radius: 25px;
    margin: 25px;
  }
</style>
