<script setup>
import { ref, computed } from "vue";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { library } from "@fortawesome/fontawesome-svg-core";
import { faGithub } from "@fortawesome/free-brands-svg-icons";

library.add(faGithub);

import weave from "../assets/projects/weave.png";
import kasir from "../assets/projects/kasir.png";
import coffe from "../assets/projects/coffe.png";
import resistor from "../assets/projects/resistor.png";
import onlineshope from "../assets/projects/onlineshope.png";
import Undangan from "../assets/projects/undangan.png";

const projects = ref([
  {
    id: 1,
    category: "web",
    title: "E-commerce Weave",
    description:
      "Online Shop sederhana menggunakan MERN Stack (MongoDB, Express.js, React.js, Node.js) Tampilan responsif dan user-friendly",
    image: weave,
    demo: "https://weaveshop.netlify.app/",
    technologies: ["MongoDb", "Express Js", "React Js", "Node Js", "Bootstrap"],
    features: [
      "Dashboard",
      "Autentikasi user",
      "admin",
      "Manajemen produk (tambah/edit/hapus)",
      "Checkout",
      "Contact",
      "Upload bukti pembayaran",
      "Pelacakan status pesanan (Dikemas, Dikirim, Diterima)",
      "Note : Untuk demo , backend nya belum di fetch karena belum ada server public",
    ],
  },
  {
    id: 2,
    category: "web",
    title: "front End Kasir & Input Barang",
    description:
      "Front end sederhana untuk kasir dan input barang menggunakan React js dan Bootstrap Tampilan responsif dan user-friendly",
    image: kasir,
    github: "https://github.com/irfanjarulloh25/KasirDanStockBarang",
    technologies: ["React Js", "Bootstrap"],
    features: [
      "Dashboard",
      "Transaksi (kasir)",
      "Riwayat Transaksi",
      "Input Jasa Service",
      "Input Sparepart",
      "Laporan Transaksi",
    ],
  },
  {
    id: 3,
    category: "web",
    title: "Coffe Shoppe",
    description:
      "Front end sederhana untuk Coffe Shope menggunakan Html, Css, Bootstrap & Javascript Tampilan responsif dan user-friendly",
    image: coffe,
    github: "https://github.com/irfanjarulloh25/Coffe-Ruang-Rasa",
    technologies: ["Html", "Bootstrap", "Javascript"],
    features: [
      "Home",
      "Store",
      "Contact",
      "About",
      "User",
      "ShoppingCart",
      "Checkout",
    ],
  },
  {
    id: 4,
    category: "web",
    title: "Alat Hitung Resistor",
    description:
      "Alat hitung resistor sederhana menggunakan html css dan javascript",
    image: resistor,
    github: "https://github.com/irfanjarulloh25/Alat-hitung-resistor",
    technologies: ["Html", "Css", "Javascript"],
    features: ["Alat Hitung Resistor"],
  },
  {
    id: 5,
    category: "web",
    title: "E-commerce",
    description:
      "Online Shop sederhana menggunakan Html, Css, Bootstrap, Javascript, Php dan Sql Tampilan responsif dan user-friendly",
    image: onlineshope,
    github: "https://github.com/irfanjarulloh25/Online-shop",
    technologies: ["Html", "Css", "Bootstrap", "Javascript", "Php", "Sql"],
    features: [
      "Autentikasi user",
      "admin",
      "Manajemen produk (tambah/edit/hapus)",
      "Checkout",
      "Contact",
      "Upload bukti pembayaran",
      "Pelacakan status pesanan (Dikemas, Dikirim, Diterima)",
    ],
  },
  {
    id: 6,
    category: "web",
    title: "Undangan Digital",
    description:
      "Undangan Digital sederhana menggunakan Html, Css, Bootstrap & Javascript Tampilan responsif dan user-friendly",
    image: Undangan,
    github: "https://github.com/irfanjarulloh25/undangan-digital",
    technologies: ["Html", "Bootstrap", "Javascript"],
    features: [
      "Cover / Opening Page",
      "Countdown Timer",
      "Profil / Informasi Acara",
      "Peta Lokasi (Google Maps Embed)",
      "Galeri Foto / Video",
    ],
  },
]);

const showAll = ref(false);
const displayedProjects = computed(() =>
  showAll.value ? projects.value : projects.value.slice(0, 4)
);

const showModal = ref(false);
const selectedProject = ref(null);

const openProjectModal = (project) => {
  selectedProject.value = project;
  showModal.value = true;
};

const closeProjectModal = () => {
  showModal.value = false;
  selectedProject.value = null;
};
</script>

