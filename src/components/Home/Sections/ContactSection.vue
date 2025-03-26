<script setup lang="ts">
import { ref } from "vue";
import { reactive } from "vue";

const formData = reactive({
  name: "",
  email: "",
  phone: "",
  message: "",
});
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
            name: formData.name,
            email: formData.email,
            phone: formData.phone,
            message: formData.message,
          },
        }),
      }
    );

    if (!response.ok) {
      throw new Error("Failed to send message. Please try again.");
    }

    successMessage.value = "Your message has been sent successfully!";
    Object.assign(formData, { name: "", email: "", phone: "", message: "" });
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
          <h3 class="text-accent font-bold">Contact Us</h3>
          <p class="mt-4 text-4xl font-bold">
            Haven't gotten what you want yet?
          </p>

          <!-- Call -->
          <div class="container flex items-center gap-4 mt-4">
            <i
              class="pi pi-phone bg-white p-4 rounded-lg text-3xl text-[#061951]"
            ></i>
            <div class="text-left">
              <p class="font-semibold">Call</p>
              <p>0274 4299 535</p>
              <p>+62 877 203 203 94</p>
            </div>
          </div>

          <!-- Email -->
          <div class="container flex items-center gap-4 mt-4">
            <i
              class="pi pi-envelope bg-white p-4 rounded-lg text-3xl text-[#061951]"
            ></i>
            <div class="text-left">
              <p class="font-semibold">Email</p>
              <p>info@megagiga.co.id</p>
            </div>
          </div>

          <!-- Address -->
          <div class="container flex items-center gap-4 mt-4">
            <i
              class="pi pi-map-marker bg-white p-4 rounded-lg text-3xl text-[#061951]"
            ></i>
            <div class="text-left">
              <p class="font-semibold">Address</p>
              <p>
                Pondok Permai Wirosaban B10, Jl. Ki Ageng Pemanahan, Bantul,
                Yogyakarta 55191
              </p>
            </div>
          </div>
        </div>

        <!-- Form -->
        <div class="lg:w-1/2 bg-white p-6 rounded-lg shadow-md w-full">
          <input
            v-model="formData.name"
            type="text"
            placeholder="Name"
            class="w-full p-3 border rounded-lg mb-4"
            required
          />
          <input
            v-model="formData.email"
            type="email"
            placeholder="Email"
            class="w-full p-3 border rounded-lg mb-4"
            required
          />
          <input
            v-model="formData.phone"
            type="tel"
            placeholder="Phone"
            class="w-full p-3 border rounded-lg mb-4"
            required
          />
          <textarea
            v-model="formData.message"
            placeholder="Your Message"
            class="w-full p-3 border rounded-lg mb-4"
            required
          ></textarea>

          <!-- Notifikasi -->
          <p v-if="successMessage" class="text-green-600 mb-4">
            {{ successMessage }}
          </p>
          <p v-if="errorMessage" class="text-accent mb-4">
            {{ errorMessage }}
          </p>

          <!-- Tombol -->
          <button
            @click="handleSubmit"
            :disabled="loading"
            class="bg-accent text-white px-6 py-3 rounded-md hover:bg-accent/80 disabled:bg-gray-400 w-full cursor-pointer"
          >
            {{ loading ? "Sending..." : "Send" }}
          </button>
        </div>
      </div>
    </div>
  </section>
</template>
