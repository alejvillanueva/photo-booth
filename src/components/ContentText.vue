<template>
  <div class="content-text-container">
    <h1><slot name="main" /></h1>
    <h2><slot name="sub" /></h2>
  </div>
</template>
<style scoped>
  .content-text-container{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>