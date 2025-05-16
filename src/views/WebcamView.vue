<script setup>
  import { onMounted, ref } from 'vue';

  const video = ref(null);
  const canvas = ref(null);

  const emit = defineEmits(['review']);

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

</script>
<template>
  <div class="webcam">
    <video 
      ref="video" 
      autoplay 
    />
    <canvas 
      ref="canvas" 
      hidden 
    />
    <button @click="takePhoto">
      Take
    </button>
  </div>
</template>
<style scoped>
  .webcam{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  video{
    max-width: 50vmax;
  }
</style>
