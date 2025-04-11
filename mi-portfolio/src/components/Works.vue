<template>
  <div 
    v-for="(member, index) in members"
  :key="index"
  class="carousel-line-wrapper"
  >
  <h3 class="carousel-title">{{ member.name }}</h3>
  <div
    class="carousel-line"
    :style="{ animationDirection: member.direction === 'right-to-left' ? 'normal' : 'reverse' }"
  >
    <div class="carousel-track"
    :class="member.direction === 'right-to-left' ? 'scroll-left' : 'scroll-right'">
      <img
        v-for="(image, i) in [...member.images, ...member.images]"
        :key="i"
        :src="image"
        class="carousel-image"
      />
    </div>
  </div>
</div>
</template>

<script setup>
const members = [
  {
    name: "Flora",
    images: [
    new URL("../assets/nay.jpeg", import.meta.url).href,
    new URL("../assets/nay4.jpg", import.meta.url).href,
    new URL("../assets/nay3.jpg", import.meta.url).href,
    new URL("../assets/nay9.png", import.meta.url).href,
    new URL("../assets/nay6.png", import.meta.url).href
    ],
    direction: "right-to-left"
  },
  {
    name: "Fauna",
    images: [
      new URL("../assets/olatz1.jpg", import.meta.url).href,
      new URL("../assets/olatz6.jpeg", import.meta.url).href,
      new URL("../assets/olatz3.jpeg", import.meta.url).href,
      new URL("../assets/olatz4.jpeg", import.meta.url).href,
      new URL("../assets/olatz5.jpeg", import.meta.url).href
    ],
    direction: "left-to-right"
  },
  {
    name: "Merriweather",
    images: [
      new URL("../assets/tania1.webp", import.meta.url).href,
      new URL("../assets/tania2.webp", import.meta.url).href,
      new URL("../assets/tania3.webp", import.meta.url).href,
      new URL("../assets/tania4.webp", import.meta.url).href,
      new URL("../assets/tania5.webp", import.meta.url).href
    ],
    direction: "right-to-left"
  }
];
</script>

<style scoped>

.carousel-line-wrapper {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  align-items: flex-start;
  padding: 0 2rem;
}

.carousel-title {
  color: #f5ede1;
  font-family: 'Cinzel', serif;
  font-size: 2rem;
  margin-bottom: 0.5rem;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.4);
}


.carousel-line {
  overflow: hidden;
  height: 20rem;
  position: relative;
}

.carousel-track {
  display: flex;
  width: max-content;
  animation: scroll-carousel 10s linear infinite;
}

.carousel-image {
  width: 20rem;
  height: 20rem;
  object-fit: cover;
  margin-right: 1rem;
  border-radius: 12px;
}

.scroll-left {
  animation: scroll-left 15s linear infinite;
}

/* Movimiento hacia la derecha */
.scroll-right {
  animation: scroll-right 15s linear infinite;
}
/* Animación horizontal */

@keyframes scroll-left {
  0% {
    transform: translateX(0%);
  }
  100% {
    transform: translateX(-50%);
  }
}

@keyframes scroll-right {
  0% {
    transform: translateX(-50%);
  }
  100% {
    transform: translateX(0%);
  }
}
</style>
