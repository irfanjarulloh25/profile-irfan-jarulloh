<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import robotImg from "../assets/robot.png";
import tailwindImg from "../assets/tailwind1.png";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { faDatabase } from "@fortawesome/free-solid-svg-icons";
import {
  faHtml5,
  faCss3Alt,
  faJs,
  faVuejs,
  faNodeJs,
  faReact,
  faBootstrap, faPhp,
} from "@fortawesome/free-brands-svg-icons";

// Skill list
const skills = [
  { icon: faHtml5, color: "text-orange-500", angle: 0, name: "HTML5" },
  { icon: faCss3Alt, color: "text-blue-500", angle: 40, name: "CSS3" },
  { icon: faJs, color: "text-yellow-400", angle: 80, name: "JavaScript" },
  { icon: faVuejs, color: "text-green-500", angle: 120, name: "Vue.js" },
  { icon: faNodeJs, color: "text-green-600", angle: 160, name: "Node.js" },
  { icon: faReact, color: "text-blue-400", angle: 200, name: "React.js" },
  { icon: faDatabase, color: "text-red-500", angle: 240, name: "SQL" },
  {
    icon: faBootstrap,
    color: "text-purple-500",
    angle: 280,
    name: "Bootstrap",
  },
  { img: tailwindImg, color: "text-sky-400", angle: 320, name: "Tailwind" },
  {
    icon: faPhp,
    color: "text-indigo-500",
    angle: 360,
    name: "PHP",
  },
];

const orbitRadius = ref(160);
const containerRef = ref(null);

// Untuk responsive
const windowWidth = ref(window.innerWidth);
const updateWidth = () => (windowWidth.value = window.innerWidth);

onMounted(() => {
  // Update orbit radius
  const updateRadius = () => {
    if (containerRef.value) {
      const w = containerRef.value.clientWidth;

      // Jika layar < 768px, orbit lebih besar supaya skill tidak berdempetan
      if (window.innerWidth < 768) {
        orbitRadius.value = Math.max(120, w / 2); // radius minimal 120px
      } else {
        orbitRadius.value = Math.min(160, w / 2.5); // desktop
      }
    }
  };
  updateRadius();
  window.addEventListener("resize", updateRadius);
  window.addEventListener("resize", updateWidth);
});

onUnmounted(() => {
  window.removeEventListener("resize", updateWidth);
});
</script>

<template>
  <section id="skills" class="scroll-mt-30">
  <!-- Judul -->
  <div class="text-center mb-10">
    <h3
      class="text-3xl md:text-4xl font-bold text-white inline-block border-b-4 border-blue-600 pb-2"
    >
      My Skills
    </h3>
  </div>

  <!-- Container utama -->
  <div
    class="relative flex flex-col md:flex-row items-center bg-transparent text-white border-2 border-blue-600 rounded-xl shadow-[0_0_10px_#2c75ff,0_0_22px_#2c75ff] w-11/12 md:w-4/5 lg:w-2/3 h-auto md:h-[28rem] mx-auto mt-6 p-6 mb-40"
  >
    <div class="flex flex-col md:flex-row items-center w-full gap-8">
      <!-- Kiri: Robot + orbit -->
      <div
        ref="containerRef"
        class="relative w-11/12 md:w-1/2 flex justify-center items-center min-h-[360px]"
      >
        <!-- Robot -->
        <img
          :src="robotImg"
          alt="Robot"
          class="rounded-full z-10 transition-all"
          :class="
            windowWidth < 768
              ? 'w-44 h-44'
              : windowWidth < 1024
              ? 'w-40 h-40'
              : 'w-56 h-56'
          "
        />

        <!-- Lingkaran orbit -->
        <svg class="absolute top-0 left-0 w-full h-full pointer-events-none">
          <circle
            :cx="'50%'"
            :cy="'50%'"
            :r="orbitRadius"
            stroke="#2c75ff"
            stroke-width="2"
            fill="none"
          />
        </svg>

        <!-- Skill -->
        <div
          v-for="skill in skills"
          :key="skill.name"
          class="group relative flex justify-center items-center rounded-full bg-black border-2 border-blue-600 shadow-[0_0_5px_#2c75ff,0_0_10px_#2c75ff] hover:scale-110 transition-all z-20"
          :class="skill.color"
          :style="{
            width: windowWidth < 768 ? '3rem' : '3.5rem',
            height: windowWidth < 768 ? '3rem' : '3.5rem',
            top: `calc(50% + ${
              Math.sin((skill.angle * Math.PI) / 180) * orbitRadius
            }px - ${windowWidth < 768 ? 24 : 28}px)`,
            left: `calc(50% + ${
              Math.cos((skill.angle * Math.PI) / 180) * orbitRadius
            }px - ${windowWidth < 768 ? 24 : 28}px)`,
            position: 'absolute',
          }"
        >
          <!-- Icon -->
          <template v-if="skill.icon">
            <FontAwesomeIcon
              :icon="skill.icon"
              class="text-2xl md:text-3xl z-10"
            />
          </template>

          <!-- Gambar (misal Tailwind) -->
          <template v-else-if="skill.img">
            <img
              :src="skill.img"
              alt="skill.name"
              class="w-8 md:w-10 h-8 md:h-10 z-5"
            />
          </template>

          <!-- Tooltip -->
          <span
            class="absolute px-2 py-1 text-sm rounded bg-blue-600 text-white opacity-0 scale-90 group-hover:opacity-100 group-hover:scale-100 transition-all duration-200 whitespace-nowrap z-50"
          >
            {{ skill.name }}
          </span>
        </div>
      </div>

      <!-- Kanan: Text skill -->
      <div
        class="md:w-1/2 text-center md:text-left flex flex-col justify-center px-4 md:px-0"
      >
        <div class="mb-4">
          <h3 class="text-xl font-semibold mb-2 text-blue-400">Frontend</h3>
          <p class="text-base md:text-lg text-white text-center md:text-left">
            HTML, CSS, JavaScript, PHP, Vue.js, React.js, TailwindCSS, Bootstrap
          </p>
        </div>
        <div>
          <h3 class="text-xl font-semibold mb-2 text-blue-400">Backend</h3>
          <p class="text-base md:text-lg text-white text-center md:text-left">
            Node.js, Express.js, MongoDB, SQL
          </p>
        </div>
      </div>
    </div>
  </div>
  </section>
</template>
