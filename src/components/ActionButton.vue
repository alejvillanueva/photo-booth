<script setup>
  const props = defineProps(['theme'])
</script>
<template>
  <button :class="theme">
    <slot />
  </button>
</template>
<style scoped>
  button{
    font-family: 'Lexend';
    border-radius: 25px;
    cursor: pointer;
    padding: 10px 25px;
    font-weight: bolder;
  }

  .primary{
    background-color: #0008db;
    color: white;
    border-color: white;
  }

  .primary:hover{
    background-color: white;
    color: #0008db;
    transition: .3s;   
    border-color: transparent;
    box-shadow: 0 0 25px 1px white;

  }

  .secondary{
    background-color: white;
    color: #0008db;
    border-color: #0008db;
  }
  .secondary:hover{
    background-color: #0008db;
    color: white;  
    transition: .3s;
    box-shadow: 0 0 25px 1px white;
  }

</style>