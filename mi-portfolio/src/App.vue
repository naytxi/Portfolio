<template>
  <div class="main-container">
    <RainEffect />
    <section class="app">
      <Clouds :style="{ opacity: cloudsOpacity }" />
      <div class="content">
        <img src="./assets/fairy-logo.png" class="logo" />
        <h1 class="title">THREE FAIRY GODMOTHERS</h1>
        <p class="description">A little group of artists</p>
        <button class="hamburger" @click="toggleMenu">&#9776;</button>
        <div class="submenu" v-if="menuOpen">
          <ul class="menu">
            <li><a @click.prevent="scrollToSection('home')">Home</a></li>
            <li><a @click.prevent="scrollToSection('aboutSection')">About</a></li>
            <li><a @click.prevent="scrollToSection('worksSection')">Works</a></li>
            <li><a @click.prevent="scrollToSection('supportSection')">Support</a></li>
            <li><a @click.prevent="scrollToSection('contactSection')">Contact</a></li>
          </ul>
        </div>
      </div>
    </section>

    <Fog :style="{ opacity: fogOpacity }" />

    <section
      class="next-section"
      ref="aboutSection"
      :class="{ visible: aboutVisible }"
    >
      <h2 class="title">ABOUT</h2>
      <About />
    </section>

    <section
      class="works-section"
      ref="worksSection"
      :class="{ visible: worksVisible }"
    >
      <h2 class="title">WORKS</h2>
      <Works />
    </section>

    <section
      class="contact-section"
      ref="contactSection"
      :class="{ visible: contactVisible }"
    >
      <h2 class="title">CONTACT</h2>
      <Contact />
    </section>

    <section
      class="support-section"
      ref="supportSection"
      :class="{ visible: supportVisible }"
    >
      <Support @stopRain="stopRain" @resumeRain="resumeRain" />
    </section>

    <RainEffect v-if="showRain" />
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
import RainEffect from "./components/Rain.vue";
import About from "./components/AboutMe.vue";
import Clouds from "./components/Clouds.vue";
import Works from "./components/Works.vue";
import Fog from "./components/Fog.vue";
import Contact from "./components/Contact.vue";
import Support from "./components/Support.vue";

// refs para las secciones
const aboutSection = ref(null);
const worksSection = ref(null);
const contactSection = ref(null);
const supportSection = ref(null);

// estado del menú
const menuOpen = ref(false);
const toggleMenu = () => (menuOpen.value = !menuOpen.value);

// opacidad de nubes/niebla
const cloudsOpacity = ref(0.5);
const fogOpacity = ref(0.3);

// control de visibilidad de secciones
const aboutVisible = ref(false);
const worksVisible = ref(false);
const contactVisible = ref(false);
const supportVisible = ref(false);

// lluvia
const showRain = ref(true);
const stopRain = () => (showRain.value = false);
const resumeRain = () => (showRain.value = true);

// efecto scroll para opacidades
const handleScroll = () => {
  const scrollPosition = window.scrollY;
  const opacityFactor = Math.max(0, Math.min(0.5, 0.5 - scrollPosition / 500));
  cloudsOpacity.value = opacityFactor;
  fogOpacity.value = opacityFactor;
};

// función para hacer scroll suave
const scrollToSection = (sectionRefName) => {
  if (sectionRefName === "home") {
    window.scrollTo({ top: 0, behavior: "smooth" });
    menuOpen.value = false;
    return;
  }

  const sections = {
    aboutSection: aboutSection.value,
    worksSection: worksSection.value,
    contactSection: contactSection.value,
    supportSection: supportSection.value,
  };

  const section = sections[sectionRefName];
  if (section) {
    section.scrollIntoView({ behavior: "smooth" });
    menuOpen.value = false;
  }
};

// observadores para animación de entrada
onMounted(() => {
  window.addEventListener("scroll", handleScroll);

  const observeVisibility = (element, callback) => {
    if (!element) return;
    const observer = new IntersectionObserver(
      ([entry]) => callback(entry.isIntersecting),
      { threshold: 0.1 }
    );
    observer.observe(element);
  };

  observeVisibility(aboutSection.value, (isVisible) => (aboutVisible.value = isVisible));
  observeVisibility(worksSection.value, (isVisible) => (worksVisible.value = isVisible));
  observeVisibility(contactSection.value, (isVisible) => (contactVisible.value = isVisible));
  observeVisibility(supportSection.value, (isVisible) => (supportVisible.value = isVisible));
});

onBeforeUnmount(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Cinzel:wght@400;700&family=Playfair+Display:wght@400;700&display=swap");

html,
body {
  margin: 0;
  padding: 0;
  overflow-x: auto;
  background-color: rgb(24, 23, 23);
}

.main-container {
  display: flex;
  flex-direction: column;
  overflow: hidden;
  width: 100%;
  max-width: 100vw;
  gap: 4rem;
}

.app {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
  z-index: 2;
}

.content {
  z-index: 2;
  margin-bottom: 5rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.logo {
  width: 15rem;
  height: auto;
  margin-bottom: 20px;
}

.title {
  font-family: "Cinzel", serif;
  font-size: 4rem;
  font-weight: 700;
  color: #f5ede1;
  text-transform: uppercase;
  text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.5);
}

.description {
  font-family: "Playfair Display", serif;
  font-size: 1.5rem;
  font-weight: 400;
  color: #f5ede1;
  margin-top: 10px;
  text-shadow: 1px 1px 4px rgba(0, 0, 0, 0.4);
}

.hamburger {
  position: fixed;
  top: 5rem;
  right: 8rem;
  background: none;
  border: none;
  font-size: 2rem;
  color: #f5ede1;
  cursor: pointer;
  z-index: 10;
  border: solid 0.1rem;
  transition: 1s;
}

.hamburger:hover {
  background-color: #f5ede1;
  opacity: 0.2;
  transform: scale(0.8);
}

.submenu {
  position: fixed;
  top: 10rem;
  right: 8rem;
  background: rgba(0, 0, 0, 0.8);
  border-radius: 10px;
  padding: 1rem;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.2);
}

.submenu .menu {
  display: flex;
  flex-direction: column;
  gap: 1rem;
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

/* Animación de entrada */
.next-section,
.works-section,
.contact-section,
.support-section {
  opacity: 0;
  transform: translateY(100px);
  transition: opacity 0.8s ease-out, transform 0.8s ease-out;
}

.next-section.visible,
.works-section.visible,
.contact-section.visible,
.support-section.visible {
  opacity: 1;
  transform: translateY(0);
}

/* Responsivo */
@media (max-width: 768px) {
  .logo {
    width: 8rem;
    margin-bottom: 1rem;
  }

  .title {
    font-size: 2rem;
    text-align: center;
    padding: 0 1rem;
  }

  .description {
    font-size: 1rem;
    text-align: center;
    padding: 0 1rem;
  }

  .hamburger {
    top: 2rem;
    right: 2rem;
    font-size: 1.5rem;
  }

  .submenu {
    top: 6rem;
    right: 2rem;
  }
}

@media (min-width: 769px) and (max-width: 1024px) {
  .logo {
    width: 12rem;
  }

  .title {
    font-size: 3rem;
  }

  .description {
    font-size: 1.3rem;
  }

  .hamburger {
    top: 3rem;
    right: 3rem;
    font-size: 1.8rem;
  }

  .submenu {
    top: 8rem;
    right: 3rem;
  }
}
</style>
