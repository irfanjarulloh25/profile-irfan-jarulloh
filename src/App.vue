<template>
  <BackgroundStars />
  <div class="relative z-10 text-white">
    <Navbar />
    <Header></Header>
    <About />
    <Skills />
    <Certificate />
    <Projects />
    <Contact />
    <Footer></Footer>
  </div>
</template>

<script setup>
import BackgroundStars from "./components/BackgroundStars.vue";
import Navbar from "./components/Navbar.vue";
import Header from "./components/Header.vue";
import About from "./components/About.vue";
import Skills from "./components/Skills.vue";
import Certificate from "./components/Certificate.vue";
import Projects from "./components/Projects.vue";
import Contact from "./components/Contact.vue";
import Footer from "./components/Footer.vue";
</script>
