<template>
  <section id="contact" class="mb-15 scroll-mt-30">
    <div class="text-center mb-10">
      <h3
        class="text-3xl md:text-4xl font-bold text-white inline-block border-b-4 border-blue-600 pb-2"
      >
        Contact
      </h3>
    </div>
    <form
      class="max-w-lg mx-auto bg-transparent p-6 rounded-2xl space-y-5 border-2 border-blue-600 shadow-[0_0_10px_#2c75ff,0_0_22px_#2c75ff]"
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
          rows="4"
          class="mt-2 block w-full rounded-lg border-2 border-blue-600 p-3"
        ></textarea>
      </div>

      <!-- Button -->
      <button
        type="submit"
        class="w-full bg-blue-600 text-white font-semibold py-3 px-6 rounded-lg shadow hover:bg-white hover:text-blue-600 transition"
      >
        Open Email App
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
        email: "",
        message: "",
      },
      recipientEmail: "irfanjarulloh89@gmail.com", // email tujuan (misalnya milikmu)
    };
  },
  methods: {
    handleSubmit() {
      // bikin isi email
      const subject = encodeURIComponent(`Message from ${this.form.name}`);
      const body = encodeURIComponent(
        `Name: ${this.form.name}\nEmail: ${this.form.email}\nMessage: ${this.form.message}`
      );

      // mailto link
      const mailtoLink = `mailto:${this.recipientEmail}?subject=${subject}&body=${body}`;

      // pindah ke aplikasi email si pengirim
      window.location.href = mailtoLink;

      // reset form
      this.form = { name: "", email: "", message: "" };
    },
  },
};
</script>
