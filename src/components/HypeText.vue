<template>
  <div class="hype-text-container">
    <h1><slot name="main" /></h1>
    <h2><slot name="sub" /></h2>
  </div>
</template>
<style scoped>
  .hype-text-container{
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  h1, h2 {
    margin: 15px; /*SMALL MARGIN*/
    text-align: center;
  }
</style>