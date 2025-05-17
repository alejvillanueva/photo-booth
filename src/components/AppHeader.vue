<script setup>
  import logo from '../assets/gramercy_logo.png';
  const props = defineProps(['showExitButton']);
  const emit = defineEmits(['exit']);

  const goHome = () => {
    emit('exit');
  }
</script>
<template>
  <div class="header">
    <div class="header-content">
      <img 
        class="header-logo"
        :src="logo"
        alt="Gramercy Tech"
      >
      <button 
        v-if="showExitButton" 
        @click="goHome"
      > 
        Exit 
      </button>
    </div>
  </div>
</template>
<style scoped>
  .header{
    box-sizing: border-box;
    display: flex;
    width: 100%;
    justify-content: flex-end;
    padding: 50px;
  }
  
  .header-content{
    display: flex;
    width: 50%;
    justify-content: space-between;
  }
  .header-logo{
    max-width: 3vmax;
  }
</style>