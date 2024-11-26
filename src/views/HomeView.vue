<template>
  <!-- Links -->
  <a href="https://x.com/">
    <img src="@/assets/twitter.png" class="w-20 h-20 absolute max-h-screen top-44 left-[560px] socials" />
  </a>
  <a href="https://telegram.org/">
    <img src="@/assets/tg.png" class="w-20 h-20 absolute max-h-screen top-44 left-[700px] socials" />
  </a>
  <a href="https://pump.fun/">
    <img src="@/assets/pf (1).png" class="w-20 h-20 absolute max-h-screen top-44 left-[840px] socials" />
  </a>

  <!-- Clickable images for background change -->
  <img 
    src="@/assets/bg2.gif" 
    class="w-20 h-20 absolute max-h-screen top-44 left-[980px] socials" 
    @click="changeBackground('/src/assets/bg2.gif')" 
    alt="Background 2" 
  />
  <img 
    src="@/assets/bg3.gif" 
    class="w-20 h-20 absolute max-h-screen top-44 left-[1120px] socials" 
    @click="changeBackground('/src/assets/bg3.gif')" 
    alt="Background 3" 
  />
  <img 
    src="@/assets/bg.gif" 
    class="w-20 h-20 absolute max-h-screen top-44 left-[1260px] socials" 
    @click="changeBackground('/src/assets/bg.gif')" 
    alt="Background Default" 
  />

  <!-- Background container -->
  <div class="min-h-screen bg-no-repeat bg-cover" :style="{ backgroundImage: `url(${currentBackground})` }"></div>

  <!-- Custom cursor -->
  <div class="custom-cursor"></div>
</template>




<script setup lang="ts">
import { ref } from 'vue';

// Reactive variable for the background image
const currentBackground = ref('/src/assets/bg.gif');

// Function to change the background
function changeBackground(imageUrl: string) {
  currentBackground.value = imageUrl;
}
</script>



<style>
html {
  cursor: url('/x.ico'), auto;
}

.socials:hover {
  transform: scale(1.2); /* Enlarge the image by 20% */
}

body {
  margin: 0;
  height: 100vh;
}

.min-h-screen {
  transition: background-image 0.5s ease;
  height: 100vh;
  width: 100vw;
}
</style>

