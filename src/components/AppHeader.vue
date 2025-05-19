<script setup>
  import logo from '../assets/gramercy_logo.png';
  import ActionButton from './ActionButton.vue';
  
  const props = defineProps({
    showExitButton: {
      type: Boolean,
      default: false,
    }
  });
  
  const emit = defineEmits(['exit']);

  const goHome = () => {
    emit('exit');
  }
</script>
<template>
  <div class="header">
    <ActionButton class="placeholder">
      Exit
    </ActionButton>
    <img 
      class="header-logo"
      :src="logo"
      alt="Gramercy Tech"
    >
    <ActionButton 
      :class="{placeholder: !showExitButton}" 
      theme="primary"
      @click="goHome"
    > 
      Exit 
    </ActionButton>
  </div>
</template>
<style scoped>
  .header{
    display: flex;
    box-sizing: border-box;
    width: 100%;
    padding: var(--space-xxl);
  }
  .header-logo{
    max-width: 4vmax;
    margin: auto;
  }
  .placeholder{
    visibility: hidden;
  }
</style>