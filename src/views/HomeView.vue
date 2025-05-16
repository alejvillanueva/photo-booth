<script setup>
  import logo from '../assets/gramercy_logo.png';
  import { ref, watch} from 'vue';

  const userName = ref('');
  const validInput = ref(true);

  const emit = defineEmits(['start']);
  const submitName = () => {
    validInput.value = !!userName.value.trim();
    console.log("validInput", validInput.value)
    if(validInput.value) {
      const name = userName.value;
      emit('start', name)
    } 
  }

  watch(userName, (newName, oldName) => {
    if(!oldName.trim().length && newName.length) {
      validInput.value = true;
    }
  })

</script>
<template>
  <div class="home-screen">
    <img 
      class="home-screen-logo"
      :src="logo"
      alt="Gramercy Tech"
    >
    <h1>Welcome to the Photo Experience!</h1>
    <h2> Smile, snap, and share with our difital photo booth experience.</h2>
    <p>Enter your name to begin.</p> 
    <div class="home-screen-input-container">
      <div class="home-screen-input-controls">
        <input 
          v-model="userName"
          class="home-screen-input"
          :class="{invalid: !validInput}"
          @keydown.enter="submitName"
        >
        <button @click="submitName"> 
          Start
        </button>
      </div>
      <small 
        :class="{invalid: !validInput}"
        class="home-screen-input-warning" 
      >
        Name is required
      </small>
    </div>
  </div>
</template>
<style scoped>
  .home-screen{
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
  }
  .home-screen-logo{
      max-width: 5vmax;
      height: auto;
  }
  .home-screen-input-container{
    display: flex;
    flex-direction: column;
  }
  .home-screen-input{
      font-family: 'Lexend';
      border: 1px solid white; /* Global */
      border-radius: 10px;
      padding: 5px; /* Global */
      margin-right: 5px;
  }
  .home-screen-input:hover{
       border-color: darkblue;
  }
  .home-screen-input:focus{
    outline: 2px solid lightblue;
    border-color: white;
  }
  .home-screen-input.invalid{
    box-shadow: 0 0 10px 3px red;
  }
  .home-screen-input-warning{
    visibility: hidden;
    padding: 5px;
  }
  .home-screen-input-warning.invalid{
    text-align: left;
    visibility: visible;
    color: lightcoral;
    font-weight: 300;
    font-size: small;
  }
  
</style>
