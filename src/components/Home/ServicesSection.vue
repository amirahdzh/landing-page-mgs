<script setup lang="ts">
import { useFetch } from "@vueuse/core";
import { computed } from "vue";
import ServiceCard from "./ServiceCard.vue";

// Fetch data dari API
const { data, error, isFetching } = useFetch(
  "https://strapi-admin.megagigasolusindo.co.id/api/services?locale=id"
).json();

// Default icon jika API tidak menyediakannya
const defaultIcon = "/src/assets/default-service.svg";

// Format data untuk ditampilkan
const services = computed(() => {
  return (
    data.value?.data.map((item: any) => ({
      icon: item.icon || defaultIcon, // Pakai default jika `icon` null
      title: item.title,
      description: item.description,
    })) || []
  );
});
</script>

<template>
  <section class="py-20 relative bg-white overflow-hidden">
    <!-- SVG Background -->
    <div class="absolute top-0 left-0 pointer-events-none">
      <img
        src="/src/components/Vector/service-vector.svg"
        alt="Background Vector"
        class="w-auto h-auto max-w-[250px] opacity-50"
      />
    </div>

    <div class="container mx-auto px-6 text-center relative max-w-screen-lg">
      <h2 class="text-red-600 font-semibold text-lg">What we Have</h2>
      <h1 class="text-3xl font-bold text-gray-900 mt-2">Our Services</h1>

      <!-- Loading State -->
      <p v-if="isFetching" class="text-gray-500 mt-6">Loading...</p>

      <!-- Error State -->
      <p v-else-if="error" class="text-red-500 mt-6">
        Failed to load services. Please try again.
      </p>

      <!-- Card List -->
      <div v-else class="mt-10 grid grid-cols-1 md:grid-cols-2 gap-6">
        <ServiceCard
          v-for="(service, index) in services"
          :key="index"
          :icon="service.icon"
          :title="service.title"
          :description="service.description"
        />
      </div>
    </div>
  </section>
</template>
