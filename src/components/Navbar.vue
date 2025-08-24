<template>
  <nav
    class="fixed top-0 left-0 w-full z-50 backdrop-blur-md shadow-md border-b border-blue-600"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between h-20">
        <!-- Logo -->
        <div class="flex items-center space-x-2">
          <div
            class="bg-blue-600 text-white font-bold px-3 py-2 rounded-lg shadow-lg"
          >
            IJ
          </div>
          <span class="text-2xl font-bold tracking-wide text-white">
            Irfan Jarulloh
          </span>
        </div>

        <!-- Desktop Menu -->
        <div class="hidden md:flex items-center space-x-10 text-2xl">
          <a
            href="#"
            class="relative text-gray-200 hover:text-blue-400 after:content-[''] after:absolute after:left-1/2 after:bottom-0 after:h-[2px] after:w-0 after:bg-blue-500 after:transition-all after:duration-300 hover:after:w-full hover:after:left-0"
            >Home</a
          >
          <a
            href="#about"
            class="relative text-gray-200 hover:text-blue-400 after:content-[''] after:absolute after:left-1/2 after:bottom-0 after:h-[2px] after:w-0 after:bg-blue-500 after:transition-all after:duration-300 hover:after:w-full hover:after:left-0"
            >About</a
          >
          <a
            href="#skills"
            class="relative text-gray-200 hover:text-blue-400 after:content-[''] after:absolute after:left-1/2 after:bottom-0 after:h-[2px] after:w-0 after:bg-blue-500 after:transition-all after:duration-300 hover:after:w-full hover:after:left-0"
            >Skills</a
          >
           <a
            href="#certificate"
            class="relative text-gray-200 hover:text-blue-400 after:content-[''] after:absolute after:left-1/2 after:bottom-0 after:h-[2px] after:w-0 after:bg-blue-500 after:transition-all after:duration-300 hover:after:w-full hover:after:left-0"
            >Certificate</a
          >
          <a
            href="#projects"
            class="relative text-gray-200 hover:text-blue-400 after:content-[''] after:absolute after:left-1/2 after:bottom-0 after:h-[2px] after:w-0 after:bg-blue-500 after:transition-all after:duration-300 hover:after:w-full hover:after:left-0"
            >Project</a
          >
          <a
            href="#contact"
            class="relative text-gray-200 hover:text-blue-400 after:content-[''] after:absolute after:left-1/2 after:bottom-0 after:h-[2px] after:w-0 after:bg-blue-500 after:transition-all after:duration-300 hover:after:w-full hover:after:left-0"
            >Contact</a
          >
        </div>

        <!-- Mobile Menu Button -->
        <div class="flex md:hidden items-center">
          <button
            @click="isOpen = !isOpen"
            class="focus:outline-none text-white"
          >
            <svg
              class="w-6 h-6"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                v-if="!isOpen"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16"
              />
              <path
                v-else
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M6 18L18 6M6 6l12 12"
              />
            </svg>
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Menu Dropdown -->
    <div
      v-if="isOpen"
      class="md:hidden bg-black/70 backdrop-blur-md px-4 pb-3 space-y-2 shadow-md"
    >
      <a
        href="#header"
        class="block text-gray-200 relative after:content-[''] after:absolute after:left-1/2 after:bottom-0 after:w-0 after:h-[2px] after:bg-blue-400 after:transition-all after:duration-300 hover:after:left-0 hover:after:w-full"
      >
        Home
      </a>
      <a
        href="#about"
        class="block text-gray-200 relative after:content-[''] after:absolute after:left-1/2 after:bottom-0 after:w-0 after:h-[2px] after:bg-blue-400 after:transition-all after:duration-300 hover:after:left-0 hover:after:w-full"
      >
        About
      </a>
      <a
        href="#skills"
        class="block text-gray-200 relative after:content-[''] after:absolute after:left-1/2 after:bottom-0 after:w-0 after:h-[2px] after:bg-blue-400 after:transition-all after:duration-300 hover:after:left-0 hover:after:w-full"
      >
        Skill
      </a>
      <a
        href="#certificate"
        class="block text-gray-200 relative after:content-[''] after:absolute after:left-1/2 after:bottom-0 after:w-0 after:h-[2px] after:bg-blue-400 after:transition-all after:duration-300 hover:after:left-0 hover:after:w-full"
      >
        Certificate
      </a>
      <a
        href="#projects"
        class="block text-gray-200 relative after:content-[''] after:absolute after:left-1/2 after:bottom-0 after:w-0 after:h-[2px] after:bg-blue-400 after:transition-all after:duration-300 hover:after:left-0 hover:after:w-full"
      >
        Project
      </a>
      <a
        href="#contact"
        class="block text-gray-200 relative after:content-[''] after:absolute after:left-1/2 after:bottom-0 after:w-0 after:h-[2px] after:bg-blue-400 after:transition-all after:duration-300 hover:after:left-0 hover:after:w-full"
      >
        Contact
      </a>
    </div>
  </nav>
</template>

<script setup>
import { ref } from "vue";

const isOpen = ref(false);
</script>
