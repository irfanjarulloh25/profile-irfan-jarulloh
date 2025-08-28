<script setup>
import { ref, onMounted } from "vue";
import aboutImg from "../assets/about.jpeg";

const isVisible = ref(false);

onMounted(() => {
  const section = document.getElementById("about");
  const observer = new IntersectionObserver(
    (entries) => {
      if (entries[0].isIntersecting) {
        isVisible.value = true; // muncul di viewport → animasi jalan
      } else {
        isVisible.value = false; // keluar viewport → reset
      }
    },
    { threshold: 0.2 }
  );
  observer.observe(section);
});
</script>

<template>
  <section id="about" class="scroll-mt-30">
    <!-- Judul -->
    <div class="text-center mb-10">
      <h3
        class="text-3xl md:text-4xl font-bold text-white inline-block border-b-4 border-blue-600 pb-2 transition-all duration-1000"
        :class="
          isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 -translate-y-10'
        "
      >
        About Me
      </h3>
    </div>

    <!-- Card utama -->
    <div
      class="relative flex flex-col md:flex-row items-center bg-transparent text-white border-2 border-blue-600 rounded-xl shadow-[0_0_10px_#2c75ff,0_0_22px_#2c75ff] w-11/12 md:w-4/5 lg:w-2/3 h-auto md:h-[27rem] mx-auto mt-[2rem] md:mt-[2rem] p-6 mb-[10rem] transition-all duration-1000 ease-out"
      :class="isVisible ? 'opacity-100 scale-100' : 'opacity-0 scale-95'"
    >
      <div class="flex flex-col md:flex-row items-center justify-center gap-8">
        <!-- Image -->
        <div
          class="flex justify-center md:justify-center md:w-1/2 mb-6 md:mb-0 transition-all duration-1000 delay-200"
          :class="
            isVisible
              ? 'opacity-100 translate-x-0'
              : 'opacity-0 -translate-x-10'
          "
        >
          <img
            :src="aboutImg"
            alt="About Me"
            class="w-64 h-64 md:w-80 md:h-80 object-cover rounded-xl shadow-[0_0_8px_#2c75ff,0_0_20px_#2c75ff] md:ml-10"
          />
        </div>

        <!-- Text -->
        <div
          class="md:w-1/2 text-center md:text-left flex flex-col justify-center transition-all duration-1000 delay-300"
          :class="
            isVisible ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-10'
          "
        >
          <p class="text-base md:text-lg text-gray-200 mb-4">
            Saya Irfan Jarulloh, seorang Fullstack Developer dan mahasiswa aktif
            yang antusias dalam membangun aplikasi web modern. Saya senang
            belajar teknologi baru, mengembangkan keterampilan, dan menciptakan
            proyek yang bermanfaat.
          </p>
          <p class="text-base md:text-lg text-gray-200 mb-4">
            Saya juga aktif mengikuti komunitas teknologi. Bootcamp, workshop,
            dan proyek kolaboratif selalu saya manfaatkan untuk meningkatkan
            pengalaman dan kualitas proyek melalui praktik terbaik.
          </p>
          <p class="text-base md:text-lg text-gray-200">
            Saya percaya kombinasi antara pembelajaran akademik dan pengalaman
            praktis akan membantu saya menjadi pengembang yang kompeten.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>
