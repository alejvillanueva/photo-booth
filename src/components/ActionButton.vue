<script setup>
  const props = defineProps({
    theme: {
      type: String,
      default: "primary"
    }
  })
</script>
<template>
  <button :class="theme">
    <slot />
  </button>
</template>
<style scoped>
  button{
    font-family: var(--font-family-primary);
    font-weight: var(--font-weight-bold);
    border-radius: var(--border-radius);
    padding: var(--space-md) var(--space-xl);
    height: fit-content;
  }

  .primary{
    background-color: var(--primary-bg-color);
    color: var(--primary-text-color);
    border-color: var(--primary-border-color);
  }

  .primary:hover{
    background-color: var(--secondary-bg-color);
    color: var(--secondary-text-color);
    border-color: var(--secondary-border-color);
    box-shadow: 0 0 var(--box-shadow-blur-radius) var(--box-shadow-spread-radius) var(--action-button-box-shadow-color); 
    transition: .3s;   
  }

  .secondary{
    background-color: var(--secondary-bg-color);
    color: var(--secondary-text-color);
    border-color: var(--secondary-border-color);
  }
  .secondary:hover{
    background-color: var(--primary-bg-color);
    color: var(--primary-text-color);  
    box-shadow: 0 0 var(--box-shadow-blur-radius) var(--box-shadow-spread-radius) var(--action-button-box-shadow-color);
    transition: .3s;
  }
</style>