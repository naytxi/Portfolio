<template>
    <div class="fog" :style="{ transform: fogTransform }"></div>
  </template>
  
  <script setup>

  </script>
  
  <style>
  .fog {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 80vh;
    background-image: url('../assets/fog.png');
    background-size: cover;
    z-index: 0;
    pointer-events: none;
    overflow:hidden;
  }

  </style>
  