<template>
    <canvas ref="rainCanvas"></canvas>
  </template>
  
  <script setup>
  import { onMounted, ref } from "vue";
  
  const rainCanvas = ref(null);
  const drops = [];
  
  onMounted(() => {
    const canvas = rainCanvas.value;
    const ctx = canvas.getContext("2d");
  
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  
    // Crear gotas de lluvia
    for (let i = 0; i < 100; i++) {
      drops.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        speed: Math.random() * 4 + 2,
        length: Math.random() * 15 + 5,
      });
    }
  
    function drawRain() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = "rgba(173, 216, 230, 0.5)"; // Color azul claro con transparencia
  
      drops.forEach((drop) => {
        ctx.beginPath();
        ctx.moveTo(drop.x, drop.y);
        ctx.lineTo(drop.x, drop.y + drop.length);
        ctx.strokeStyle = "rgba(173, 216, 230, 0.7)";
        ctx.lineWidth = 1;
        ctx.stroke();
  
        drop.y += drop.speed;
        if (drop.y > canvas.height) {
          drop.y = 0;
          drop.x = Math.random() * canvas.width;
        }
      });
  
      requestAnimationFrame(drawRain);
    }
  
    drawRain();
  
    // Ajustar tamaño al cambiar ventana
    window.addEventListener("resize", () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    });
  });
  </script>
  
  <style>
  canvas {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    max-width: 100vw;
    max-height: 100vh;
    pointer-events: none;
    background-color:transparent;
    z-index: 0;
    overflow: hidden;
  }
  </style>
  