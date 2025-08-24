<template>
  <footer class="bg-blue-600 text-white py-6">
    <div class="flex justify-center space-x-6 mb-4">
      <a
        href="https://www.instagram.com/irfan.jarulloh/"
        target="_blank"
        rel="noopener noreferrer"
        class="hover:text-pink-500 text-2xl"
      >
        <font-awesome-icon :icon="['fab', 'instagram']" />
      </a>
      <a
        href="https://web.facebook.com/irfan.jarulloh/?_rdc=1&_rdr#"
        target="_blank"
        rel="noopener noreferrer"
        class="hover:text-blue-500 text-2xl"
      >
        <font-awesome-icon :icon="['fab', 'facebook']" />
      </a>
    </div>
    <div class="text-center text-sm">
      <p>
        Created by
        <a href="/" class="text-white hover:underline">Irfan Jarulloh</a>.
        | &copy; 2025.
      </p>
    </div>
  </footer>
</template>

<script setup>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { library } from "@fortawesome/fontawesome-svg-core";
import { faInstagram, faFacebook } from "@fortawesome/free-brands-svg-icons";

// daftarkan icon
library.add(faInstagram, faFacebook);
</script>
