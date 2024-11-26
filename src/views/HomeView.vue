<template>
  <!-- Links -->
  <a href="https://x.com/">
    <img src="@/assets/twitter.png" class=" absolute max-h-screen top-[180px] left-[480px] socials" />
  </a>
  <a href="https://telegram.org/">
    <img src="@/assets/Telegram.png" class="absolute max-h-screen top-[240px] left-[480px] socials" />
  </a>


  <a href="https://pump.fun/">
    <img src="@/assets/DexScreener.png" class=" absolute max-h-screen top-[300px] left-[480px] socials" />
  </a>
   <!--  <a href="https://pump.fun/">
    <img src="@/assets/pf (1).png" class="w-20 h-20 absolute max-h-screen top-44 left-[840px] socials" />


  </a> -->



  <!-- Background container -->
  <div class="min-h-screen bg-no-repeat bg-cover" :style="{ backgroundImage: `url(${currentBackground})` }"></div>

  <!-- Custom cursor -->
  <div class="custom-cursor"></div>
</template>




<script setup lang="ts">
import { ref, onMounted } from 'vue';
import bgChange from '@/assets/bg1.gif';
import bgDefault from '@/assets/bg2.gif';

// Reactive variable for the background image
const currentBackground = ref(bgDefault);

// Function to preload an image
function preloadImage(url: string) {
  return new Promise<void>((resolve) => {
    const img = new Image();
    img.src = url;
    img.onload = () => resolve();
  });
}

// Function to change the background
async function changeBackground(imageUrl: string) {
  await preloadImage(imageUrl);
  currentBackground.value = imageUrl;
}

onMounted(() => {
  document.addEventListener('click', () => {
    changeBackground(bgChange);
  });
});
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