<template>
  <section id="projects" class="scroll-mt-25">
    <!-- Section Title -->
    <div class="text-center mb-10">
      <h3
        class="text-xl sm:text-2xl md:text-4xl font-bold text-white inline-block border-b-4 border-blue-600 pb-2"
      >
        My Projects
      </h3>
    </div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 mb-[10rem]">
      <!-- Project Grid -->
      <div
        class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 gap-6 justify-items-center"
      >
        <div
          v-for="project in displayedProjects"
          :key="project.id"
          class="project-card bg-transparent border-2 border-blue-600 rounded-xl overflow-hidden transition-all duration-300 shadow-[0_0_10px_#2c75ff,0_0_22px_#2c75ff] w-full max-w-xs"
        >
          <div
            class="h-28 sm:h-40 md:h-48 overflow-hidden flex justify-center items-center"
          >
            <img
              :src="project.image"
              :alt="project.title"
              class="w-full h-full object-contain pt-0 sm:pt-2"
            />
          </div>

          <div class="p-4 sm:p-6 text-center pt-2">
            <span
              class="inline-block px-2 py-1 text-[10px] sm:text-xs md:text-sm font-semibold bg-blue-100 text-blue-800 rounded-full mb-2"
            >
              {{ project.category }}
            </span>
            <h3
              class="text-sm sm:text-base md:text-lg font-semibold text-white mb-2 break-words text-center"
            >
              {{ project.title }}
            </h3>

            <div class="flex justify-center items-center gap-4">
              <button
                class="view-project text-white hover:text-blue-600 text-sm sm:text-base md:text-lg font-medium"
                @click="openProjectModal(project)"
              >
                View Details
              </button>
            </div>
          </div>
        </div>
      </div>

      <!-- Tampilkan Semua -->
      <div class="flex justify-center mt-6">
        <button
          @click="showAll = !showAll"
          class="px-4 sm:px-6 py-1 sm:py-2 bg-blue-600 text-white rounded-full text-sm sm:text-base hover:bg-white hover:text-blue-600 transition"
        >
          {{ showAll ? "Tampilkan Lebih Sedikit" : "Lihat Semua" }}
        </button>
      </div>
    </div>

    <!-- Project Modal -->
    <div
      v-if="showModal"
      class="fixed inset-0 backdrop-blur-md bg-opacity-50 flex items-center justify-center p-4 z-50"
    >
      <div
        class="bg-white rounded-xl max-w-5xl w-full max-h-screen overflow-y-auto relative flex flex-col md:flex-row"
      >
        <!-- Tombol Close -->
        <button
          @click="closeProjectModal"
          class="absolute top-2 right-2 md:top-4 md:right-4 text-gray-500 hover:text-gray-700 z-50 p-1"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5 sm:h-6 sm:w-6"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </button>

        <!-- Gambar kiri -->
        <div class="md:w-1/2 w-full p-4 flex justify-center items-center">
          <img
            :src="selectedProject.image"
            :alt="selectedProject.title"
            class="w-3/4 sm:w-full h-auto rounded-lg"
          />
        </div>

        <!-- Konten kanan -->
        <div class="md:w-1/2 p-4 sm:p-6 flex flex-col justify-between">
          <div>
            <h3
              class="text-lg sm:text-xl md:text-2xl font-bold text-gray-800 mb-2"
            >
              {{ selectedProject.title }}
            </h3>
            <span
              class="inline-block px-2 py-1 text-[10px] sm:text-xs md:text-sm rounded-full bg-blue-100 text-blue-800 mb-4"
              >{{ selectedProject.category }}</span
            >

            <h5 class="font-medium text-gray-700 text-sm sm:text-base">
              Overview
            </h5>
            <p class="text-gray-600 mb-4 text-sm sm:text-base">
              {{ selectedProject.description }}
            </p>

            <h5 class="font-medium text-gray-700 text-sm sm:text-base">
              Technologies Used
            </h5>
            <div class="flex flex-wrap gap-2 mt-2 mb-4">
              <span
                v-for="tech in selectedProject.technologies"
                :key="tech"
                class="px-2 py-1 bg-blue-600 rounded text-xs sm:text-sm md:text-base"
                >{{ tech }}</span
              >
            </div>

            <h5 class="font-medium text-gray-700 text-sm sm:text-base">
              Key Features
            </h5>
            <ul
              class="list-disc list-inside text-gray-600 space-y-1 mb-4 text-sm sm:text-base"
            >
              <li v-for="feature in selectedProject.features" :key="feature">
                {{ feature }}
              </li>
            </ul>
          </div>

          <!-- Tombol Demo & Code -->
          <div class="pt-2 flex space-x-4">
            <a
              v-if="selectedProject.demo"
              :href="selectedProject.demo"
              target="_blank"
              class="flex items-center text-blue-600 hover:text-blue-800 text-sm sm:text-base"
            >
              View Demo
            </a>
            <a
              v-if="selectedProject.github"
              :href="selectedProject.github"
              target="_blank"
              class="flex items-center text-blue-600 hover:text-blue-800 text-sm sm:text-base"
            >
              View Code
              <FontAwesomeIcon
                :icon="['fab', 'github']"
                class="text-xl sm:text-2xl ml-1"
              />
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.view-project {
  position: relative;
  display: inline-block;
}

.view-project::after {
  content: "";
  position: absolute;
  left: 50%;
  bottom: 0;
  width: 0;
  height: 2px;
  background-color: currentColor;
  transition: width 0.3s ease, left 0.3s ease;
}

.view-project:hover::after {
  width: 100%;
  left: 0;
}
</style>
