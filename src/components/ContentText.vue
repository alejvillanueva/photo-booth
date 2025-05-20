<template>
  <div class="content-text-container">
    <h1><slot name="main" /></h1>
    <h3><slot name="sub" /></h3>
  </div>
</template>
<style scoped>
  .content-text-container{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>