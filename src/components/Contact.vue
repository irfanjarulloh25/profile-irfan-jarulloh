<template>
  <section id="contact" class="mb-15 scroll-mt-23">
    <div class="text-center mb-5">
      <h3
        class="text-3xl md:text-4xl font-bold text-white inline-block border-b-4 border-blue-600 pb-2"
      >
        Contact
      </h3>
    </div>
    <form
      ref="contactForm"
      class="max-w-lg mx-auto bg-transparent p-6 rounded-2xl space-y-5 border-2 border-blue-600 shadow-[0_0_10px_#2c75ff,0_0_22px_#2c75ff] animate-fade"
      @submit.prevent="handleSubmit"
    >
      <!-- Name -->
      <div>
        <label for="name" class="block text-sm font-medium text-white"
          >Name</label
        >
        <input
          type="text"
          id="name"
          v-model="form.name"
          placeholder="Your name"
          required
          class="mt-2 block w-full rounded-lg border-2 border-blue-600 p-3"
        />
      </div>

      <!-- Phone -->
      <div>
        <label for="phone" class="block text-sm font-medium text-white"
          >Phone</label
        >
        <input
          type="tel"
          id="phone"
          v-model="form.phone"
          placeholder="Your phone number"
          required
          class="mt-2 block w-full rounded-lg border-2 border-blue-600 p-3"
        />
      </div>

      <!-- Email -->
      <div>
        <label for="email" class="block text-sm font-medium text-white"
          >Email</label
        >
        <input
          type="email"
          id="email"
          v-model="form.email"
          placeholder="Your email"
          required
          class="mt-2 block w-full rounded-lg border-2 border-blue-600 p-3"
        />
      </div>

      <!-- Message -->
      <div>
        <label for="message" class="block text-sm font-medium text-white"
          >Message</label
        >
        <textarea
          id="message"
          v-model="form.message"
          placeholder="Your message"
          required
          rows="2"
          class="mt-2 block w-full rounded-lg border-2 border-blue-600 p-3 h-20"
        ></textarea>
      </div>

      <!-- Button -->
      <button
        type="submit"
        class="w-full bg-blue-600 text-white font-semibold py-3 px-6 rounded-lg shadow hover:bg-white hover:text-blue-600 transition"
      >
        Send via WhatsApp
      </button>
    </form>
  </section>
</template>

<script>
export default {
  name: "ContactForm",
  data() {
    return {
      form: {
        name: "",
        phone: "",
        email: "",
        message: "",
      },
      recipientPhone: "6281299981774", // nomor WA tujuan
    };
  },
  methods: {
    handleSubmit() {
      const text = encodeURIComponent(
        `Halo, saya ${this.form.name}\n` +
          `Phone: ${this.form.phone}\n` +
          `Email: ${this.form.email}\n` +
          `Pesan: ${this.form.message}`
      );

      const waLink = `https://wa.me/${this.recipientPhone}?text=${text}`;
      window.open(waLink, "_blank");

      // reset form
      this.form = { name: "", phone: "", email: "", message: "" };
    },
  },
  mounted() {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add("show");
          } else {
            entry.target.classList.remove("show"); // biar bisa animasi lagi kalau scroll balik
          }
        });
      },
      { threshold: 0.2 }
    );

    observer.observe(this.$refs.contactForm);
  },
};
</script>

<style scoped>
/* Animasi fade + slide */
.animate-fade {
  opacity: 0;
  transform: translateY(40px);
  transition: all 0.8s ease;
}

.animate-fade.show {
  opacity: 1;
  transform: translateY(0);
}
</style>
