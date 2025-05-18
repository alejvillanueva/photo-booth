<script setup>
  import { onMounted, ref } from 'vue';

  import HypeText from '../components/HypeText.vue';
  import AppHeader from '../components/AppHeader.vue';
  import ActionButton from '../components/ActionButton.vue';
  const video = ref(null);
  const canvas = ref(null);

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
  
  onMounted(() => {
    startCamera();
  })

  const takePhoto = () => {
    const context = canvas.value.getContext('2d');
    const {videoWidth, videoHeight } = video.value;

    canvas.value.width = videoWidth;
    canvas.value.height = videoHeight;
    context.drawImage(video.value, 0, 0, videoWidth, videoHeight);

    const data = canvas.value.toDataURL("image/png");
    emit('review', data)
  }

  const goHome = () => {
    emit('exit');
  }

</script>
<template>
  <div class="webcam-container">   
    <AppHeader
      :show-exit-button="true"
      @exit="goHome"
    />
    <HypeText>
      <template #main>
        Position your face within the frame and take your photo whenever you're ready!
      </template>
      <template #sub>
        Say cheese!
      </template>
    </HypeText>
    <div class="webcam">
      <video 
        ref="video" 
        autoplay 
      />
      <canvas 
        ref="canvas" 
        hidden 
      />
      <ActionButton
        theme="secondary"
        @click="takePhoto"
      >
        Take Photo
      </ActionButton>
    </div>
  </div>
</template>
<style scoped>
  .webcam-container{
    display: flex;
    flex-direction: column;
    align-items: center;
    position: absolute;
    width: 100vw;
    height: 100vh;

  }
  .webcam{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  video{
    width: 50vmin;
    border-radius: 25px;
    margin: 25px;
  }
</style>
