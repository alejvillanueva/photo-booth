<script setup>
  import logo from '../assets/gramercy_logo.png';
import ActionButton from '../components/ActionButton.vue';
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
        <ActionButton
          theme="primary"
          @click="submitName"
        >
          start
        </ActionButton>
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
    position: absolute;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;

    height: 100vh;
    width: 100vw;
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
    display: flex;
    background-color: var(--secondary-bg-color);
    border: 1px solid var(--secondary-bg-color);
    border-radius: var(--border-radius);
    box-shadow: 0 0 10px 3px lightblue;
    padding: 2px 2px 2px 0px;
    align-items: center;
  }
  .home-screen-input-controls:hover{
    border-color: gray;
  }
  .home-screen-input-controls.invalid{
    box-shadow: 0 0 20px 3px var(--primary-warning-color);
  }
   .home-screen-input-controls.invalid:hover{
    border-color: var(--secondary-warning-color);
  }
  .home-screen-input-warning{
    visibility: hidden;
    padding: 5px 0px 0px 10px;
  }
  .home-screen-input-warning.invalid{
    text-align: left;
    visibility: visible;
    color: var(--secondary-warning-color);
    font-weight: var(--font-weight-light);
    font-size: small;
  }
  
</style>
