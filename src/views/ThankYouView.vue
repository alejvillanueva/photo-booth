<script setup>
  import logo from '../assets/gramercy_logo.png';
import ActionButton from '../components/ActionButton.vue';
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
      <ActionButton
        theme="secondary"
        @click="startOver"
      >
        Start Over?
      </ActionButton>
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
