<script setup>
  import ActionButton from '../components/ActionButton.vue';
  import AppHeader from '../components/AppHeader.vue';
  import ContentText from '../components/ContentText.vue';
  
  const props = defineProps({
    name: {
      type: String,
      default: "User",
    },
    photo: {
      type: String,
      default: "",
    }
  });

  const emit = defineEmits(['reset']);

  const startOver = () => {
    emit('reset');
  }
</script>
<template>
  <div class="thank-you-container">
    <AppHeader />
    <ContentText>
      <template #main> 
        You are all set. Thanks, {{ name }}!
      </template>
      <template #sub> 
        Hope you enjoyed our photo booth experience! Feel free to start over and submit a new photo. 
      </template>
    </ContentText>
    <div class="thank-you-photo-controls">
      <img
        class="photo"
        :src="photo"
      >
      <ActionButton
        theme="secondary"
        @click="startOver"
      >
        Start Over?
      </ActionButton>
    </div>
  </div>
</template>
<style scoped>
  .photo{
      width: var(--sanvas-size);;
      border-radius: var(--border-radius);
      margin: 25px;
  }
  .thank-you-container{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .thank-you-photo-controls{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>
