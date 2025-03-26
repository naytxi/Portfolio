<template>
    <div class="clouds">
      <div class="clouds-1"></div>
      <div class="clouds-2"></div>
      <div class="clouds-3"></div>
    </div>
  </template>
  
  <script setup>
  
  </script>
  
  <style scoped>
  @import url('https://fonts.googleapis.com/css?family=Oswald');
  
  .clouds {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 100%;
    pointer-events: none;
    overflow: hidden;
    opacity: 0.4;
  }
  
  .clouds-1,
  .clouds-2,
  .clouds-3 {
    background-repeat: repeat-x;
    position: absolute;
    top: 0;
    right: 0;
    left: 0;
    height: 500px;
  }
  
  .clouds-1 {
    background-image: url('https://s.cdpn.io/15514/clouds_2.png');
    animation: clouds-loop-1 20s infinite linear;
  }
  
  .clouds-2 {
    background-image: url('https://s.cdpn.io/15514/clouds_1.png');
    animation: clouds-loop-2 15s infinite linear;
  }
  
  .clouds-3 {
    background-image: url('https://s.cdpn.io/15514/clouds_3.png');
    animation: clouds-loop-3 17s infinite linear;
  }
  
  @keyframes clouds-loop-1 {
    to {
      background-position: -1000px 0;
    }
  }
  
  @keyframes clouds-loop-2 {
    to {
      background-position: -1000px 0;
    }
  }
  
  @keyframes clouds-loop-3 {
    to {
      background-position: -1579px 0;
    }
  }
  </style>
  