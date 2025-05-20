<script setup>
  import { onMounted, ref } from 'vue';

  import ContentText from '../components/ContentText.vue';
  import AppHeader from '../components/AppHeader.vue';
  import ActionButton from '../components/ActionButton.vue';
  
  const video = ref(null);
  const canvas = ref(null);
  const countdown = ref(3);
  const startCountdown = ref(false);

  const emit = defineEmits(['review', 'exit']);

  const startCamera = () => {
    const mediaProps = {
      video: true
    }

    navigator.mediaDevices.getUserMedia(mediaProps).then(stream => {
      video.value.srcObject = stream;
    }).catch((error) => {
      console.error("Error access webcam: ", error);
    })
  }

  const closeCamera = () => {
    const { srcObject } = video.value;
    srcObject.getTracks().forEach(track => {
      track.stop();
      video.value = null;
    });
  }
  
  onMounted(() => {
    startCamera();
  })

  const pressTake = () => {
    startCountdown.value = true;
    
    const intervalID = setInterval(() => {
      countdown.value--;

      if(countdown.value === 0){
        clearInterval(intervalID);
        takePhoto();
      }
    }, 1000);
  } 

  const takePhoto = () => {
    const context = canvas.value.getContext('2d');
    const {videoWidth, videoHeight } = video.value;

    canvas.value.width = videoWidth;
    canvas.value.height = videoHeight;
    context.drawImage(video.value, 0, 0, videoWidth, videoHeight);

    const data = canvas.value.toDataURL("image/png");

    //closeCamera();
    emit('review', data)
  }

  const goHome = () => {
    closeCamera();
    emit('exit');
  }

</script>
<template>
  <div class="container">   
    <AppHeader
      :show-exit-button="true"
      @exit="goHome"
    />
    <div class="main">
      <ContentText>
        <template #main>
          Say cheese!
        </template>
        <template #sub>
          Position your face within the frame and take your photo whenever you're ready!
        </template>
      </ContentText>
      <div class="webcam-container">
        <div class="webcam-wrapper">
          <video 
            ref="video" 
            autoplay 
            class="media-canvas"
          />
          <div
            v-if="startCountdown"
            class="webcam-overlay"
          >
            {{ countdown }}
          </div>
          <canvas 
            ref="canvas" 
            hidden 
          />
        </div>
        <ActionButton
          theme="secondary"
          @click="pressTake"
        >
          Take Photo
        </ActionButton>
      </div>
    </div>
  </div>
</template>
<style scoped>

  video{
    margin: 0;
  }
  .webcam-wrapper{
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
    margin: var(--space-xl);
  }

  .webcam-overlay{
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    width: var(--canvas-size);
    height: 100%;
    border-radius: var(--border-radius);
    background-color: rgba(0, 0, 0, 0.3);
    font-size: 6rem;
  }

  @media (max-width: 600px) {
    .webcam-overlay {
      width: var(--canvas-size-mb);
    }
  }
</style>
