<template>
  <canvas ref="canvas" class="fixed top-0 left-0 w-full h-full -z-10"></canvas>
</template>

<script setup>
import { onMounted, ref } from "vue";

const canvas = ref(null);

onMounted(() => {
  const ctx = canvas.value.getContext("2d");

  function resizeCanvas() {
    canvas.value.width = window.innerWidth;
    canvas.value.height = window.innerHeight;
  }

  resizeCanvas();
  window.addEventListener("resize", resizeCanvas);

  const stars = Array.from({ length: 150 }).map(() => ({
    x: Math.random() * canvas.value.width,
    y: Math.random() * canvas.value.height,
    radius: Math.random() * 1.5,
    speed: Math.random() * 0.5 + 0.2,
    alpha: Math.random(),        // opacity awal
    delta: Math.random() * 0.02 + 0.005 // perubahan opacity per frame
  }));

  function drawStars() {
    ctx.clearRect(0, 0, canvas.value.width, canvas.value.height);
    stars.forEach((star) => {
      ctx.beginPath();
      ctx.arc(star.x, star.y, star.radius, 0, Math.PI * 2);
      ctx.fillStyle = `rgba(255,255,255,${star.alpha})`; // gunakan alpha
      ctx.fill();
    });
  }

  function updateStars() {
    stars.forEach((star) => {
      // bergerak ke bawah
      star.y += star.speed;
      if (star.y > canvas.value.height) {
        star.y = 0;
        star.x = Math.random() * canvas.value.width;
      }

      // ubah alpha untuk efek berkedip
      star.alpha += star.delta;
      if (star.alpha <= 0 || star.alpha >= 1) {
        star.delta = -star.delta; // balik arah perubahan
        star.alpha = Math.max(0, Math.min(star.alpha, 1));
      }
    });
  }

  function animate() {
    drawStars();
    updateStars();
    requestAnimationFrame(animate);
  }

  animate();
});
</script>
