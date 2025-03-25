<script setup lang="ts">
import { ref } from "vue";

// State untuk form
const name = ref("");
const email = ref("");
const phone = ref("");
const message = ref("");
const loading = ref(false);
const successMessage = ref("");
const errorMessage = ref("");

// Fungsi untuk mengirim data ke API
const handleSubmit = async () => {
  loading.value = true;
  successMessage.value = "";
  errorMessage.value = "";

  try {
    const response = await fetch(
      "https://strapi-admin.megagigasolusindo.co.id/api/contact-uses",
      {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          data: {
            name: name.value,
            email: email.value,
            phone: phone.value,
            message: message.value,
          },
        }),
      }
    );

    if (!response.ok) {
      throw new Error("Failed to send message. Please try again.");
    }

    successMessage.value = "Your message has been sent successfully!";
    // Reset form setelah sukses
    name.value = "";
    email.value = "";
    phone.value = "";
    message.value = "";
  } catch (error: any) {
    errorMessage.value = error.message || "Something went wrong!";
  } finally {
    loading.value = false;
  }
};
</script>

<template>
  <section class="py-20 relative bg-accent/10 overflow-hidden">
    <div class="container mx-auto px-6 max-w-screen-lg">
      <div class="flex flex-col lg:flex-row items-center lg:items-start gap-12">
        <!-- Bagian Informasi -->
        <div class="lg:w-1/2 text-center lg:text-left">
          <h3 class="text-3xl font-bold">Contact Us</h3>
          <p class="mt-4">Haven't gotten what you want yet?</p>
          <p class="mt-2">📞 024 4209 533</p>
          <p class="mt-2">📧 info@mgsaja.co.id</p>
          <p class="mt-2">📍 Pendopo Permai Wonosobo</p>
        </div>

        <!-- Form -->
        <div class="lg:w-1/2 bg-white p-6 rounded-lg shadow-md w-full">
          <input
            v-model="name"
            type="text"
            placeholder="Name"
            class="w-full p-3 border rounded-lg mb-4"
            required
          />
          <input
            v-model="email"
            type="email"
            placeholder="Email"
            class="w-full p-3 border rounded-lg mb-4"
            required
          />
          <input
            v-model="phone"
            type="tel"
            placeholder="Phone"
            class="w-full p-3 border rounded-lg mb-4"
            required
          />
          <textarea
            v-model="message"
            placeholder="Your Message"
            class="w-full p-3 border rounded-lg mb-4"
            required
          ></textarea>

          <!-- Notifikasi -->
          <p v-if="successMessage" class="text-green-600 mb-4">
            {{ successMessage }}
          </p>
          <p v-if="errorMessage" class="text-red-600 mb-4">
            {{ errorMessage }}
          </p>

          <!-- Tombol -->
          <button
            @click="handleSubmit"
            :disabled="loading"
            class="bg-red-600 text-white px-6 py-3 rounded-md hover:bg-red-700 disabled:bg-gray-400 w-full"
          >
            {{ loading ? "Sending..." : "Send" }}
          </button>
        </div>
      </div>
    </div>
  </section>
</template>
