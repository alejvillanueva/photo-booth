<script setup>
  import logo from '../assets/gramercy_logo.png';
  import HypeText from '../components/HypeText.vue';
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
    <HypeText>
      <template #main>
        Welcome to the Photo Experience!
      </template>
      <template #sub>
        Smile, snap, and share with our digital photo booth experience.
      </template>
    </HypeText>
    <p>Enter your name to begin.</p> 
    <div class="home-screen-input-container">
      <div 
        class="home-screen-input-controls"
        :class="{invalid: !validInput}"
      >
        <input 
          v-model="userName"
          class="home-screen-input"
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
  input{
    font-family: 'Lexend';
    border: none;
  }
  input:focus{
    outline: none;
  }
  .home-screen{
    position: absolute;
    height: 100vh;
    width: 100vw;
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
  .home-screen-input-controls{
      font-family: 'Lexend';
      background-color: white;
      border: 1px solid white; /* Global */
      border-radius: 20px;
      padding: 10px; /* Global */
      margin-right: 5px;
      box-shadow: 0 0 10px 3px lightblue;
      box-sizing: border-box;
  }
  .home-screen-input-controls:hover{
       border-color: gray;
  }
  .home-screen-input-controls.invalid{
    box-shadow: 0 0 20px 3px red;
  }
   .home-screen-input-controls.invalid:hover{
       border-color: lightcoral;
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
