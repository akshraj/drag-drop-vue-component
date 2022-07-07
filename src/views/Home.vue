<template>
  <div class="home">
    <h1>DropZone</h1>
    <DropZone @drop.prevent="drop" @change="selectedFile" />
    <span class="file-info">File: {{ dropzoneFile.name }}</span>
  </div>
</template>

<script>
import DropZone from '@/components/DropZone.vue'
import { ref } from 'vue'

export default {
  name: 'Home',
  components: {
    DropZone
  },
  setup() {
    let dropzoneFile = ref('');

    function drop(e) {
      dropzoneFile.value = e.dataTransfer.files[0];
    }

    function selectedFile(e) {
      // dropzoneFile.value = document.querySelector('.dropzoneFile').files[0];
      dropzoneFile.value = e.target.files[0];
    }

    return { dropzoneFile, drop, selectedFile }
  }
}
</script>

<style scoped lang="scss">
.home {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background-color: #f1f1f1;

  h1 {
    font-size: 40px;
    margin-bottom: 32px;
  }

  .file-info {
    margin-top: 32px;
  }
}
</style>
