<script setup>
import aboutImg from "../assets/about.jpeg";
</script>

<template>
  <section id="about" class="scroll-mt-30">
    <!-- Judul About Me dengan underline -->
    <div class="text-center mb-10">
      <h3
        class="text-3xl md:text-4xl font-bold text-white inline-block border-b-4 border-blue-600 pb-2"
      >
        About Me
      </h3>
    </div>

    <div
      class="relative flex flex-col md:flex-row items-center bg-transparent text-white border-2 border-blue-600 rounded-xl shadow-[0_0_10px_#2c75ff,0_0_22px_#2c75ff] w-11/12 md:w-4/5 lg:w-2/3 h-auto md:h-[27rem] mx-auto mt-[2rem] md:mt-[2rem] p-6 mb-[10rem]"
    >
      <div class="flex flex-col md:flex-row items-center justify-center gap-8">
        <!-- Image di kiri, geser ke kanan desktop -->
        <div
          class="flex justify-center md:justify-center md:w-1/2 mb-6 md:mb-0"
        >
          <img
            :src="aboutImg"
            alt="About Me"
            class="w-64 h-64 md:w-80 md:h-80 object-cover rounded-xl border-2 shadow-[0_0_8px_#2c75ff,0_0_20px_#2c75ff] border-none md:ml-10"
          />
        </div>

        <!-- Text di kanan -->
        <div
          class="md:w-1/2 text-center md:text-left flex flex-col justify-center"
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
