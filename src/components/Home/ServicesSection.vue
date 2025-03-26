<script setup lang="ts">
import { useFetch } from "@vueuse/core";
import { computed } from "vue";
import ServiceCard from "./ServiceCard.vue";

// Fetch data dari API
const { data, error, isFetching } = useFetch(
  "https://strapi-admin.megagigasolusindo.co.id/api/services?locale=id"
).json();

// Format data untuk ditampilkan
const services = computed(() => {
  return (
    data.value?.data.map((item: any) => ({
      icon: item?.icon || "pi pi-cog", // GUNAKAN GAMBAR DEFAULT
      title: item?.title || "No Title",
      description: item?.description || "No Description Available",
    })) || []
  );
});
</script>

<template>
  <section class="py-20 relative bg-white overflow-hidden">
    <!-- SVG Background -->
    <div class="absolute top-10 -left-4 pointer-events-none">
      <img
        src="/src/components/Vector/service-vector.svg"
        alt="Background Vector"
        class="w-[72px] h-auto max-w-[200px] opacity-50 scale-x-[-1] scale-y-[-1] transform rotate-[8deg]"
      />
    </div>

    <div class="container mx-auto px-6 text-center relative max-w-screen-lg">
      <h2 class="text-red-600 font-semibold text-lg">What we Have</h2>
      <h1 class="text-4xl font-medium text-gray-900 mt-2">Our Services</h1>

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
