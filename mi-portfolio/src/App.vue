<template>
  <div class="main-container">
    <section class="app">
      <RainEffect />
      <Clouds />
      <div class="content">
        <img src="./assets/fairy-logo.png" class="logo" />
        <h1 class="title">THREE FAIRY GODMOTHERS</h1>
        <p class="description">A little group of artists</p>
      </div>
      <nav>
    <ul class="menu">
            <li ><a href="">Home</a></li>
            <li><a href="#">About</a></li>
            <li><a href="#">Works</a></li>
            <li><a href="#">Support</a></li>
            <li><a href="#">Contact</a></li>
        </ul>
</nav>
    </section>

    <section class="next-section">
      <About />
    </section>
  </div>
</template>

<script setup>
import RainEffect from "./components/Rain.vue";
import About from "./components/AboutMe.vue";
import Clouds from "./components/Clouds.vue"; 
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Cinzel:wght@400;700&family=Playfair+Display:wght@400;700&display=swap");

/* Contenedor principal */
.main-container {
  width: 100vw;
  height: 100vh;
  overflow-x: hidden;
  display: flex;
  margin: 0;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  gap: 20rem;
}

/* Primera sección */
.app {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  margin-right: 40rem;
}

/* Contenedor del contenido */
.content {
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  margin-bottom: 5rem;
}

/* Logo */
.logo {
  width: 15rem;
  height: auto;
  margin-bottom: 20px;
}

/* Estilo del título */
.title {
  font-family: "Cinzel", serif;
  font-size: 4rem;
  font-weight: 700;
  color: #f5ede1;
  text-transform: uppercase;
  text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.5);
}

/* Estilo de la descripción */
.description {
  font-family: "Playfair Display", serif;
  font-size: 1.5rem;
  font-weight: 400;
  color: #f5ede1;
  margin-top: 10px;
  text-shadow: 1px 1px 4px rgba(0, 0, 0, 0.4);
}

.menu {
  display: flex;
  flex-direction: row;
  list-style-type: none;
  padding: 0;
  margin: 0;
  gap: 2rem;
  font-size: 1.5rem;

}

.menu a {
  color: #f5ede1;
  text-decoration: none;
  display: inline-block; 
  padding: 10px; 
  transition: transform 0.3s ease; 
}

.menu a:hover {
  transform: scale(1.1);
}
/* Sección AboutMe */
.next-section {
  width: 100vw;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 5rem 0;
  margin-right: 50rem;
  margin-top: 8rem;
}
</style>
