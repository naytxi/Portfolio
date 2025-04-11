<template>
    <div class="support-wrapper">
      <h2 class="support-title">SUPPORT THE FAIRIES</h2>
      <p class="support-message">
        If you believe in magic, help us keep the spark alive ✨
      </p>
      <button class="donate-button" @click="handleDonate">Donate</button>
  
      <div class="glow-effect"></div>
    </div>
  </template>
  
  <script setup>
  import { onMounted, onUnmounted, defineEmits } from 'vue';
  
  const emit = defineEmits(['stopRain', 'resumeRain']);
  
  const handleDonate = () => {
    alert("Thanks for your magical support!");
  };
  
  onMounted(() => {
    emit('stopRain'); // notifica al padre que pare la lluvia
  });
  
  onUnmounted(() => {
    emit('resumeRain'); // si querés que vuelva si se sale del componente
  });
  </script>
  
  <style scoped>
  .support-wrapper {
    padding: 4rem 2rem;
    max-width: 800px;
    margin: 0 auto;
    text-align: center;
    position: relative;
  }
  
  .support-title {
    font-family: "Cinzel", serif;
    font-size: 2.5rem;
    color: #f5ede1;
    margin-bottom: 1.5rem;
  }
  
  .support-message {
    font-family: "Playfair Display", serif;
    font-size: 1.3rem;
    color: #f5ede1;
    margin-bottom: 2rem;
  }
  
  .donate-button {
    padding: 1rem 2rem;
    font-family: "Cinzel", serif;
    font-size: 2rem;
    background: linear-gradient(to right, #f7c948, #f78c6b);
    border: none;
    border-radius: 12px;
    color: #1e1e1e;
    cursor: pointer;
    transition: transform 0.3s ease;
  }
  
  .donate-button:hover {
    transform: scale(1.20);
  }
  
  .glow-effect {
    position: absolute;
    bottom: -100px;
    left: 50%;
    transform: translateX(-50%);
    width: 500px;
    height: 500px;
    background: radial-gradient(circle, rgba(255, 223, 102, 0.4), rgba(255, 153, 51, 0));
    pointer-events: none;
    filter: blur(50px);
  }
  </style>
  