<script setup>
  const props = defineProps({
    theme: {
      type: String,
      default: "icon"
    }
  })
</script>
<template>
  <button :class="theme">
    <slot class="icon-image" />
  </button>
</template>
<style scoped>
  .icon {
    display: flex;
    background-color: var(--overlay-color);
    border-color: var(--primary-border-color);
    border-radius: var(--border-radius-circle);
    padding: var(--space-xxs);
    margin: var(--space-md) var(--space-sm);
  }

  .icon:hover{
    background-color: var(--primary-bg-color);
  }
</style>