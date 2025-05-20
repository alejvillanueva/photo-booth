<script setup>
  const props = defineProps({
    theme: {
      type: String,
      default: "mobile"
    }
  })
</script>
<template>
  <button :class="theme">
    <slot />
  </button>
</template>
<style scoped>
  .mobile {
    display: flex;
    border-radius: var(--border-radius-circle);
    padding: var(--space-xxs);
    margin: var(--space-md) var(--space-sm);
    border-color: var(--primary-border-color);
    background-color: var(--mobile-button-bg-color); 
  }

  .mobile:focus{
    background-color: var(--mobile-button-hover-color);
  }
</style>