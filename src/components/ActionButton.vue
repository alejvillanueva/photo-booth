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
    padding: 10px 25px;
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
    box-shadow: 0 0 25px 1px var(--action-button-box-shadow-color); 
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
    transition: .3s;
    box-shadow: 0 0 25px 1px var(--action-button-box-shadow-color);
  }

</style>