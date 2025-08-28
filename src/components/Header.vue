<script setup>
import { ref, onMounted } from "vue";
import profile from "../assets/profile.JPG";
import BackgroundStars from "./BackgroundStars.vue";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { faLinkedin, faGithub } from "@fortawesome/free-brands-svg-icons";

const isVisible = ref(false);

onMounted(() => {
  const header = document.getElementById("header");
  const observer = new IntersectionObserver(
    (entries) => {
      if (entries[0].isIntersecting) {
        isVisible.value = true; // masuk viewport → tampil
      } else {
        isVisible.value = false; // keluar viewport → reset
      }
    },
    { threshold: 0.2 }
  );
  observer.observe(header);
});
</script>

<template>
  <BackgroundStars />

  <div
    id="header"
    class="relative flex flex-col md:flex-row items-center bg-transparent text-white border-2 border-blue-600 shadow-[0_0_10px_#2c75ff,0_0_22px_#2c75ff] rounded-xl w-11/12 md:w-3/5 h-auto md:h-[25rem] mx-auto mt-[7rem] md:mt-[12rem] p-6 mb-[10rem] md:-translate-x-11 scroll-mt-30 transition-all duration-1000 ease-out"
    :class="
      isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'
    "
  >
    <!-- Image -->
    <div
      class="flex justify-center md:absolute md:right-0 md:top-1/2 md:-translate-y-1/2 md:translate-x-1/2 z-10 mb-6 md:mb-0 transition-all duration-1000 delay-200"
      :class="isVisible ? 'opacity-100 scale-100' : 'opacity-0 scale-75'"
    >
      <img
        :src="profile"
        alt="Profile"
        class="w-[180px] h-[180px] md:w-[240px] md:h-[240px] object-cover rounded-full border-2 border-blue-600 shadow-[0_0_15px_#2c75ff,0_0_30px_#2c75ff]"
      />
    </div>

    <!-- Profile Info -->
    <div class="text-center md:text-left md:ml-[40px] md:mr-[150px] text-white">
      <h2
        class="text-2xl sm:text-3xl md:text-4xl italic font-semibold mb-5 transition-all duration-1000 delay-300"
        :class="
          isVisible ? 'opacity-100 translate-x-0' : 'opacity-0 -translate-x-10'
        "
      >
        Hi, saya
        <span class="text-blue-600 font-extrabold">Irfan Jarulloh</span>
      </h2>

      <div
        class="name text-2xl md:text-4xl border-b-5 border-blue-600 mb-4 inline-block transition-all duration-1000 delay-500"
        :class="
          isVisible ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-10'
        "
      >
        Fullstack Developer
      </div>

      <p
        class="text-base md:text-lg mb-4 transition-all duration-1000 delay-700"
        :class="
          isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-5'
        "
      >
        Saya senang belajar hal baru, mengembangkan keterampilan, dan berkarya
        melalui berbagai proyek kreatif.
      </p>

      <!-- Sosmed -->
      <div
        class="flex justify-center md:justify-start gap-8 mt-5 transition-all duration-1000 delay-900"
        :class="
          isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-5'
        "
      >
        <a
          href="https://www.linkedin.com/in/irfan-jarulloh-196b98293/"
          target="_blank"
          class="relative group flex flex-col items-center text-3xl md:text-4xl text-white hover:text-blue-600 transition duration-300"
        >
          <FontAwesomeIcon :icon="faLinkedin" />
          <span
            class="w-0 h-[2px] bg-blue-600 transition-all duration-300 mt-2 md:mt-0 md:absolute md:left-1/2 md:-bottom-1 md:group-hover:left-0 group-hover:w-full"
          ></span>
        </a>

        <a
          href="https://github.com/irfanjarulloh25"
          target="_blank"
          class="relative group flex flex-col items-center text-3xl md:text-4xl text-white hover:text-blue-600 transition duration-300"
        >
          <FontAwesomeIcon :icon="faGithub" />
          <span
            class="w-0 h-[2px] bg-blue-600 transition-all duration-300 mt-2 md:mt-0 md:absolute md:left-1/2 md:-bottom-1 md:group-hover:left-0 group-hover:w-full"
          ></span>
        </a>
      </div>
    </div>
  </div>
</template>
