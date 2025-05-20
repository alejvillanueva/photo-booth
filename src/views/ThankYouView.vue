<script setup>
  import ActionButton from '../components/ActionButton.vue';
  import AppHeader from '../components/AppHeader.vue';
  import ContentText from '../components/ContentText.vue';
  import MobileButton from '../components/MobileButton.vue';

  import downloadIcon from '../assets/download-icon.svg';
  import sendIcon from '../assets/send-icon.svg';

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

  const generateTimestamp = () => {
    const todaysDate = new Date();
    const date = todaysDate.getDate();
    const month = todaysDate.getMonth() + 1;
    const year = todaysDate.getFullYear();

    return `${year}-${month}-${date}`;
  }
  const downloadImage = () => {
    const link = document.createElement('a');
    link.href = props.photo;
    
    const timestamp = generateTimestamp();
    link.download = `Photobooth-${timestamp}.png`;
    link.click();
    link.remove();
  }

</script>
<template>
  <div class="container">
    <AppHeader />
    <div class="main">
      <ContentText>
        <template #main> 
          Success! Thanks, {{ name }}!
        </template>
        <template #sub> 
          Hope you enjoyed our photo booth experience! Feel free to start over and submit a new photo. 
        </template>
      </ContentText>
      <div class="thank-you-photo-controls">
        <img
          class="media-canvas"
          :src="photo"
        >
        <ActionButton
          theme="secondary"
          @click="startOver"
        >
          Start Over
        </ActionButton>
        <div class="mobile-actions">
          <MobileButton @click="downloadImage">
            <img
              class="mobile-button-image"
              :src="downloadIcon"
              alt="Download Image"
            >
          </MobileButton>
          <MobileButton>
            <img
              class="mobile-button-image"
              :src="sendIcon"
              alt="Share Image"
            >
          </MobileButton>
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped>
  .thank-you-photo-controls{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .mobile-actions{
    display: none;
  }

  .mobile-button-image{
    max-width: 3vmax;
  }
  @media (max-width: 600px) {
    .mobile-actions{
      display: flex;
    }
  }
</style>
