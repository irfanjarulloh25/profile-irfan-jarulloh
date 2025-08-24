<script setup>
import { ref, computed } from "vue";

// Data sertifikat
const certificates = ref([
  {
    id: 1,
    title: "GIT",
    image: new URL("../assets/certificate/git.jpg", import.meta.url).href,
  },
  {
    id: 2,
    title: "HTML",
    image: new URL("../assets/certificate/html.jpg", import.meta.url).href,
  },
  {
    id: 3,
    title: "CSS",
    image: new URL("../assets/certificate/css.jpg", import.meta.url).href,
  },
  {
    id: 4,
    title: "BOOTSTRAP",
    image: new URL("../assets/certificate/bootstrap.jpg", import.meta.url).href,
  },
  {
    id: 5,
    title: "TAILWIND",
    image: new URL("../assets/certificate/tailwind.jpg", import.meta.url).href,
  },
  {
    id: 6,
    title: "JAVASCRIPT",
    image: new URL("../assets/certificate/js1.jpg", import.meta.url).href,
  },
  {
    id: 7,
    title: "OOP JAVASCRIPT",
    image: new URL("../assets/certificate/js2.jpg", import.meta.url).href,
  },
  {
    id: 8,
    title: "ASYNCHRONOUS JAVASCRIPT",
    image: new URL("../assets/certificate/js3.jpg", import.meta.url).href,
  },
  {
    id: 9,
    title: "DOM JAVASCRIPT",
    image: new URL("../assets/certificate/js4.jpg", import.meta.url).href,
  },
  {
    id: 10,
    title: "AJAX & WEB API",
    image: new URL("../assets/certificate/js5.jpg", import.meta.url).href,
  },
  {
    id: 11,
    title: "UI / UX DESIGN",
    image: new URL("../assets/certificate/ui.jpg", import.meta.url).href,
  },
  {
    id: 12,
    title: "VUE JS",
    image: new URL("../assets/certificate/vue.jpg", import.meta.url).href,
  },
  {
    id: 13,
    title: "REACT JS",
    image: new URL("../assets/certificate/react1.jpg", import.meta.url).href,
  },
  {
    id: 14,
    title: "KOMPONEN REACT JS",
    image: new URL("../assets/certificate/react2.jpg", import.meta.url).href,
  },
  {
    id: 15,
    title: "EVENT HANDLER REACT JS",
    image: new URL("../assets/certificate/react3.jpg", import.meta.url).href,
  },
  {
    id: 16,
    title: "REACT JS",
    image: new URL("../assets/certificate/react4.jpg", import.meta.url).href,
  },
  {
    id: 17,
    title: "STATE REACT JS",
    image: new URL("../assets/certificate/react5.jpg", import.meta.url).href,
  },
  {
    id: 18,
    title: "COMPONENT REACT JS",
    image: new URL("../assets/certificate/react7.jpg", import.meta.url).href,
  },
  {
    id: 19,
    title: "EFFECT & FETCHING REACT JS",
    image: new URL("../assets/certificate/react8.jpg", import.meta.url).href,
  },
  {
    id: 20,
    title: "PHP",
    image: new URL("../assets/certificate/php.jpg", import.meta.url).href,
  },
  {
    id: 21,
    title: "NODE JS",
    image: new URL("../assets/certificate/node.jpg", import.meta.url).href,
  },
  {
    id: 22,
    title: "MONGDB",
    image: new URL("../assets/certificate/mongo1.jpg", import.meta.url).href,
  },
  {
    id: 23,
    title: "MONGODB",
    image: new URL("../assets/certificate/mongo2.jpg", import.meta.url).href,
  },
  {
    id: 24,
    title: "RELASI DATA MONGODB",
    image: new URL("../assets/certificate/mongo3.jpg", import.meta.url).href,
  },
  {
    id: 25,
    title: "EXPRESS JS",
    image: new URL("../assets/certificate/express.jpg", import.meta.url).href,
  },
]);

const showAll = ref(false);
const modalImage = ref(null);

// Hanya tampilkan 2 baris pertama (desktop 4 kolom per baris => 8 item)
const displayedCertificates = computed(() => {
  return showAll.value ? certificates.value : certificates.value.slice(0, 8);
});

// Fungsi buka modal
const openModal = (image) => {
  modalImage.value = image;
};
</script>

<template>
  <section id="certificate" class="scroll-mt-30">
    <div class="text-center mb-10">
      <h3
        class="text-3xl md:text-4xl font-bold text-white inline-block border-b-4 border-blue-600 pb-2"
      >
        Certificate
      </h3>
    </div>
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 mb-[10rem]">
      <!-- Grid sertifikat -->
      <div
        class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 gap-6 justify-items-center"
      >
        <div
          v-for="certificate in displayedCertificates"
          :key="certificate.id"
          class="certificate-card bg-transparent border-2 border-blue-600 rounded-xl overflow-hidden transition-all duration-300 shadow-[0_0_10px_#2c75ff,0_0_22px_#2c75ff] w-full max-w-xs"
        >
          <!-- Gambar Sertifikat -->
          <div
            class="h-36 sm:h-48 overflow-hidden flex justify-center items-center"
          >
            <img
              :src="certificate.image"
              :alt="certificate.title"
              class="w-full h-full object-contain pt-0 sm:pt-2"
            />
          </div>

          <!-- Info Sertifikat -->
          <div class="p-6 text-center pt-2">
            <h3
              class="text-base sm:text-xl font-semibold text-white mb-2 px-0 sm:px-0 break-words text-center"
            >
              {{ certificate.title }}
            </h3>

            <button
              class="view-certificate text-white hover:text-blue-600 text-lg sm:text-xl font-medium"
              @click="openModal(certificate.image)"
            >
              View Details
            </button>
          </div>
        </div>
      </div>

      <!-- Tombol lihat semua -->
      <div class="flex justify-center mt-6 gap-5">
        <button
          @click="showAll = !showAll"
          class="px-6 py-2 bg-blue-600 text-white rounded-full hover:bg-white hover:text-blue-600 transition"
        >
          {{ showAll ? "Tampilkan Lebih Sedikit" : "Lihat Semua" }}
        </button>
        <a
          href="https://www.codepolitan.com/coders/irfanjarulloh89/"
          target="_blank"
          class="px-6 py-2 bg-blue-600 text-white rounded-full hover:bg-white hover:text-blue-600 transition"
        >
          View Codepolitan
        </a>
      </div>

      <!-- Modal untuk view detail -->
      <div
        v-if="modalImage"
        class="fixed inset-0 bg-black bg-opacity-70 flex justify-center items-center z-50"
        @click="modalImage = null"
      >
        <img
          :src="modalImage"
          alt="Certificate"
          class="max-h-[90%] max-w-[90%] object-contain"
        />
      </div>
    </div>
  </section>
</template>

<style scoped>
.view-certificate {
  position: relative;
  display: inline-block;
}

.view-certificate::after {
  content: "";
  position: absolute;
  left: 50%;
  bottom: 0;
  width: 0;
  height: 2px;
  background-color: currentColor;
  transition: width 0.3s ease, left 0.3s ease;
}

.view-certificate:hover::after {
  width: 100%;
  left: 0;
}
</style>
