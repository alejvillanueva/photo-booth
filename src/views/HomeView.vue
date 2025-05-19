<script setup>
  import { ref, watch} from 'vue';

  import logo from '../assets/gramercy_logo.png';
  import ActionButton from '../components/ActionButton.vue';
  import ContentText from '../components/ContentText.vue';

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
    <ContentText>
      <template #main>
        Welcome to the Photo Experience!
      </template>
      <template #sub>
        Smile, snap, and share with our digital photo booth experience.
      </template>
    </ContentText>
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
    box-shadow: 0 0 var(--box-shadow-blur-radius) var(--box-shadow-spread-radius) var(--input-box-shadow-color);
    padding: var(--space-xxs) var(--space-xxs) var(--space-xxs) 0px;
    align-items: center;
  }
  .home-screen-input-controls:hover{
    border-color: gray;
  }
  .home-screen-input-controls.invalid{
    box-shadow: 0 0 var(--box-shadow-blur-radius) var(--box-shadow-spread-radius) var(--primary-warning-color);
  }
   .home-screen-input-controls.invalid:hover{
    border-color: var(--secondary-warning-color);
  }
  .home-screen-input-warning{
    visibility: hidden;
    padding: var(--space-xs) 0px 0px var(--space-lg);
  }
  .home-screen-input-warning.invalid{
    text-align: left;
    visibility: visible;
    color: var(--secondary-warning-color);
    font-weight: var(--font-weight-light);
    font-size: small;
  }
  
</style>
